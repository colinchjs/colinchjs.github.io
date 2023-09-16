---
layout: post
title: "Building a GraphQL API gateway with Express.js and Apollo Server Federation"
description: " "
date: 2023-09-17
tags: [graphql, expressjs]
comments: true
share: true
---

In today's modern web architecture, it is common to have multiple microservices that are responsible for different functionalities of a web application. When these microservices expose their own GraphQL APIs, it can become complex for the client application to manage and query these individual APIs.

To solve this problem, we can build a **GraphQL API gateway** that acts as a single entry point for all the microservices. In this tutorial, we'll explore how to build a GraphQL API gateway using **Express.js** and **Apollo Server Federation**.

## What is Apollo Server Federation?

**Apollo Server Federation** is a way to compose a federated graph by combining multiple GraphQL microservices into a single schema. It allows you to create a unified, federated graph by stitching together the schemas of individual microservices. Apollo Federation simplifies the process of building a GraphQL API gateway by providing a well-defined way to compose and query multiple GraphQL APIs.

## Prerequisites

Before we begin, make sure you have the following installed:

- Node.js (>=12.x)
- npm or yarn

## Setting Up the Gateway Server

1. Start by creating a new directory for your project:

```bash
mkdir api-gateway
cd api-gateway
```

2. Initialize a new Node.js project:

```bash
npm init -y
```

3. Install the necessary dependencies:

```bash
npm install express apollo-server apollo-server-express graphql graphql-tools
```

4. Create a new file `index.js` and add the following code to set up the Express server and Apollo Server:

```javascript
const express = require('express');
const { ApolloServer } = require('apollo-server-express');
const { buildFederatedSchema } = require('@apollo/federation');

const typeDefs = `
    type Query {
        hello: String
    }
`;

const resolvers = {
    Query: {
        hello: () => 'Hello from GraphQL API Gateway!',
    },
};

const server = new ApolloServer({
    schema: buildFederatedSchema([{ typeDefs, resolvers }]),
});

const app = express();
server.applyMiddleware({ app });

app.listen({ port: 4000 }, () =>
    console.log(`Gateway server ready at http://localhost:4000${server.graphqlPath}`)
);
```

This code sets up an Express server and configures Apollo Server with a basic `Query` type for demonstration purposes.

5. Finally, start the gateway server by running:

```bash
node index.js
```

You should see a message indicating that the gateway server is running at [http://localhost:4000/graphql](http://localhost:4000/graphql).

## Adding Federation to Individual Services

To complete our GraphQL API gateway setup, we also need to modify the individual GraphQL microservices to include federation directives.

1. Modify the existing microservice schema to include the `@key` directive. For example:

```graphql
type Product @key(fields: "id") {
    id: ID!
    name: String!
    description: String!
    price: Float!
}
```

2. Import the `buildFederatedSchema` function from `@apollo/federation` and use it to create a federated schema:

```javascript
const { buildFederatedSchema } = require('@apollo/federation');

// ... existing schema and resolvers

const schema = buildFederatedSchema([{ typeDefs, resolvers }]);
```

3. In the `ApolloServer` configuration, set the `schema` property with the federated schema:

```javascript
const server = new ApolloServer({
    schema,
});
```

4. Start the individual microservice as usual.

## Querying the Federated Graph

With the GraphQL API gateway and federated microservices set up, the client can now query the federated graph using a single GraphQL endpoint.

```graphql
query {
    hello
    product(id: "123") {
        id
        name
        price
    }
}
```

In the above example, the `hello` query is executed by the gateway server, while the `product` query is resolved by the corresponding microservice. The gateway is responsible for stitching together the results from multiple services to create a single response.

## Conclusion

Building a GraphQL API gateway using Express.js and Apollo Server Federation allows you to simplify the management and querying of multiple microservices. With federation, you can compose a federated graph from multiple microservices and expose a single GraphQL endpoint to the client. By following the steps outlined in this tutorial, you can set up your own GraphQL API gateway and start harnessing the power of federation in your microservices architecture.

#graphql #expressjs