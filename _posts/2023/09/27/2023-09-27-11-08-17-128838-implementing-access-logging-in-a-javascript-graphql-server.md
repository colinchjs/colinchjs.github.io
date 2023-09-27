---
layout: post
title: "Implementing access logging in a Javascript GraphQL server"
description: " "
date: 2023-09-27
tags: [graphql, logging]
comments: true
share: true
---

## Setting up the Server

Before we dive into access logging, let's quickly set up a basic GraphQL server using Express and Apollo Server. Here's an example of how you can set up a simple GraphQL server:

```javascript
const express = require('express');
const { ApolloServer, gql } = require('apollo-server-express');

const app = express();

const typeDefs = gql`
  type Query {
    hello: String
  }
`;

const resolvers = {
  Query: {
    hello: () => 'Hello, world!',
  },
};

const server = new ApolloServer({ typeDefs, resolvers });

server.applyMiddleware({ app });

app.listen({ port: 4000 }, () =>
  console.log(`Server ready at http://localhost:4000${server.graphqlPath}`)
);
```

Now that we have our server set up, let's move on to implementing access logging.

## Implementing Access Logging

To implement access logging, we can leverage the power of middleware in Express. Middleware allows us to intercept requests and perform additional actions, such as logging, before passing them to the actual resolver functions.

Here's an example of how you can implement access logging middleware in your GraphQL server:

```javascript
// Access Logging Middleware
app.use((req, res, next) => {
  console.log(`[${new Date().toISOString()}] Access Log - ${req.method}: ${req.originalUrl}`);
  next();
});

const server = new ApolloServer({ typeDefs, resolvers });

server.applyMiddleware({ app });
```

In the above code snippet, we define a custom middleware function that logs the request method and URL whenever a request is received. We then call `next()` to continue the request lifecycle.

By placing this middleware before `ApolloServer`, we ensure that the logging occurs before the requests are processed by the GraphQL server.

## Enhancing Access Logs

You can further enhance your access logs by including additional information, such as client IP address, request headers, or even response status codes. This can be useful for debugging and monitoring purposes.

Here's an enhanced version of the access logging middleware that includes the client IP address and request headers:

```javascript
app.use((req, res, next) => {
  const clientIP = req.headers['x-forwarded-for'] || req.connection.remoteAddress;
  console.log(`[${new Date().toISOString()}] Access Log - ${clientIP} - ${req.method}: ${req.originalUrl}`);
  next();
});
```

In the above code, we use the `x-forwarded-for` header to get the client IP address, which works when your Express app is behind a reverse proxy like Nginx. Alternatively, we obtain the IP address from the `req.connection.remoteAddress` property.

## Conclusion

Implementing access logging in a JavaScript GraphQL server can provide valuable insights and help monitor the incoming requests. By using middleware in Express, we can easily add access logging to our server. You can enhance logging further by including additional information like client IP address and request headers.

Implementing access logging is crucial for server monitoring, ensuring security, and debugging. By keeping track of incoming requests, you can identify potential issues, analyze traffic patterns, and optimize your GraphQL server's performance.

#graphql #logging