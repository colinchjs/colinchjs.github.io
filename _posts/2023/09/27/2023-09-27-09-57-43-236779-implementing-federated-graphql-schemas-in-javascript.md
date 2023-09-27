---
layout: post
title: "Implementing federated GraphQL schemas in Javascript"
description: " "
date: 2023-09-27
tags: [GraphQL, Federation]
comments: true
share: true
---

GraphQL has gained popularity in recent years due to its ability to provide a flexible and efficient way to query and manipulate data. **Federation** is an extension to GraphQL that allows you to build distributed schemas by breaking them down into smaller, independent microservices.

In this blog post, we'll explore how to implement federated GraphQL schemas in Javascript using popular libraries like Apollo Server and Apollo Gateway.

## What is Federation?

**GraphQL Federation** is an approach to building scalable and modular GraphQL schemas. It allows you to split your schema across multiple services, where each service manages a specific domain or data model. The federated schemas can then be stitched together to create a unified GraphQL API.

This approach offers several benefits, such as improved code organization, independent development and deployment of services, and reducing the complexity of a monolithic schema.

## Implementing Federated GraphQL Schemas

To implement federated GraphQL schemas in Javascript, we need the following components:

1. **Apollo Server**: Apollo Server is a community-driven, open-source GraphQL server that allows you to build GraphQL APIs easily. It supports federation out of the box and provides tools to combine multiple schemas.

2. **Apollo Gateway**: Apollo Gateway is a component that acts as a single entry point for your federated schemas. It handles the schema stitching and federated queries across your microservices.

Here are the high-level steps to implement federated GraphQL schemas:

1. **Create independent GraphQL services**: Split your schema into smaller, independent services based on your domain or data models. Each service should contain its own GraphQL schema definition, resolvers, and data sources.

2. **Expose your services as Apollo Server instances**: Start each service as an Apollo Server instance, providing the necessary schema definition, resolvers, and data sources. Make sure to include the `@key` directive in your type definitions to define the federation key.

3. **Configure Apollo Gateway**: Set up an Apollo Gateway instance that acts as the entry point for your federated schemas. Configure it with the URLs of your independent services.

4. **Start Apollo Gateway**: Start the Apollo Gateway server, which will handle federated queries and combine the schemas from your independent services.

Example code for implementing federated schemas using Apollo Server and Apollo Gateway:

**Service 1 - User Service**

```javascript
const { ApolloServer, gql } = require('apollo-server');

const typeDefs = gql`
  type User @key(fields: "id") {
    id: ID!
    name: String!
  }

  type Query {
    user(id: ID!): User
  }
`;

const resolvers = {
  Query: {
    user: (id) => {
      // Logic to fetch user data using a data source
    }
  }
};

const server = new ApolloServer({ typeDefs, resolvers });

server.listen().then(({ url }) => {
  console.log(`User service running at ${url}`);
});
```

**Service 2 - Product Service**

```javascript
const { ApolloServer, gql } = require('apollo-server');

const typeDefs = gql`
  type Product @key(fields: "id") {
    id: ID!
    name: String!
    price: Float!
  }

  type Query {
    product(id: ID!): Product
  }
`;

const resolvers = {
  Query: {
    product: (id) => {
      // Logic to fetch product data using a data source
    }
  }
};

const server = new ApolloServer({ typeDefs, resolvers });

server.listen().then(({ url }) => {
  console.log(`Product service running at ${url}`);
});
```

**Apollo Gateway**

```javascript
const { ApolloGateway } = require('@apollo/gateway');

const gateway = new ApolloGateway({
  serviceList: [
    { name: 'users', url: 'http://localhost:4001' },
    { name: 'products', url: 'http://localhost:4002' }
  ]
});

gateway.listen().then(({ url }) => {
  console.log(`Apollo Gateway running at ${url}`);
});
```

With this setup, you can start the individual services and the Apollo Gateway, which will combine the schemas and handle federated queries.

## Conclusion

Implementing federated GraphQL schemas in Javascript using Apollo Server and Apollo Gateway allows you to build distributed and scalable GraphQL APIs. By splitting your schema into smaller services, you can achieve better code organization, independent deployment, and reduced complexity.

**#GraphQL #Federation #Javascript**