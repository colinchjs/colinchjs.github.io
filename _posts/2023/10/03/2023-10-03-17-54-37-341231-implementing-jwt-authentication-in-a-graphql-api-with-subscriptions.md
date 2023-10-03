---
layout: post
title: "Implementing JWT authentication in a GraphQL API with subscriptions"
description: " "
date: 2023-10-03
tags: [GraphQL, JWTAuthentication]
comments: true
share: true
---

In this tutorial, we will walk through the process of implementing JWT (JSON Web Tokens) authentication in a GraphQL API that also supports subscriptions. JWT authentication is a secure and widely adopted method for verifying the authenticity of requests in web applications.

## What are JSON Web Tokens?

JSON Web Tokens (JWT) are an open standard (RFC 7519) used for securely transmitting information between parties as a JSON object. A JWT consists of three parts: a header, a payload, and a signature. 

The header contains information about the type of token and the hashing algorithm used. The payload contains the claims or information about the user. The signature is created using the base64-encoded header, payload, and a secret key. When a token is received, the server can verify its authenticity by checking the signature.

## Prerequisites

Before we begin, make sure you have the following:

- [Node.js](https://nodejs.org) installed on your system
- Basic knowledge of GraphQL and its concepts

## Step 1: Setting up the GraphQL Server

To get started, let's create a new Node.js project and install the required dependencies.

1. Create a new directory for your project and navigate into it.

2. Initialize a new Node.js project using the following command:

```bash
npm init -y
```

3. Install the required dependencies: `graphql`, `express`, `jsonwebtoken`, `graphql-subscriptions`, `subscriptions-transport-ws`, and `apollo-server` using the command:

```bash
npm install graphql express jsonwebtoken graphql-subscriptions subscriptions-transport-ws apollo-server
```

4. Create a new file called `server.js` and open it in your favorite code editor.

5. Import the required modules and create an instance of `ApolloServer` as shown below:

```javascript
const { ApolloServer, PubSub } = require('apollo-server');
const express = require('express');
const jwt = require('jsonwebtoken');
const { createServer } = require('http');
const { execute, subscribe } = require('graphql');
const { SubscriptionServer } = require('subscriptions-transport-ws');

const typeDefs = `
  type Query {
    hello: String
  }

  type Mutation {
    login(username: String!, password: String!): String
  }

  type Subscription {
    messageAdded: String
  }
`;

const resolvers = {
  Query: {
    hello: () => 'Hello, world!'
  },
  Mutation: {
    login: (parent, { username, password }) => {
      // Perform authentication logic and generate JWT
      const token = jwt.sign({ username }, 'secret-key', { expiresIn: '1h' });
      
      return token;
    }
  },
  Subscription: {
    messageAdded: {
      subscribe: () => pubsub.asyncIterator('MESSAGE_ADDED')
    }
  }
};

const pubsub = new PubSub();

const server = new ApolloServer({
  typeDefs,
  resolvers,
  context: ({ req }) => {
    // Extract and verify JWT token from the request headers
    const token = req.headers.authorization || '';
    
    if (token) {
      try {
        const decoded = jwt.verify(token, 'secret-key');
        return { user: decoded.username };
      } catch (error) {
        // Handle token verification error
        throw new ApolloError('Invalid token');
      }
    }
    
    return null;
  },
});

const app = express();
server.applyMiddleware({ app });

const httpServer = createServer(app);

httpServer.listen({ port: 4000 }, () => {
  console.log(`Server ready at http://localhost:4000${server.graphqlPath}`);
  new SubscriptionServer({
    execute,
    subscribe,
    schema: server.schema,
    onConnect: () => ({ pubsub })
  }, {
    server: httpServer,
    path: server.graphqlPath
  });
});
```

In the above code, we have defined a basic GraphQL schema with a `Query`, `Mutation`, and `Subscription` type. The `login` mutation is responsible for generating a JWT token, which is then returned as a string. The `context` option in `ApolloServer` is used to extract and verify the JWT token from the request headers.

## Step 2: Testing JWT Authentication and Subscriptions

Now that we have set up our GraphQL server with JWT authentication and subscriptions, let's test it using GraphQL Playground or any other GraphQL client tool. 

1. Start the server by running the following command in the project directory:

```bash
node server.js
```

2. Open the GraphQL Playground by navigating to `http://localhost:4000/graphql` in your browser.

3. Send a `login` mutation request with valid credentials as shown below:

```graphql
mutation {
  login(username: "myusername", password: "mypassword")
}
```

The server will respond with a JWT token.

4. Copy the generated token and add it as an `Authorization` header in the format `Bearer <token>`.

5. Subscribe to the `messageAdded` subscription as shown below:

```graphql
subscription {
  messageAdded
}
```

You should be able to receive real-time updates whenever a new message is added.

Congratulations! You have successfully implemented JWT authentication in your GraphQL API with subscriptions. 

### #GraphQL #JWTAuthentication