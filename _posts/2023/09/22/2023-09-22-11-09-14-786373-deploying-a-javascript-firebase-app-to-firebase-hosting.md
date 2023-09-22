---
layout: post
title: "Deploying a JavaScript Firebase app to Firebase hosting"
description: " "
date: 2023-09-22
tags: [firebase, hosting]
comments: true
share: true
---

Firebase Hosting is a powerful platform that allows you to deploy and host your web applications with ease. In this blog post, we will walk through the steps to deploy a JavaScript Firebase app to Firebase Hosting.

## Prerequisites

Before deploying your app, make sure you have the following:

- A Firebase project created
- Firebase CLI installed

## Step 1: Set up Firebase project

To begin, navigate to the Firebase console and create a new project or select an existing project. Once you have your project set up, open your terminal and log in to Firebase CLI using the command:

```
firebase login
```

This will prompt you to authenticate with your Google account.

## Step 2: Set up your project folder

In your local project folder, make sure you have a `firebase.json` file that defines your project configuration. If you don't have one, create a new file and paste the following content:

```json
{
  "hosting": {
    "public": "public",
    "ignore": [
      "firebase.json",
      "**/.*",
      "**/node_modules/**"
    ],
    "rewrites": [
      {
        "source": "**",
        "destination": "/index.html"
      }
    ]
  }
}
```

This configuration specifies that the `public` folder is the root of your Firebase Hosting deployment, and all requests will be redirected to `index.html`.

## Step 3: Build your project

Before deploying your app, make sure you have built your project by running the appropriate command. This step may vary depending on the build system or tools you are using.

For example, if you are using npm and webpack, you can build your project using the following command:

```
npm run build
```

Make sure your build artifacts are generated in the `public` directory.

## Step 4: Deploy to Firebase Hosting

Once your project is built, you can deploy it to Firebase Hosting using the following command:

```
firebase deploy --only hosting
```

This command will deploy the contents of your `public` directory to Firebase Hosting. You will receive a deployment URL once the deployment process is complete.

## Conclusion

In this blog post, we have learned how to deploy a JavaScript Firebase app to Firebase Hosting. By following these steps, you can easily host your web applications and make them accessible to users worldwide. So go ahead, deploy your app and let the world experience your amazing JavaScript-powered Firebase application!

#firebase #hosting