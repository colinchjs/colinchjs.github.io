---
layout: post
title: "Integrating GraphQL with Express.js in Javascript"
description: " "
date: 2023-09-27
tags: []
comments: true
share: true
---

GraphQL is a query language and runtime for APIs that enables clients to request and receive only the data they need, making it an efficient and flexible way to retrieve data from servers. In this blog post, we will explore how to integrate GraphQL with Express.js, a popular web application framework for Node.js.

## Prerequisites

To follow along with this tutorial, you should have the following installed:

- Node.js
- Express.js
- GraphQL

## Setting up the project

1. Create a new directory for your project and navigate into it:

```
$ mkdir graphql-express-example
$ cd graphql-express-example
```

2. Initialize a new Node.js project:

```
$ npm init -y
```

3. Install the necessary dependencies:

```
$ npm install express express-graphql graphql
```

## Creating an Express.js server

Now, let's create the server file, `server.js`, to set up an Express.js server:

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { GraphQLSchema, GraphQLObjectType, GraphQLString } = require('graphql');

const app = express();

app.use('/graphql', graphqlHTTP({
  schema: new GraphQLSchema({
    query: new GraphQLObjectType({
      name: 'HelloWorld',
      fields: {
        message: {
          type: GraphQLString,
          resolve: () => 'Hello, GraphQL!'
        }
      }
    })
  }),
  graphiql: true
}));

app.listen(3000, () => {
  console.log('Server running at http://localhost:3000/graphql');
});
```

In the code above, we import the required modules and create an Express.js app. We then define a GraphQL schema with a single query field, `message`, which returns the string 'Hello, GraphQL!'. We set up the `/graphql` endpoint to handle GraphQL requests using `express-graphql` middleware. The `graphiql: true` option allows us to use the GraphiQL IDE for testing our API. Finally, we start the server and listen on port 3000.

## Testing our GraphQL API

To test our GraphQL API, open your browser and navigate to `http://localhost:3000/graphql`. You should see the GraphiQL IDE, which allows you to interact with the API.

In the left panel, you can enter your GraphQL query:

```graphql
query {
  message
}
```

Click the "Play" button or press `Ctrl + Enter` to execute the query. You should receive the following response:

```json
{
  "data": {
    "message": "Hello, GraphQL!"
  }
}
```

Congratulations! You have successfully integrated GraphQL with Express.js.

## Conclusion

In this tutorial, we learned how to integrate GraphQL with Express.js. With GraphQL, we can define a schema and retrieve data efficiently using queries. Express.js provides a robust framework for building web applications, and combining it with GraphQL allows us to create powerful APIs.