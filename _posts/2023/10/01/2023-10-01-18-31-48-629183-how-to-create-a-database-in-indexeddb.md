---
layout: post
title: "How to create a database in IndexedDB"
description: " "
date: 2023-10-01
tags: [WebDevelopment, IndexedDB]
comments: true
share: true
---

IndexedDB is a powerful browser-based database that allows you to store and retrieve data on the client-side. In this blog post, we will explore how to create a database in IndexedDB using JavaScript.

## Prerequisites

Before we start, make sure you have a basic understanding of JavaScript and how to work with the browser's developer console.

## Step 1: Opening a Database Connection

To create a database in IndexedDB, we first need to open a connection to it. This can be done using the `indexedDB.open()` method. The `open()` method takes two parameters: the name of the database and its version.

```javascript
const dbName = "myDatabase";
const dbVersion = 1;

const request = indexedDB.open(dbName, dbVersion);

request.onerror = (event) => {
  console.error("Error opening database", event.target.error);
};

request.onsuccess = (event) => {
  const db = event.target.result;
  console.log("Database connection successful", db);
};
```

In the code above, we define the database name as `"myDatabase"` and the version as `1`. We then open a connection to the database using `indexedDB.open()`. The `request` object returned by `open()` can be used to handle errors and success events.

## Step 2: Creating Object Stores

Once the connection to the database is established, we can create object stores. Object stores are containers that hold the data in IndexedDB.

```javascript
request.onupgradeneeded = (event) => {
  const db = event.target.result;
  
  if (!db.objectStoreNames.contains("myObjectStore")) {
    const objectStore = db.createObjectStore("myObjectStore", { keyPath: "id", autoIncrement: true });
  }
};
```

In the code above, we listen for the `upgradeneeded` event, which is fired when the database version changes or a new database is created. Inside the event handler, we check if the object store `"myObjectStore"` already exists. If it doesn't, we create it using the `createObjectStore()` method on the database object. The `createObjectStore()` method takes two parameters: the name of the object store and an optional configuration object. In this example, we set the key path to `"id"` and enable auto-increment for the key.

## Step 3: Closing the Database Connection

After creating the object store, it's a good practice to close the database connection.

```javascript
request.onsuccess = (event) => {
  const db = event.target.result;

  // ...

  db.close();
};

request.onerror = (event) => {
  console.error("Error opening database", event.target.error);
};
```

In the code above, we use the `db.close()` method to close the database connection. This ensures that the resources are properly released and reduces the risk of memory leaks.

## Conclusion

Creating a database in IndexedDB involves opening a connection, creating object stores, and closing the connection. With the basics covered, you can now start storing and retrieving data from the database. Make sure to explore the available API methods to perform operations like adding, updating, and deleting data.

#WebDevelopment #IndexedDB