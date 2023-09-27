---
layout: post
title: "Implementing federation with Apollo Gateway in Javascript"
description: " "
date: 2023-09-27
tags: [hashtags, ApolloGateway]
comments: true
share: true
---

In a microservices architecture, the concept of **federation** allows multiple GraphQL services to be combined into a single federated graph. **Apollo Gateway** is a popular solution for implementing federation in JavaScript applications using Apollo Server.

Let's walk through the steps to implement federation with Apollo Gateway.

## Step 1: Set Up the Gateway Server

First, create a new JavaScript project and install the necessary packages:

```javascript
npm init -y
npm install apollo-server apollo-gateway
```

Create a file named `gateway.js` and set up the Apollo Gateway server:

```javascript
const { ApolloGateway } = require("@apollo/gateway");

const gateway = new ApolloGateway({
  serviceList: [
    { name: "accounts", url: "http://localhost:4001/graphql" },
    { name: "products", url: "http://localhost:4002/graphql" },
    // Add more services as needed
  ],
});

// Start the server
gateway.listen().then(({ url }) => {
  console.log(`Gateway server ready at ${url}`);
});
```

Replace the `url` values with the URLs of your individual GraphQL services.

## Step 2: Create Individual GraphQL Services

Create separate GraphQL services for each microservice. For example, create an `accounts` service in a file named `accounts.js`:

```javascript
const { ApolloServer, gql } = require("apollo-server");

const typeDefs = gql`
  type User {
    id: ID!
    name: String!
    email: String!
  }

  type Query {
    user(id: ID!): User
  }
`;

const resolvers = {
  Query: {
    user: (parent, { id }, context) => {
      // Logic to fetch user from database or API
    },
  },
};

const server = new ApolloServer({ typeDefs, resolvers });

server.listen(4001).then(({ url }) => {
  console.log(`Accounts service ready at ${url}`);
});
```

Similarly, create a `products` service in a file named `products.js` with relevant type definitions, resolvers, and listen on a different port.

## Step 3: Start the Services and Gateway

Open separate terminals for each service and the gateway.

1. Terminal 1: Start the accounts service with `node accounts.js`.
2. Terminal 2: Start the products service with `node products.js`.
3. Terminal 3: Start the gateway with `node gateway.js`.

## Step 4: Verify the Federated Graph

Open a browser and navigate to `http://localhost:PORT/graphql` (replace `PORT` with the port number specified in the `gateway.js` file).

Execute queries against the federated graph, combining data from different services:

```graphql
query {
  user(id: "1") {
    id
    name
    email
  }
}
```

You should see the combined results from the accounts and products services.

Congratulations! You have successfully implemented federation with Apollo Gateway in JavaScript.

#hashtags: #ApolloGateway #Federation