---
layout: post
title: "Building a GraphQL API with Express.js and a database like PostgreSQL or MySQL"
description: " "
date: 2023-09-17
tags: [graphql, expressjs]
comments: true
share: true
---

In this tutorial, we will explore how to build a GraphQL API using Express.js, a popular Node.js framework, and connect it to a database like PostgreSQL or MySQL. GraphQL is a powerful query language that enables clients to request and receive only the specific data they need from a server, reducing over-fetching and under-fetching of data.

## Prerequisites

Before we start, make sure you have the following installed:

- Node.js and npm: [Download Node.js](https://nodejs.org/en/download/) and follow the installation instructions.

## Setup

1. Create a new directory for your project and navigate to it using the command line.

2. Generate a new package.json file by running the following command:

```shell
npm init -y
```

3. Install the required dependencies:

```shell
npm install express graphql express-graphql pg mysql
```

## Setting up Express.js

Create a new file called `server.js` and open it in your favorite code editor. Add the following code:

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');

// Define your GraphQL schema
const schema = buildSchema(`
  type Query {
    hello: String
  }
`);

// Implement your API resolvers
const root = {
  hello: () => 'Hello, World!'
};

// Create an Express server
const app = express();

// Define the GraphQL endpoint
app.use('/graphql', graphqlHTTP({
  schema: schema,
  rootValue: root,
  graphiql: true // Enable GraphiQL for testing
}));

// Start the server
app.listen(3000, () => {
  console.log('Server started on http://localhost:3000');
});
```

In the above code, we import the required dependencies and define a simple GraphQL schema and resolver. We then create an Express server and configure the `/graphql` endpoint to handle GraphQL requests. We also enable GraphiQL, a web-based IDE for testing GraphQL APIs.

## Database Setup

### PostgreSQL

If you want to use PostgreSQL as your database, make sure you have PostgreSQL installed and running on your machine. Additionally, install the following npm package:

```shell
npm install pg
```

### MySQL

For MySQL, ensure you have MySQL installed and running on your machine. Then, install the following npm package:

```shell
npm install mysql
```

## Connecting to the Database

To connect to the database, you will need to provide the necessary configuration details such as host, port, username, password, and database name. Follow the respective documentation for PostgreSQL or MySQL to establish the connection.

Once connected, you can modify your GraphQL resolvers to fetch data from the database and respond to the client accordingly.

## Conclusion

Congratulations! You have learned how to build a GraphQL API with Express.js and connect it to a database like PostgreSQL or MySQL. GraphQL provides a modern and efficient way to fetch data from your server, and using a database makes it even more powerful. Take this knowledge and build amazing GraphQL APIs for your applications.

#graphql #expressjs