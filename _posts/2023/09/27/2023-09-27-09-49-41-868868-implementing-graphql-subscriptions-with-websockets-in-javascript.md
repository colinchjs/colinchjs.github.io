---
layout: post
title: "Implementing GraphQL subscriptions with WebSockets in Javascript"
description: " "
date: 2023-09-27
tags: [GraphQL, Subscriptions]
comments: true
share: true
---

GraphQL is a powerful query language that allows you to efficiently fetch and manipulate data from a server. However, one of its limitations is that it only supports request-response communication. This means that you have to make a separate request each time you want to get real-time updates.

To overcome this limitation, you can use GraphQL subscriptions along with WebSockets to enable real-time updates from the server. This allows you to subscribe to certain events or data changes and receive updates instantly without the need to make additional requests.

In this blog post, we will walk through the process of implementing GraphQL subscriptions with WebSockets in JavaScript.

## Prerequisites

Before we begin, make sure you have the following prerequisites in place:

1. Basic knowledge of GraphQL and JavaScript.
2. A GraphQL server that supports subscriptions (such as Apollo Server).
3. A WebSocket server (such as Socket.IO or GraphQL subscriptions transport).

## Setting up the WebSocket Server

First, we need to set up the WebSocket server to handle the subscription functionality. You can choose a WebSocket library of your choice, such as Socket.IO or GraphQL subscriptions transport.

Here's an example using Socket.IO:

1. Install the Socket.IO library:

```javascript
npm install socket.io
```

2. Initialize the WebSocket server:

```javascript
const http = require('http');
const socketIo = require('socket.io');

const server = http.createServer();
const io = socketIo(server);

io.on('connection', (socket) => {
  console.log('A client connected.');

  // Handle subscription logic here
  
  socket.on('disconnect', () => {
    console.log('A client disconnected.');
  });
});

server.listen(3000, () => {
  console.log('WebSocket server is running on port 3000.');
});
```

## Implementing Subscriptions on the GraphQL Server

Next, we need to implement the subscriptions on the GraphQL server. If you are using Apollo Server, you can easily integrate with the WebSocket server.

1. Install the required packages:

```javascript
npm install apollo-server apollo-server-express subscriptions-transport-ws
```

2. Configure the Apollo Server with WebSocket support:

```javascript
const express = require('express');
const { ApolloServer } = require('apollo-server-express');
const { execute, subscribe } = require('graphql');
const { createServer } = require('http');
const { SubscriptionServer } = require('subscriptions-transport-ws');

const typeDefs = `
  type Subscription {
    newPost: Post
  }

  type Post {
    id: ID!
    title: String!
    content: String!
  }

  type Query {
    posts: [Post]
  }
`;

const resolvers = {
  Subscription: {
    newPost: {
      subscribe: () => pubsub.asyncIterator(['NEW_POST']),
    },
  },
  Query: {
    posts: () => {
      // Fetch posts from the database or any other data source
    },
  },
};

const server = new ApolloServer({
  typeDefs,
  resolvers,
  subscriptions: {
    onConnect: (connectionParams, webSocket) => {
      console.log('WebSocket client connected.');
    },
    onDisconnect: (webSocket, context) => {
      console.log('WebSocket client disconnected.');
    },
  },
});

const app = express();
server.applyMiddleware({ app });

const httpServer = createServer(app);
httpServer.listen({ port: 4000 }, () => {
  console.log(`🚀  Server ready at http://localhost:4000${server.graphqlPath}`);
  
  new SubscriptionServer(
    {
      execute,
      subscribe,
      schema: server.schema,
    },
    {
      server: httpServer,
      path: server.graphqlPath,
    }
  );
});
```

## Subscribing to GraphQL Subscriptions

Once you have set up the WebSocket server and implemented the subscriptions on the GraphQL server, you can now subscribe to the GraphQL subscriptions from the client-side.

1. Install the required package:

```javascript
npm install apollo-client apollo-link-ws subscriptions-transport-ws
```

2. Configure the Apollo Client with WebSocket support:

```javascript
import ApolloClient from 'apollo-client';
import { split } from 'apollo-link';
import { HttpLink } from 'apollo-link-http';
import { WebSocketLink } from 'apollo-link-ws';
import { getMainDefinition } from 'apollo-utilities';
import { InMemoryCache } from 'apollo-cache-inmemory';

const httpLink = new HttpLink({
  uri: 'http://localhost:4000/graphql',
});

const wsLink = new WebSocketLink({
  uri: 'ws://localhost:3000',
  options: {
    reconnect: true,
  },
});

const link = split(
  ({ query }) => {
    const definition = getMainDefinition(query);
    return (
      definition.kind === 'OperationDefinition' &&
      definition.operation === 'subscription'
    );
  },
  wsLink,
  httpLink,
);

const client = new ApolloClient({
  link,
  cache: new InMemoryCache(),
});

// Subscribe to a GraphQL subscription
client.subscribe({
  query: gql`
    subscription {
      newPost {
        id
        title
        content
      }
    }
  `,
}).subscribe({
  next: (data) => {
    console.log('Received new post:', data);
  },
  error: (error) => {
    console.error('Subscription error:', error);
  },
});

```

## Conclusion

In this blog post, we have learned how to implement GraphQL subscriptions with WebSockets in JavaScript. By combining the power of GraphQL subscriptions and WebSockets, you can achieve real-time updates from the server without the need for additional requests. This can greatly enhance the user experience of your applications.

Implementing real-time functionality in GraphQL opens up a wide range of possibilities for building interactive and dynamic applications. Whether you are building a chat application, a live feed, or a collaborative editing tool, GraphQL subscriptions with WebSockets provide a reliable and efficient solution.

Give it a try and see how it can revolutionize your application's real-time capabilities!

#GraphQL #Subscriptions