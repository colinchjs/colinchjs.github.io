---
layout: post
title: "Cloud functions automation with Firebase Firestore"
description: " "
date: 2023-09-22
tags: [Firebase, CloudFunctions]
comments: true
share: true
---

In this blog post, we will explore cloud functions automation using Firebase Firestore. Firebase Firestore is a NoSQL cloud-based database designed to store and sync data for mobile and web applications. Cloud Functions, on the other hand, enables developers to run custom backend code in response to events and HTTPS requests.

## Setting Up Cloud Functions

To get started with cloud functions automation, you first need to set up a Firebase project and initialize Cloud Functions. Follow these steps:

1. Install the Firebase CLI by running the following command:
   ```
   npm install -g firebase-tools
   ```

2. Set up your Firebase project using your Google account credentials:
   ```
   firebase login
   ```

3. Initialize Cloud Functions in your Firebase project:
   ```
   firebase init functions
   ```

## Creating a Cloud Function

Now that we have set up Cloud Functions, we can start creating a function that automates specific tasks when changes occur in Firebase Firestore. Let's say we want to send an email whenever a new document is added to a certain collection. Here's the code for our function:

```javascript
const functions = require('firebase-functions');
const admin = require('firebase-admin');
const nodemailer = require('nodemailer');

admin.initializeApp();

exports.sendEmailOnFirestoreChange = functions.firestore
  .document('collection/{docId}')
  .onCreate(async (snapshot) => {
    const newData = snapshot.data();
    const mailOptions = {
      from: '<sender@example.com>',
      to: '<recipient@example.com>',
      subject: 'New Document Added',
      text: `A new document with ID ${snapshot.id} has been added to the collection.`,
    };

    try {
      const transporter = nodemailer.createTransport({
        service: 'gmail',
        auth: {
          user: '<your-gmail-account>@gmail.com',
          pass: '<your-gmail-password>',
        },
      });
      await transporter.sendMail(mailOptions);
      console.log('Email sent successfully!');
    } catch (error) {
      console.error('Error sending email:', error);
    }
  });
```

## Deploying the Cloud Function

To deploy the cloud function, follow these steps:

1. Navigate to your project's root directory and deploy the function using the Firebase CLI:
   ```
   firebase deploy --only functions
   ```

2. Once the deployment is successful, you can find the URL of your function in the Firebase console. It should be in the format: `https://REGION-PROJECT_ID.cloudfunctions.net/sendEmailOnFirestoreChange`.

## Testing the Cloud Function

To test the cloud function, add a new document to the specified Firestore collection. You should receive an email at the recipient address specified in the code.

## Conclusion

Firebase Firestore and Cloud Functions provide powerful tools for automating tasks in your Firebase project. In this blog post, we explored how to set up and create a cloud function to send an email when a new document is added to Firestore. With cloud functions automation, you can build more efficient and scalable applications. #Firebase #CloudFunctions #Firestore #Automation