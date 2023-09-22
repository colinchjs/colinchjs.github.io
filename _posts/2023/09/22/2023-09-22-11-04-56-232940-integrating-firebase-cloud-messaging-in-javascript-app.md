---
layout: post
title: "Integrating Firebase cloud messaging in JavaScript app"
description: " "
date: 2023-09-22
tags: [firebase]
comments: true
share: true
---

Firebase Cloud Messaging (FCM) is a cross-platform messaging solution that allows you to send push notifications and messages to your users' devices. It provides reliable delivery of messages at no cost.

In this tutorial, we will learn how to integrate Firebase Cloud Messaging into a JavaScript app. Let's get started!

## Prerequisites

Before you begin, make sure you have the following:

1. A Firebase project: Create a new project in the Firebase console if you haven't already. Take note of the project's **Server Key** and **Sender ID**.

2. An HTML file: Create an HTML file with a basic structure.

## Setting up Firebase Cloud Messaging

To integrate Firebase Cloud Messaging in your JavaScript app, follow these steps:

1. Include the Firebase JavaScript SDK in your HTML file:

   ```html
   <script src="https://www.gstatic.com/firebasejs/8.7.1/firebase-app.js"></script>
   <script src="https://www.gstatic.com/firebasejs/8.7.1/firebase-messaging.js"></script>
   ```

2. Initialize Firebase in your JavaScript file:

   ```javascript
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_AUTH_DOMAIN",
     projectId: "YOUR_PROJECT_ID",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };

   firebase.initializeApp(firebaseConfig);
   ```

   Make sure to replace the placeholder values with your project's information from the Firebase console.

3. Retrieve the Firebase Cloud Messaging token:

   ```javascript
   const messaging = firebase.messaging();
   messaging.getToken({ vapidKey: 'YOUR_PUBLIC_VAPID_KEY' }).then((currentToken) => {
     if (currentToken) {
       console.log('Token:', currentToken);
       // Send this token to your server to enable sending push notifications
     } else {
       console.error('Unable to get token.');
     }
   }).catch((err) => {
     console.error('Error getting token:', err);
   });
   ```

   Replace `'YOUR_PUBLIC_VAPID_KEY'` with a valid VAPID key. VAPID (Voluntary Application Server Identification) is used for web push notifications.

## Sending Push Notifications

Now that we have obtained the Cloud Messaging token, we can use it to send push notifications to the user's device. This can be done either from a server or directly from the Firebase console.

To send a push notification from the Firebase console, follow these steps:

1. Go to the Firebase console and select your project.

2. In the left sidebar, click on **Cloud Messaging**.

3. Click on the **New Notification** button.

4. Enter the details for your notification, including the message, title, and target audience.

5. Click on the **Send Test Message** button to test the notification or click on **Send** to send it to all eligible devices.

That's it! You have successfully integrated Firebase Cloud Messaging in your JavaScript app and sent a push notification.

## Conclusion

Integrating Firebase Cloud Messaging in a JavaScript app can greatly improve user engagement by sending push notifications. By following the steps mentioned in this tutorial, you can easily set up Firebase Cloud Messaging in your own app.

#firebase #FCM