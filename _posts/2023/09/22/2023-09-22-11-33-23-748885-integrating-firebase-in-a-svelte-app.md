---
layout: post
title: "Integrating Firebase in a Svelte app"
description: " "
date: 2023-09-22
tags: [firebase, svelte]
comments: true
share: true
---

## Prerequisites

Before we dive into the integration process, make sure you have the following:

- A Svelte app setup and running.
- A Firebase project created on the [Firebase Console](https://console.firebase.google.com/).

## Step 1: Install Firebase SDK

To get started, we need to install the Firebase SDK in our Svelte app. Open your terminal and navigate to your project directory. Run the following command to install the Firebase JavaScript library:

```bash
npm install firebase
```

## Step 2: Configure Firebase

Next, we need to configure Firebase by providing the necessary credentials. Go to your Firebase project settings and locate the **Web** configuration. Copy the following information:

- apiKey
- authDomain
- projectId
- storageBucket
- messagingSenderId
- appId

Create a new file in your Svelte app's source directory, e.g., `firebaseConfig.js`. Paste the copied configuration inside the file using the following format:

```javascript
export const firebaseConfig = {
  apiKey: '<YOUR_API_KEY>',
  authDomain: '<YOUR_AUTH_DOMAIN>',
  projectId: '<YOUR_PROJECT_ID>',
  storageBucket: '<YOUR_STORAGE_BUCKET>',
  messagingSenderId: '<YOUR_MESSAGING_SENDER_ID>',
  appId: '<YOUR_APP_ID>'
};
```

Remember to replace `<YOUR_API_KEY>`, `<YOUR_AUTH_DOMAIN>`, and other placeholders with the respective values from your Firebase project.

## Step 3: Initialize Firebase

Now, in your Svelte app's main entry file, typically `main.js` or `App.svelte`, import the Firebase SDK and initialize it with the configuration:

```javascript
import * as firebase from 'firebase/app';
import { firebaseConfig } from './firebaseConfig';

firebase.initializeApp(firebaseConfig);
```

## Step 4: Using Firebase Services

With Firebase successfully integrated into our Svelte app, let's explore a few examples of how to leverage its services.

### Real-time Database

To use the Firebase Real-time Database, import the required modules in your Svelte component:

```javascript
import { getDatabase, ref, set } from 'firebase/database';

// Example usage
const db = getDatabase(); // Get a reference to the database
const dataRef = ref(db, 'data'); // Get a reference to a specific node
set(dataRef, 'Hello, Firebase!').then(() => {
  console.log('Data written to Firebase Real-time Database');
});
```

### User Authentication

To enable user authentication in your Svelte app, import the required modules:

```javascript
import { getAuth, createUserWithEmailAndPassword } from 'firebase/auth';

// Example usage
const auth = getAuth(); // Get a reference to the authentication service
createUserWithEmailAndPassword(auth, email, password)
  .then((userCredential) => {
    console.log('User created:', userCredential.user);
  })
  .catch((error) => {
    console.error('Error creating user:', error);
  });
```

### Cloud Messaging

To send notifications using Firebase Cloud Messaging, import the necessary modules:

```javascript
import { getMessaging, getToken } from 'firebase/messaging';

// Example usage
const messaging = getMessaging(); // Get a reference to the messaging service
getToken(messaging, { vapidKey: '<YOUR_VAPID_KEY>' })
  .then((currentToken) => {
    console.log('Device token:', currentToken);
  })
  .catch((error) => {
    console.error('Error retrieving device token:', error);
  });
```

Replace `<YOUR_VAPID_KEY>` with your own VAPID key for push notifications.

## Conclusion

Integrating Firebase into a Svelte app opens up a world of possibilities for real-time data syncing, user authentication, and cloud messaging. By following the steps outlined in this blog post, you can seamlessly leverage Firebase's powerful capabilities within your Svelte application.

#firebase #svelte