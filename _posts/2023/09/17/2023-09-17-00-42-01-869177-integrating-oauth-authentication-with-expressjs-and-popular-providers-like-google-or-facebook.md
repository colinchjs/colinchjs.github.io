---
layout: post
title: "Integrating OAuth authentication with Express.js and popular providers like Google or Facebook"
description: " "
date: 2023-09-17
tags: [Expressjs, OAuth, Authentication]
comments: true
share: true
---

In today's digital world, user authentication plays a significant role in securing web applications. OAuth has become the de facto standard for implementing authentication and authorization flows in modern web development. Integrating OAuth authentication with Express.js, a popular web application framework for Node.js, is a straightforward process that allows users to sign in using their existing credentials from providers like Google or Facebook. In this tutorial, we'll walk through the steps of integrating OAuth authentication with Express.js and these popular providers.

## Prerequisites
Before we dive into the implementation, make sure you have the following prerequisites in place:

- Basic knowledge of JavaScript and Node.js
- Familiarity with Express.js and its middleware concept
- A developer account on your targeted provider's platform (e.g., Google or Facebook)
- Node.js and npm (Node Package Manager) installed

## Step 1: Set up your project
First, let's create a new Express.js project and install the necessary dependencies. Open your terminal or command prompt and execute the following commands:

```bash
$ mkdir express-oauth-example
$ cd express-oauth-example
$ npm init --yes
$ npm install express passport passport-google-oauth20 passport-facebook express-session --save
```

## Step 2: Configure OAuth credentials
Next, we need to obtain OAuth credentials from the provider(s) you want to integrate. Follow these steps:

### Google
1. Go to the [Google Developers Console](https://console.developers.google.com/).
2. Create a new project or select an existing one.
3. Enable the **Google+ API** and **Google Identity Toolkit API**.
4. Go to **Credentials** > **Create Credentials** > **OAuth client ID**.
5. Configure the OAuth consent screen, providing necessary details.
6. Select **Web Application** as the application type.
7. Add `http://localhost:3000/auth/google/callback` as an **Authorized redirect URI**.
8. Copy the generated **Client ID** and **Client Secret**.

### Facebook
1. Go to the [Facebook Developers Portal](https://developers.facebook.com/).
2. Create a new app or select an existing one.
3. Go to **Settings** > **Basic**.
4. Add `http://localhost:3000/auth/facebook/callback` as a **Valid OAuth Redirect URI**.
5. Copy the **App ID** and **App Secret**.

## Step 3: Initialize Express.js and Passport.js
In your project's main file (e.g., `index.js`), include the necessary dependencies and set up Express.js and Passport.js:

```javascript
const express = require("express");
const passport = require("passport");
const session = require("express-session");

const app = express();

// Session middleware
app.use(session({ secret: "your-secret-key", resave: true, saveUninitialized: true }));

// Passport middleware
app.use(passport.initialize());
app.use(passport.session());
```

## Step 4: Configure Passport.js strategies
To integrate OAuth with Express.js, we need to configure Passport.js strategies for each provider. Add the following code to your `index.js` file:

```javascript
const GoogleStrategy = require("passport-google-oauth20").Strategy;
const FacebookStrategy = require("passport-facebook").Strategy;

// Google strategy
passport.use(new GoogleStrategy({
    clientID: "your-google-client-id",
    clientSecret: "your-google-client-secret",
    callbackURL: "http://localhost:3000/auth/google/callback"
}, (accessToken, refreshToken, profile, done) => {
    // Handle user information
}));

// Facebook strategy
passport.use(new FacebookStrategy({
    clientID: "your-facebook-app-id",
    clientSecret: "your-facebook-app-secret",
    callbackURL: "http://localhost:3000/auth/facebook/callback"
}, (accessToken, refreshToken, profile, done) => {
    // Handle user information
}));
```

Replace the placeholders (`your-google-client-id`, `your-google-client-secret`, `your-facebook-app-id`, `your-facebook-app-secret`) with the respective credentials obtained from the provider(s).

## Step 5: Define authentication routes
Create the necessary routes for authentication:

```javascript
// Google authentication
app.get("/auth/google", passport.authenticate("google", { scope: ["profile"] }));

app.get("/auth/google/callback", passport.authenticate("google"), (req, res) => {
    // Redirect or handle the successful authentication
});

// Facebook authentication
app.get("/auth/facebook", passport.authenticate("facebook"));

app.get("/auth/facebook/callback", passport.authenticate("facebook"), (req, res) => {
    // Redirect or handle the successful authentication
});
```

## Step 6: Protect your routes
You can now protect specific routes by adding the following middleware:

```javascript
function ensureAuthenticated(req, res, next) {
    if (req.isAuthenticated()) {
        return next();
    }

    res.redirect("/login");
}

app.get("/dashboard", ensureAuthenticated, (req, res) => {
    // Render the dashboard or handle the protected route
});
```

## Step 7: Start the application
Finally, start your Express.js application by running the following command:

```bash
$ node index.js
```

Now, you can navigate to `http://localhost:3000` in your browser and test the OAuth authentication flow with the specified providers.

Congratulations! You've successfully integrated OAuth authentication with Express.js and popular providers like Google or Facebook. Feel free to customize the implementation based on your specific requirements and explore additional features like storing user information, handling session management, or integrating with other OAuth providers.

#Expressjs #OAuth #Authentication