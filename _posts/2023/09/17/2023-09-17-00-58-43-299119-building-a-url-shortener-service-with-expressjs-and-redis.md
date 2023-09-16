---
layout: post
title: "Building a URL shortener service with Express.js and Redis"
description: " "
date: 2023-09-17
tags: [hashtags, ExpressJS, Redis]
comments: true
share: true
---

URL shorteners are essential tools that allow us to shorten long URLs into more manageable and shareable links. In this blog post, we will explore how to build a URL shortener service using Express.js and Redis, a powerful in-memory data store.

## Prerequisites

Before we dive into the implementation, make sure you have the following prerequisites installed on your machine:

- Node.js and npm
- Express.js
- Redis

## Setting up the project

To get started, let's create a new directory for our project and initialize a new Node.js project. Open your terminal and run the following commands:

```bash
mkdir url-shortener
cd url-shortener
npm init -y
```

Next, let's install the necessary dependencies: Express.js and Redis.

```bash
npm install express redis
```

## Creating the Express.js app

Now that we have our project set up, let's create the main file `index.js` and set up our Express.js app.

```javascript
const express = require('express');
const redis = require('redis');

const app = express();
const client = redis.createClient();

app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// TODO: Define routes

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

In the code snippet above, we imported `express` and `redis` libraries and created an instance of both `express` and `redis` clients. We also set up the necessary middleware to parse JSON and URL-encoded data.

## Shortening URLs

To shorten a URL, we need to define a route that accepts a long URL and generates a unique short code for it.

```javascript
app.post('/shorten', (req, res) => {
  const { longUrl } = req.body;
  const shortCode = generateShortCode();

  client.set(shortCode, longUrl, (err) => {
    if (err) {
      res.status(500).json({ message: 'Failed to shorten URL' });
    } else {
      res.status(200).json({ shortUrl: `https://example.com/${shortCode}` });
    }
  });
});
```

In this code, we define a `POST` route `/shorten` that extracts the `longUrl` from the request body. We generate a unique `shortCode` and use `client.set()` function provided by Redis client to store the mapping of `shortCode` and `longUrl`.

## Redirecting to original URLs

To redirect users to the original URL when they access the shortened URL, we define another route that accepts the `shortCode`.

```javascript
app.get('/:shortCode', (req, res) => {
  const { shortCode } = req.params;

  client.get(shortCode, (err, longUrl) => {
    if (err || !longUrl) {
      res.status(404).json({ message: 'URL not found' });
    } else {
      res.redirect(longUrl);
    }
  });
});
```

Here, we define a `GET` route `/:shortCode` and use `client.get()` to retrieve the corresponding `longUrl`. If the `longUrl` exists, we redirect the user to it; otherwise, we return a `404` status code.

## Conclusion

In this blog post, we explored how to build a URL shortener service using Express.js and Redis. Redis provides fast and efficient data storage, while Express.js enables us to easily define routes and handle HTTP requests. By combining these technologies, we can build a robust and scalable URL shortener service. Remember to optimize your code and handle edge cases for a production-ready implementation.

#hashtags: #ExpressJS #Redis