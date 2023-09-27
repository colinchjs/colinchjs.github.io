---
layout: post
title: "Building a ticketing system with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [graphql, ticketingsystem]
comments: true
share: true
---

In today's fast-paced digital age, ticketing systems play a crucial role in managing customer support requests and streamlining the ticket resolution process. In this blog post, we will explore how to build a robust ticketing system using JavaScript and GraphQL. Let's dive in!

## What is GraphQL?

GraphQL is an open-source query language for APIs and a runtime for executing those queries with your existing data. It allows clients to request specific data from a server using a single endpoint, reducing the number of API calls and improving performance. With GraphQL, you have more control over the data you retrieve, making it an ideal choice for building ticketing systems.

## Prerequisites

Before we begin, make sure you have the following tools installed:

- Node.js
- Express.js
- MongoDB
- Apollo Server

## Setting Up the Project

First, create a new directory for your project and navigate into it in your terminal. Then, initialize a new Node.js project by running the following command:

```javascript
npm init -y
```

Next, install the required dependencies – `express`, `apollo-server-express`, `mongoose`, and `graphql` – by executing the following command:

```javascript
npm install express apollo-server-express mongoose graphql
```

## Building the Ticket Schema

In the root directory of your project, create a new file called `schema.graphql` and define the ticket schema using GraphQL's schema definition language (SDL):

```graphql
type Ticket {
  id: ID!
  title: String!
  description: String!
  status: String!
  createdAt: String!
}

type Query {
  getTickets: [Ticket!]!
  getTicket(id: ID!): Ticket
}

type Mutation {
  createTicket(title: String!, description: String!): Ticket!
  updateTicket(id: ID!, title: String, description: String, status: String): Ticket!
  deleteTicket(id: ID!): String!
}
```

## Setting Up the Server

In the root directory, create a new file called `server.js`. Import the required modules and set up the Apollo Server:

```javascript
const express = require('express');
const { ApolloServer } = require('apollo-server-express');
const mongoose = require('mongoose');

// Import the ticket schema
const typeDefs = require('./schema.graphql');

// Connect to MongoDB
mongoose.connect('mongodb://localhost/ticketing_system', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('Connected to MongoDB'))
  .catch(err => console.error(err));

// Create the Apollo Server
const server = new ApolloServer({ typeDefs });

const app = express();
server.applyMiddleware({ app });

// Start the server
app.listen(3000, () => console.log('Server started on http://localhost:3000/graphql'));
```

## CRUD Operations

Now, let's implement the CRUD operations for managing tickets. Update the `server.js` file with the following code:

```javascript
// Import the Ticket model
const Ticket = require('./models/Ticket');

const resolvers = {
  Query: {
    getTickets: async () => {
      return Ticket.find();
    },
    getTicket: async (_, { id }) => {
      return Ticket.findById(id);
    },
  },
  Mutation: {
    createTicket: async (_, { title, description }) => {
      const ticket = new Ticket({ title, description, status: 'Open', createdAt: new Date().toISOString() });
      await ticket.save();
      return ticket;
    },
    updateTicket: async (_, { id, title, description, status }) => {
      return Ticket.findByIdAndUpdate(id, { title, description, status }, { new: true });
    },
    deleteTicket: async (_, { id }) => {
      await Ticket.findByIdAndDelete(id);
      return 'Ticket deleted successfully.';
    },
  },
};

server.applyMiddleware({ app });
server.setContext({ Ticket }); // Make the repository available within resolvers
server.setResolverFunctions(resolvers); // Set the resolver functions

app.listen(3000, () => {
  console.log(`Server started on http://localhost:3000/graphql`);
});
```

## Testing the Ticketing System

Now that our ticketing system is set up, fire up your terminal, navigate to the project directory, and start the server by running the following command:

```javascript
node server.js
```

You can now access the GraphQL playground at `http://localhost:3000/graphql` and test the various queries and mutations defined in our schema.

## Conclusion

In this blog post, we've learned how to build a ticketing system using JavaScript and GraphQL. With GraphQL's flexible querying capabilities and powerful server-side ecosystem, we can create efficient and scalable ticketing systems for handling customer support tickets. Happy coding!

**#javascript #graphql #ticketingsystem #webdevelopment**