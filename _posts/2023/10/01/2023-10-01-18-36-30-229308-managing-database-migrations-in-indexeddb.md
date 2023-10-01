---
layout: post
title: "Managing database migrations in IndexedDB"
description: " "
date: 2023-10-01
tags: [database, migrations]
comments: true
share: true
---

IndexedDB is a powerful client-side database that allows web applications to store and retrieve structured data. As your application evolves over time, you might need to make changes to your database schema to support new features or improve performance. Managing database migrations effectively is crucial to ensuring a smooth transition without any data loss. In this blog post, we will explore some best practices for managing database migrations in IndexedDB.

## 1. Versioning your database

IndexedDB relies on a versioning system to handle database schema changes. Each time you make a change to your database structure, you should increment the version number. 

```javascript
const DATABASE_NAME = 'myDB';
const DATABASE_VERSION = 2;

let request = indexedDB.open(DATABASE_NAME, DATABASE_VERSION);

request.onsuccess = function(event) {
  // Database opened successfully
};

request.onupgradeneeded = function(event) {
  const db = event.target.result;
  const oldVersion = event.oldVersion;
  
  // Perform database migration here based on the oldVersion
};
```

By providing a new version number when opening the database, you can control the execution of database migration logic when necessary.

## 2. Handling database upgrades

The `onupgradeneeded` event is triggered when the database version changes. Inside this event handler, you can perform any necessary database upgrades.

```javascript
request.onupgradeneeded = function(event) {
  const db = event.target.result;
  const oldVersion = event.oldVersion;
  
  if (oldVersion < 2) {
    // Upgrade logic for version 1 to version 2
    const booksStore = event.target.transaction.objectStore('books');
    booksStore.createIndex('author', 'author', { unique: false });
  }
  
  if (oldVersion < 3) {
    // Upgrade logic for version 2 to version 3
    const booksStore = event.target.transaction.objectStore('books');
    booksStore.createIndex('category', 'category', { unique: false });
  }
  
  // Add more upgrade logic as needed for other versions
};
```

Inside the `onupgradeneeded` event handler, you can check the `oldVersion` and perform the necessary database upgrades based on the previous version. In the example above, we added a new index to the "books" object store in two different version upgrades.

## 3. Handling data migrations

In addition to schema changes, you might need to migrate existing data when performing database upgrades. To achieve this, you can use the `onupgradeneeded` event handler to read data from the old schema and write it to the new schema.

```javascript
request.onupgradeneeded = function(event) {
  const db = event.target.result;
  const oldVersion = event.oldVersion;
  
  if (oldVersion < 2) {
    const transaction = event.target.transaction;
    const booksStore = transaction.objectStore('books');
  
    const request = booksStore.openCursor();
  
    request.onsuccess = function(event) {
      const cursor = event.target.result;
  
      if (cursor) {
        const book = cursor.value;
        // Migrate data here based on old schema
        
        cursor.update(book); // Write the migrated data back to the store
        cursor.continue();
      }
    };
  }
  
  // Handle data migration for other version upgrades
};
```

In the example above, we iterate over the existing data using an open cursor and apply the necessary transformations or adjustments to the data based on the previous schema. After the migration, we update the data using `cursor.update()` to persist the migrated data in the new schema.

## Conclusion

Managing database migrations in IndexedDB is an essential aspect of maintaining your web application's data integrity. By versioning your database, handling upgrades, and migrating data when needed, you can seamlessly evolve your application's database schema over time. Incorporating these best practices into your development process will ensure a smooth and error-free migration experience.

#database #migrations