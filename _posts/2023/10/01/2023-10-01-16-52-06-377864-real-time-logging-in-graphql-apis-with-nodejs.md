---
layout: post
title: "Real-time logging in GraphQL APIs with Node.js"
description: " "
date: 2023-10-01
tags: [nodejs, graphql]
comments: true
share: true
---

Logging is an essential part of any application, as it allows developers to track and analyze various system activities in real-time. When it comes to GraphQL APIs, logging can help in monitoring and debugging the API operations efficiently. In this blog post, we will explore how to implement real-time logging in GraphQL APIs using Node.js.

## Setting up the project

Before we begin, let's set up our Node.js project. Open your terminal and follow these steps:

1. Create a new directory for your project: `mkdir graphql-logging`
2. Navigate into the project directory: `cd graphql-logging`
3. Initialize a new Node.js project: `npm init -y`

Next, let's install the required dependencies:

```
npm install express graphql express-graphql winston winston-transport
```

## Implementing real-time logging

We will be using the popular logging library `winston` to handle our logging needs. Winston provides various logging transports that can capture logs to different sources. In this example, we will use the `winston-transport` package to stream logs to the console.

Here's how you can implement real-time logging in your GraphQL APIs:

```javascript
const express = require('express');
const { createServer } = require('http');
const { execute, subscribe } = require('graphql');
const { SubscriptionServer } = require('subscriptions-transport-ws');
const { ApolloServer } = require('apollo-server-express');
const winston = require('winston');
require('winston-transport');

const typeDefs = /* GraphQL schema definition */ `
  type Query {
    hello: String
  }
`;

const resolvers = {
  Query: {
    hello: () => 'Hello, World!'
  }
};

// Create a new winston logger instance
const logger = winston.createLogger({
  transports: [
    new winston.transports.Console()
  ]
});

// Create an express app and Apollo server
const app = express();
const server = new ApolloServer({
  typeDefs,
  resolvers,
  context: ({ req }) => ({
    logger
  })
});

// Mount the Apollo server on the /graphql route
server.applyMiddleware({ app });

// Create an HTTP server using the express app
const httpServer = createServer(app);

// Set up the subscription server for real-time logging
SubscriptionServer.create(
  {
    schema: server.schema,
    execute,
    subscribe,
    onConnect: () => ({ logger })
  },
  {
    server: httpServer,
    path: server.graphqlPath
  }
);

// Start the server
httpServer.listen({ port: 4000 }, () => {
  logger.info(`Server started at http://localhost:4000${server.graphqlPath}`);
});
```

In this code snippet, we create a new winston logger instance and set up an HTTP server using express. We then create an Apollo server, passing the `logger` instance as part of the server's context. This allows us to access the logger in our resolvers and other parts of the application.

We then create a subscription server using `SubscriptionServer.create()` from the `subscriptions-transport-ws` package. This server enables real-time logging by capturing subscriptions in the GraphQL API and sending logs to the connected clients.

Finally, we start the HTTP server and log the server's URL and GraphQL path using the logger.

## Conclusion

Implementing real-time logging in GraphQL APIs can greatly enhance the monitoring and debugging capabilities of your application. By using the `winston` logging library and the `subscriptions-transport-ws` package, you can easily capture and stream logs in real-time. This can be invaluable in identifying issues and optimizing the performance of your GraphQL APIs.

#nodejs #graphql #logging