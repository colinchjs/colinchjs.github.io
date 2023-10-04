---
layout: post
title: "Implementing request logging in a Javascript GraphQL server"
description: " "
date: 2023-09-27
tags: [GraphQL]
comments: true
share: true
---

Request logging is an essential part of monitoring and debugging server activity. It helps us gain insights into the incoming requests and diagnose any potential issues. In this blog post, we will explore how to implement request logging in a JavaScript GraphQL server.

## Prerequisites

Before we dive into implementation details, make sure you have the following prerequisites in place:

- A JavaScript GraphQL server (e.g., Apollo Server, Express GraphQL)
- Basic understanding of JavaScript and GraphQL

## Logging requests using middleware

One way to implement request logging is by using middleware. Middleware allows us to intercept requests and perform additional actions before they reach the main resolver function. Here's an example implementation using Apollo Server:

```javascript
const { ApolloServer } = require('apollo-server');
const { applyMiddleware } = require('graphql-middleware');
const { rule } = require('graphql-shield');

// Create a rule to log every request
const logRule = rule()(async (parent, args, context) => {
  console.log('Request received:', context.operationName);
  return true;
});

// Wrap the resolver with the logging rule
const server = new ApolloServer({
  schema: applyMiddleware(schema, logRule),
});

// Start the server
server.listen().then(({ url }) => {
  console.log(`Server ready at ${url}`);
});
```

In this example, we create a `logRule` that logs every request's `operationName`. We then wrap our schema with `graphql-middleware` and pass the `logRule` as middleware to the Apollo Server.

## Logging requests using middleware with metadata

To enrich our request logs further, we could include additional metadata such as the request timestamp, IP address, and user agent. Here's an example using Express GraphQL:

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { makeExecutableSchema } = require('graphql-tools');

const schema = makeExecutableSchema({ typeDefs, resolvers });

// Create a middleware function to log requests
const requestLogger = (req, res, next) => {
  const timestamp = new Date();
  const ip = req.headers['x-forwarded-for'] || req.connection.remoteAddress;
  const userAgent = req.headers['user-agent'];

  console.log('Request received:');
  console.log(`- Timestamp: ${timestamp}`);
  console.log(`- IP address: ${ip}`);
  console.log(`- User Agent: ${userAgent}`);

  next();
};

// Create an endpoint for GraphQL requests with requestLogger middleware
app.use('/graphql', requestLogger, graphqlHTTP({ schema }));

// Start the server
app.listen(3000, () => {
  console.log('Server listening on port 3000');
});
```

In this example, we define a `requestLogger` middleware function that logs the request details: timestamp, IP address, and user agent. We then attach this middleware to the `/graphql` endpoint using `app.use()` before passing it to `express-graphql`.

## Conclusion

Implementing request logging in a JavaScript GraphQL server is crucial for monitoring and diagnosing server activity. By using middleware, such as `graphql-middleware` or custom Express middleware, we can intercept the incoming requests and log important information. This allows us to gain insights into our server's behavior and troubleshoot any issues effectively.

Remember to ensure that the logs are stored securely and handle them appropriately to comply with privacy regulations. #GraphQL #JavaScript #RequestLogging #Middleware