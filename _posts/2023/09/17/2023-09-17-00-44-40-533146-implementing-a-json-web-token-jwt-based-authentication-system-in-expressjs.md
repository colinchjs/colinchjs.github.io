---
layout: post
title: "Implementing a JSON Web Token (JWT) based authentication system in Express.js"
description: " "
date: 2023-09-17
tags: [ExpressJs]
comments: true
share: true
---

In this blog post, we will explore how to implement a JSON Web Token (JWT) based authentication system in Express.js. JWT is a widely used standard for securely exchanging information between parties in a web application.

## What is JSON Web Token (JWT)?

A JSON Web Token (JWT) is a compact, URL-safe means of representing claims between two parties. It consists of three parts: a header, a payload, and a signature. The header and payload are JSON objects encoded as Base64, and together they form the JWT. The signature is used to verify the authenticity of the token.

## Installing necessary packages

We will require the following packages to implement JWT-based authentication in Express.js:

```bash
npm install express jsonwebtoken bcrypt
```

- `express`: for building our web application
- `jsonwebtoken`: for creating and verifying JWTs
- `bcrypt`: for hashing and comparing passwords

## Setting up the Express.js application

Let's start by setting up a basic Express.js server with a user registration and login endpoints.

First, create a new file named `server.js` and add the following code:

```javascript
const express = require('express');
const app = express();

app.use(express.json());

app.post('/register', (req, res) => {
  // User registration logic
});

app.post('/login', (req, res) => {
  // User login logic
});

const port = process.env.PORT || 3000;
app.listen(port, () => {
  console.log(`Server listening on port ${port}`);
});
```

## User Registration

To handle the user registration, we need to create a new user in our database. For simplicity, we'll store the user data in memory.

```javascript
const users = [];

app.post('/register', (req, res) => {
  const { email, password } = req.body;

  // Check if the user already exists
  const userExists = users.find((user) => user.email === email);
  if (userExists) {
    return res.status(400).json({ message: 'User already exists' });
  }

  // Hash the password using bcrypt
  const saltRounds = 10;
  bcrypt.hash(password, saltRounds, (err, hash) => {
    if (err) {
      return res.status(500).json({ message: 'Failed to create user' });
    }

    // Create a new user object
    const newUser = {
      email,
      password: hash,
    };

    // Save the user
    users.push(newUser);

    // Send success response
    res.status(200).json({ message: 'User created successfully' });
  });
});
```

## User Login

To handle user login, we will compare the provided password with the stored hashed password using bcrypt. If the passwords match, we will generate a JWT and send it back to the client.

```javascript
app.post('/login', (req, res) => {
  const { email, password } = req.body;

  // Find the user in our database
  const user = users.find((user) => user.email === email);
  if (!user) {
    return res.status(404).json({ message: 'User not found' });
  }

  // Compare the passwords
  bcrypt.compare(password, user.password, (err, result) => {
    if (err || !result) {
      return res.status(401).json({ message: 'Invalid credentials' });
    }

    // Generate a JWT
    const token = jwt.sign({ email }, 'secret_key', { expiresIn: '1h' });

    // Send the token back to the client
    res.status(200).json({ token });
  });
});
```

## Conclusion

In this blog post, we explored how to implement a JSON Web Token (JWT) based authentication system in Express.js. We covered user registration, login, and generating JWTs for authenticated users. JWT-based authentication is a secure and widely used method for protecting routes and verifying the authenticity of users in web applications.

Implementing JWT-based authentication adds an extra layer of security to your Express.js applications. It ensures that only authenticated users can access protected routes by providing a token that represents their identity.

# #ExpressJs #JWT