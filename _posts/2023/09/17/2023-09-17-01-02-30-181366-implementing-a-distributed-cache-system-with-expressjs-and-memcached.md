---
layout: post
title: "Implementing a distributed cache system with Express.js and Memcached"
description: " "
date: 2023-09-17
tags: [ExpressJS, Memcached]
comments: true
share: true
---

In today's fast-paced digital world, having a performant and scalable web application is crucial. One way to achieve this is by implementing a distributed cache system. In this blog post, we will explore how to build a distributed cache system using Express.js, a popular web framework for Node.js, and Memcached, a high-performance distributed memory object caching system.

## What is a Cache System?

A cache system is a temporary storage mechanism that stores frequently accessed data, allowing subsequent requests to be served faster. It helps in reducing the load on databases and improves the overall response time of the application. A distributed cache system takes this concept further by distributing the cache across multiple nodes to enhance scalability and fault tolerance.

## Why use Express.js and Memcached?

Express.js provides a powerful and flexible platform for building web applications in Node.js. It offers easy routing, middleware support, and a modular architecture that makes it an ideal choice for implementing a distributed cache system. Memcached, on the other hand, is a battle-tested caching system known for its speed and scalability. It supports distributed caching by allowing you to connect multiple cache nodes together.

## Setting up Memcached

To get started, we need to set up a Memcached server. You can install it locally or use a cloud-based Memcached service like AWS ElastiCache or MemCachier. Once set up, make sure you have the host and port details for your Memcached server.

## Installing Dependencies

Create a new Express.js project and navigate to the project directory in your terminal. Then, install the necessary dependencies by running the following command:

```bash
npm install express memcached
```

## Creating the Cache Middleware

In Express.js, middleware functions are key components for handling requests. We can create a custom middleware function to handle caching using Memcached. Below is an example of how you can create a cache middleware in Express.js:

```javascript
const Memcached = require('memcached');

const memcached = new Memcached('localhost:11211'); // replace with your Memcached server details

function cacheMiddleware(req, res, next) {
  const key = req.originalUrl;

  memcached.get(key, (err, data) => {
    if (err || !data) {
      // Data not found in cache, proceed with the original request
      res.sendResponse = res.send;
      res.send = (body) => {
        memcached.set(key, body, 60, (cacheErr) => {
          if (cacheErr) {
            console.error(cacheErr);
          }
        });
        res.sendResponse(body);
      };
      next();
    } else {
      // Data found in cache
      res.send(data);
    }
  });
}

module.exports = cacheMiddleware;
```

In the above code, we create an instance of `Memcached` with the appropriate host and port details. The `cacheMiddleware` function checks if the requested data is available in the cache. If not, it proceeds with the original request and caches the response using `memcached.set()`. If the data is found in the cache, it sends the cached response.

## Adding the Cache Middleware to Routes

To utilize the cache middleware, we need to apply it to the appropriate routes in our Express.js application. Here's an example of how you can use the cache middleware with a GET route:

```javascript
const express = require('express');
const cacheMiddleware = require('./cacheMiddleware');

const app = express();

app.get('/api/users', cacheMiddleware, (req, res) => {
  // Your logic to fetch user data from the database or an API
  const users = [
    { id: 1, name: 'John' },
    { id: 2, name: 'Jane' },
    { id: 3, name: 'Alice' },
  ];

  res.json(users);
});

app.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```

In the above code, we apply the `cacheMiddleware` to the `/api/users` route. This ensures that subsequent requests to fetch user data will be served from the cache if available, rather than hitting the database or API every time.

## Conclusion

Implementing a distributed cache system can significantly improve the performance and scalability of your web application. In this blog post, we learned how to build a distributed cache system using Express.js and Memcached. By leveraging the power of Express.js middleware and the speed of Memcached, you can achieve faster response times and reduce the load on your backend infrastructure.

#ExpressJS #Memcached