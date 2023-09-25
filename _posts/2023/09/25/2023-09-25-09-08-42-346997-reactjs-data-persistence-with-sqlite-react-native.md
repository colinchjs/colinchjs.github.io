---
layout: post
title: "React.js data persistence with SQLite (React Native)"
description: " "
date: 2023-09-25
tags: [reactnative, SQLite]
comments: true
share: true
---

In mobile app development, data persistence is crucial to ensure that user data is stored and retrieved even after the app is closed or the device is restarted. SQLite is a lightweight, serverless, and self-contained database engine that can seamlessly integrate with React Native to provide persistent storage for your app.

## Setting up SQLite in React Native

To get started, you need to install the necessary dependencies for using SQLite with React Native. Open your terminal and run the following commands:

```sh
npm install --save react-native-sqlite-storage
npx pod-install
```

## Creating a SQLite database

Once the installation is complete, you can create a SQLite database by importing the `openDatabase` function from the `react-native-sqlite-storage` package. Here's an example of creating a database and a table in React Native:

```javascript
import SQLite from 'react-native-sqlite-storage';

const db = SQLite.openDatabase(
  {
    name: 'mydb.db',
    location: 'default',
  },
  () => console.log('Database opened'),
  error => console.error('Failed to open database:', error)
);

db.transaction(tx => {
  tx.executeSql(
    'CREATE TABLE IF NOT EXISTS users (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT, age INTEGER)'
  );
});

```

In the above code, we first import the `SQLite` package and then use the `openDatabase` function to create a new database called `mydb.db`. We also specify the location of the database as `default`, which means it will be stored in the app's default location.

Inside the `transaction` callback, we execute an SQL statement to create a table called `users` with three columns: `id`, `name`, and `age`. The `CREATE TABLE IF NOT EXISTS` statement ensures that the table is only created if it doesn't already exist.

## Performing CRUD operations

Now that we have our database set up, we can perform CRUD (Create, Read, Update, Delete) operations on the SQLite database. Here's an example of inserting data into the `users` table:

```javascript
db.transaction(tx => {
  tx.executeSql(
    'INSERT INTO users (name, age) VALUES (?, ?)',
    ['John Doe', 25],
    (_, { rowsAffected }) => {
      if (rowsAffected > 0) {
        console.log('Data saved successfully!');
      }
    },
    (_, error) => console.error('Failed to save data:', error)
  );
});
```

In the above code, we use the `executeSql` method to execute an SQL statement. We pass the `INSERT INTO` statement along with the values to be inserted as an array.

Similarly, you can perform other CRUD operations like reading, updating, and deleting records from the database using the `executeSql` method with appropriate SQL statements.

## Conclusion

SQLite provides a reliable and efficient way to persist data in React Native apps. By following the steps outlined in this article, you can set up a SQLite database, create tables, and perform CRUD operations to store and retrieve data in your React Native app. Adding data persistence enhances the user experience and ensures that important data is retained even when the app is not actively being used.

#reactnative #SQLite #datapersistence