---
layout: post
title: "React.js data persistence with IndexedDB"
description: " "
date: 2023-09-25
tags: [techblog, reactjs]
comments: true
share: true
---

One of the challenges when building web applications is persisting data on the client-side. Traditional methods like cookies or local storage have limitations when it comes to storing larger amounts of data. That's where IndexedDB comes in - a powerful API built into modern browsers that allows storing and retrieving structured data.

In this blog post, we'll explore how to utilize IndexedDB with React.js to achieve data persistence within our application. Let's get started!

## What is IndexedDB?
IndexedDB is a NoSQL, transactional database maintained by the browser. It provides a way to store and retrieve large amounts of structured data, performing advanced operations like indexing, querying, and sorting on that data.

## Setting Up the React.js Application
To begin, let's set up a basic React.js application. You can use Create React App or any other boilerplate of your choice. Make sure you have the necessary dependencies installed:

```bash
npx create-react-app my-app
cd my-app
npm install indexeddb-promised
```

## Creating a Database
To interact with IndexedDB, we'll use the `indexeddb-promised` library. Let's create a new file called `database.js` and add the following code:

```javascript
import Idb from 'indexeddb-promised';

const db = new Idb('my-database', 1, upgradeDb => {
  const store = upgradeDb.createObjectStore('my-store', { keyPath: 'id' });
  store.createIndex('name', 'name', { unique: false });
});

export default db;
```

In this code, we create a new IndexedDB database named 'my-database' with a single object store named 'my-store'. The object store has a key path set to 'id' and an index on the 'name' property.

## Interacting with the Database
Now that we have our database set up, let's create a component that will use IndexedDB for data persistence. We'll call it `DataComponent.js`. Here's an example implementation:

```javascript
import React, { useEffect, useState } from 'react';
import db from './database';

const DataComponent = () => {
  const [data, setData] = useState([]);

  useEffect(() => {
    const fetchData = async () => {
      const transaction = db.transaction('my-store', 'readwrite');
      const store = transaction.objectStore('my-store');
      const items = await store.getAll();
      setData(items);
    };

    fetchData();
  }, []);

  return (
    <div>
      {data.map(item => (
        <div key={item.id}>
          <h3>{item.name}</h3>
          <p>{item.description}</p>
        </div>
      ))}
    </div>
  );
};

export default DataComponent;
```

In this code, we create a functional component `DataComponent` that fetches data from the IndexedDB database using the `getAll` method. The fetched data is stored in the component's state and rendered as a list.

## Storing Data
To store data in IndexedDB, we can add a form to our `DataComponent` that allows users to input and save new data. Here's an updated version of the component:

```javascript
// ...other imports

const DataComponent = () => {
  const [data, setData] = useState([]);
  const [name, setName] = useState('');
  const [description, setDescription] = useState('');

  const handleSave = async () => {
    const transaction = db.transaction('my-store', 'readwrite');
    const store = transaction.objectStore('my-store');
    const newItem = { id: Date.now(), name, description };
    await store.add(newItem);
    setData([...data, newItem]);
    setName('');
    setDescription('');
  };

  return (
    <div>
      {/* Render data list here */}
      
      <form>
        <input
          type="text"
          value={name}
          onChange={e => setName(e.target.value)}
          placeholder="Name"
        />
        <textarea
          value={description}
          onChange={e => setDescription(e.target.value)}
          placeholder="Description"
        />
        <button type="submit" onClick={handleSave}>
          Save
        </button>
      </form>
    </div>
  );
};

export default DataComponent;
```

In this code, we add a form with input fields for name and description. On form submission, we create a new object with an auto-generated ID and add it to the IndexedDB database using the `add` method. The component's state is updated to include the new item.

## Conclusion
IndexedDB provides a robust solution for data persistence in web applications. By integrating it with React.js, we can easily store, retrieve, and manipulate data on the client-side. In this blog post, we explored the basics of using IndexedDB with React.js, creating a database, fetching data, and storing new data.

Feel free to explore more advanced features of IndexedDB and optimize your application's data persistence using this powerful API. Happy coding!

#techblog #reactjs #indexeddb #webdevelopment