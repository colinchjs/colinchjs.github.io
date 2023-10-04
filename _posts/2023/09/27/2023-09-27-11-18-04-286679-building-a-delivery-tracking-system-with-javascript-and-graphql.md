---
layout: post
title: "Building a delivery tracking system with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [GraphQL]
comments: true
share: true
---

In today's fast-paced world, efficient delivery tracking systems are essential for businesses to ensure smooth logistics operations. JavaScript and GraphQL are powerful technologies that can be used to build a flexible and scalable delivery tracking system. In this tutorial, we will explore how to use these technologies to create a robust delivery tracking system.

## Prerequisites
Before we begin, make sure you have the following installed:
- Node.js
- npm (Node Package Manager)
- Any code editor of your choice

## Setting up the Project
To start, let's set up our project by following these steps:

1. Create a new folder for your project and navigate to it using the command line.
2. Initialize a new Node.js project by running the following command:
```shell
npm init -y
```
3. Install the necessary dependencies by running the following commands:
```shell
npm install express graphql express-graphql
```

## Setting up the Server
Now that our project is set up, let's create the server using Express.js and GraphQL. Follow these steps:

1. Create a new file called `server.js` and open it in your code editor.
2. Import the required dependencies by adding the following lines at the top of your file:
```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');
```
3. Define the GraphQL schema by adding the following code:
```javascript
const schema = buildSchema(`
  type Query {
    deliveries: [Delivery]
  }

  type Delivery {
    id: ID!
    customerName: String
    destination: String
    status: String
  }
`);
```
4. Implement the resolver functions by adding the following code:
```javascript
const root = {
  deliveries: () => {
    // Logic to fetch deliveries from your database or external API
    // Return an array of delivery objects
  },
};
```
5. Create an Express.js app and set up the GraphQL endpoint by adding the following code:
```javascript
const app = express();

app.use(
  '/graphql',
  graphqlHTTP({
    schema: schema,
    rootValue: root,
    graphiql: true,
  })
);

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```
6. Save the file and run the following command in your terminal:
```shell
node server.js
```

## Fetching Deliveries
Now that our server is up and running, let's see how we can fetch deliveries using GraphQL queries. Follow these steps:

1. Open your browser and navigate to [http://localhost:3000/graphql](http://localhost:3000/graphql).
2. Enter the following query into the GraphQL Playground:
```graphql
query {
  deliveries {
    id
    customerName
    destination
    status
  }
}
```
3. Press the "Play" button to execute the query.
4. You should see the list of deliveries returned as a response.

## Conclusion
In this tutorial, we have learned how to set up a delivery tracking system using JavaScript and GraphQL. We have created a server with Express.js and defined a GraphQL schema for deliveries. We have also implemented resolver functions to fetch deliveries from a database or external API. With this foundation, you can now extend the system to include features such as updating delivery status or adding new deliveries.

#JavaScript #GraphQL