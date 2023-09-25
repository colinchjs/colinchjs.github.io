---
layout: post
title: "React.js data syncing with Firebase Realtime Database"
description: " "
date: 2023-09-25
tags: [React, Firebase]
comments: true
share: true
---

In this tutorial, we will explore how to sync data between a React.js application and the Firebase Realtime Database. Firebase Realtime Database is a cloud-hosted NoSQL database that allows you to store and sync data in real-time.

## Prerequisites

To follow along, you'll need the following:

- Node.js and npm installed on your machine
- Basic knowledge of React.js and Firebase

## Setup

### Step 1: Create a Firebase project

1. Visit the [Firebase Console](https://console.firebase.google.com/) and create a new project.
2. Enable the Realtime Database from the Firebase Console. You can find it in the "Database" section.
3. Set the rules of your database to allow read and write access for testing purposes.

### Step 2: Set up a React.js project

1. Open your terminal and navigate to the directory where you want to create your React.js project.
2. Run the following command to create a new React.js project:

```bash
npx create-react-app firebase-sync-example
```

3. Change directory to the newly created project:

```bash
cd firebase-sync-example
```

4. Install the Firebase JavaScript SDK and Firebase React Hooks by running:

```bash
npm install firebase react-firebase-hooks
```

### Step 3: Connect React.js application to Firebase

1. Create a new file called `firebase.js` in the `src` directory.
2. Open the `firebase.js` file and add the following code:

```javascript
import firebase from 'firebase/app';
import 'firebase/database';

const firebaseConfig = {
  // Your Firebase project configuration
};

firebase.initializeApp(firebaseConfig);

export default firebase;
```

3. Replace the `firebaseConfig` object with the configuration from your Firebase project.

### Step 4: Fetch and Sync Data

1. Open the `src/App.js` file and replace the default code with the following:

```javascript
import React from 'react';
import firebase from './firebase';
import { useFirebaseDatabase } from 'react-firebase-hooks/database';

function App() {
  const [data, loading, error] = useFirebaseDatabase(
    firebase.database().ref('data')
  );

  if (loading) {
    return <div>Loading...</div>;
  }

  if (error) {
    return <div>Error: {error.message}</div>;
  }

  return (
    <div>
      <h1>Realtime Data Syncing with Firebase</h1>
      {data && <pre>{JSON.stringify(data, null, 2)}</pre>}
    </div>
  );
}

export default App;
```

2. This code uses the `useFirebaseDatabase` hook from `react-firebase-hooks` to fetch and sync data from the `data` node in the Firebase Realtime Database.
3. The fetched data is displayed in a `pre` element, which shows the data in JSON format.

### Step 5: Run the React.js application

1. Open your terminal and make sure you are in the project directory.
2. Run the following command to start the React.js development server:

```bash
npm start
```

3. Open your browser and navigate to `http://localhost:3000` to see the application in action.
4. Any changes you make to the data in the Firebase Realtime Database will be automatically synced and reflected in the React.js application.

## Conclusion

In this tutorial, you've learned how to sync data between a React.js application and the Firebase Realtime Database. You've also learned how to fetch and display real-time data using the `react-firebase-hooks` library. With this knowledge, you can now build real-time collaborative applications that update in real-time as data changes in the database. Happy coding!

#React #Firebase