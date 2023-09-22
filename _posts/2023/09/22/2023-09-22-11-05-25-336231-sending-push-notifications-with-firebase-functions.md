---
layout: post
title: "Sending push notifications with Firebase Functions"
description: " "
date: 2023-09-22
tags: [firebase, pushnotifications]
comments: true
share: true
---

In today's mobile-dominated world, push notifications have become an indispensable tool for engaging users and keeping them informed. Firebase, a mobile and web development platform from Google, offers a powerful solution for sending push notifications to mobile devices using Firebase Cloud Messaging (FCM). In this blog post, we will explore how to leverage Firebase Functions to send push notifications to users on Android and iOS devices.

## Why use Firebase Functions for sending push notifications?

Firebase Functions is a serverless compute platform that allows you to run backend code in response to events triggered by Firebase features and other HTTP requests. It is an ideal choice for sending push notifications as it provides a scalable and easy-to-use solution that integrates seamlessly with other Firebase services.

## Prerequisites

Before we start, make sure you have the following prerequisites:

- Node.js installed on your machine
- A Firebase project set up with FCM enabled

## Setting up Firebase Functions

1. Install the Firebase CLI by running the following command:

```
npm install -g firebase-tools
```

2. Log in to your Google account and initialize your Firebase project:

```
firebase login
firebase init
```

3. Select the Firebase project you want to use and choose the Firebase features you want to enable. Make sure to select **Functions** when prompted.

4. Install the necessary dependencies by running the following command:

```
cd functions
npm install firebase-admin
```

## Writing the Push Notification Function

Open the `index.js` file located inside the `functions` directory and replace its content with the following code:

```javascript
const functions = require('firebase-functions');
const admin = require('firebase-admin');

admin.initializeApp();

exports.sendPushNotification = functions.https.onCall(async (data, context) => {
  if (!context.auth) {
    throw new functions.https.HttpsError('unauthenticated', 'You must be authenticated to send push notifications.');
  }

  const { token, title, body } = data;

  const message = {
    token: token,
    notification: {
      title: title,
      body: body
    }
  };

  try {
    await admin.messaging().send(message);
    return { success: true };
  } catch (error) {
    throw new functions.https.HttpsError('internal', 'An error occurred while sending the push notification.', error);
  }
});
```

## Deploying the Firebase Function

To deploy the Firebase Function and make it accessible, run the following command:

```
firebase deploy --only functions
```

Once the deployment is complete, you will receive a URL for the Cloud Function. You will need this URL to call the function and send push notifications.

## Calling the Push Notification Function

To send push notifications from your client application, you can use the Firebase SDKs for Android and iOS. Here's an example using the Firebase Cloud Messaging API for Android:

```java
// Obtain the token for the device
String token = FirebaseInstanceId.getInstance().getToken();

// Prepare the data for the push notification
Map<String, String> data = new HashMap<>();
data.put("token", token);
data.put("title", "New Message");
data.put("body", "You have a new message!");

// Call the Firebase Cloud Function
FirebaseFunctions.getInstance()
  .getHttpsCallable("sendPushNotification")
  .call(data)
  .addOnSuccessListener(new OnSuccessListener<HttpsCallableResult>() {
    @Override
    public void onSuccess(HttpsCallableResult result) {
      // Notification sent successfully
    }
  })
  .addOnFailureListener(new OnFailureListener() {
    @Override
    public void onFailure(@NonNull Exception e) {
      // Error sending the notification
    }
  });
```

Make sure to replace `sendPushNotification` in the `getHttpsCallable` method with the URL of your Firebase Function.

## Conclusion

Push notifications are an effective way to engage users and provide timely updates. With Firebase Functions and FCM, you can easily send push notifications to your mobile app users. In this blog post, we covered the steps to set up Firebase Functions, write a push notification function, and call it from a client application. Now you can leverage the power of push notifications to enhance user experience and boost user engagement.

#firebase #pushnotifications