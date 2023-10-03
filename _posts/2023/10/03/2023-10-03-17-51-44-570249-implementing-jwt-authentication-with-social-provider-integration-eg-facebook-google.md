---
layout: post
title: "Implementing JWT authentication with social provider integration (e.g., Facebook, Google)"
description: " "
date: 2023-10-03
tags: []
comments: true
share: true
---

With the increase in popularity of social logins, it has become essential for web applications to provide authentication options with social providers like Facebook and Google. JSON Web Tokens (JWT) offer a simple and secure way to implement authentication, providing a stateless mechanism for client-server communication. In this blog post, we'll explore how to implement JWT authentication with social provider integration.

## Prerequisites
1. **Node.js** - Ensure you have Node.js installed on your system.
2. **Express.js** - Install the Express.js framework to build our application.

## Getting Started
First, let's create a new project directory and initialize it with `npm init`.
```shell
mkdir jwt-authentication
cd jwt-authentication
npm init -y
```

Next, install the required dependencies:
```shell
npm install express jsonwebtoken passport passport-facebook-token passport-google-token
```

## Implementing Facebook Login
To integrate Facebook login, we'll use the `passport-facebook-token` library. Create a new file called `facebookAuth.js` and implement the following code:

```javascript
const passport = require('passport');
const FacebookTokenStrategy = require('passport-facebook-token');

passport.use(
  'facebook',
  new FacebookTokenStrategy(
    {
      clientID: 'YOUR_FACEBOOK_APP_ID',
      clientSecret: 'YOUR_FACEBOOK_APP_SECRET',
    },
    (accessToken, refreshToken, profile, done) => {
      // Extract information from the profile and save user
      // Return user information
    }
  )
);

module.exports = passport.authenticate('facebook', { session: false });
```

Replace `YOUR_FACEBOOK_APP_ID` and `YOUR_FACEBOOK_APP_SECRET` with your own Facebook app credentials.

Now, let's create an authentication route for Facebook login in a file named `authRoutes.js`:

```javascript
const express = require('express');
const router = express.Router();
const facebookAuth = require('./facebookAuth');

router.post('/auth/facebook', facebookAuth);

module.exports = router;
```

## Implementing Google Login
To integrate Google login, we'll use the `passport-google-token` library. Add the following code to a new file called `googleAuth.js`:

```javascript
const passport = require('passport');
const GoogleTokenStrategy = require('passport-google-token');

passport.use(
  'google',
  new GoogleTokenStrategy(
    {
      clientID: 'YOUR_GOOGLE_CLIENT_ID',
      clientSecret: 'YOUR_GOOGLE_CLIENT_SECRET',
    },
    (accessToken, refreshToken, profile, done) => {
      // Extract information from the profile and save user
      // Return user information
    }
  )
);

module.exports = passport.authenticate('google', { session: false });
```

Replace `YOUR_GOOGLE_CLIENT_ID` and `YOUR_GOOGLE_CLIENT_SECRET` with your own Google app credentials.

Next, add an authentication route for Google login in the `authRoutes.js` file:

```javascript
const googleAuth = require('./googleAuth');

router.post('/auth/google', googleAuth);

module.exports = router;
```

## Generating JWT Tokens
Now that our authentication strategies are set up, we can generate JWT tokens for authenticated users. We'll create a new file called `jwtGenerator.js` with the following code:

```javascript
const jwt = require('jsonwebtoken');

const generateJwtToken = (user) => {
  const payload = {
    id: user.id,
    email: user.email,
    // Add additional user data if needed
  };

  const token = jwt.sign(payload, 'YOUR_SECRET_KEY', { expiresIn: '1h' });

  return token;
};

module.exports = generateJwtToken;
```

Replace `YOUR_SECRET_KEY` with your desired secret key for signing the token.

## Putting It All Together
In your main application file (e.g., `index.js`), import the required routes and use them in your Express app:

```javascript
const express = require('express');
const authRoutes = require('./authRoutes');
const app = express();

app.use(express.json());
app.use(authRoutes);

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

## Conclusion
Implementing JWT authentication with social provider integration offers a secure and convenient way for users to log in to your web application. By following the steps outlined in this blog post, you can easily integrate Facebook and Google login using JSON Web Tokens.