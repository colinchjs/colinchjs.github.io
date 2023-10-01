---
layout: post
title: "Adding data to an object store in IndexedDB"
description: " "
date: 2023-10-01
tags: [TechTips, IndexedDB]
comments: true
share: true
---

One common task in IndexedDB is adding data to an object store. An object store is similar to a table in a traditional database and is where the actual data is stored. To add data to an object store, you'll need to follow these steps:

1. Open a connection to the database:
```javascript
const request = indexedDB.open('my-database', 1);

request.onerror = (event) => {
  console.error('Database error:', event.target.error);
};

request.onupgradeneeded = (event) => {
  const db = event.target.result;

  // Create an object store if it doesn't exist
  if (!db.objectStoreNames.contains('my-store')) {
    db.createObjectStore('my-store', { keyPath: 'id' });
  }
};

request.onsuccess = (event) => {
  const db = event.target.result;
  addData(db);
};
```

2. Add data to the object store:
```javascript
function addData(db) {
  const transaction = db.transaction('my-store', 'readwrite');
  const objectStore = transaction.objectStore('my-store');

  const data = { id: 1, name: 'John Doe', email: 'john@example.com' };

  const request = objectStore.add(data);

  request.onsuccess = (event) => {
    console.log('Data added successfully');
  };

  request.onerror = (event) => {
    console.error('Error adding data:', event.target.error);
  };
}
```

In this example, we first opened a connection to the database using `indexedDB.open()`. If the database or object store doesn't exist, we use the `onupgradeneeded` event to create them. Otherwise, we proceed to the `onsuccess` event.

Inside the `addData()` function, we create a new transaction with the object store in `'readwrite'` mode to perform write operations. We then use `objectStore.add()` to add the data to the object store. If the operation is successful, `onsuccess` will be triggered, otherwise `onerror` will be called.

Remember to handle errors appropriately and to close the database connection when you're done with it to free up resources.

#TechTips #IndexedDB