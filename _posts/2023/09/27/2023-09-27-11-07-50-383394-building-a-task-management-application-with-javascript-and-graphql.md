---
layout: post
title: "Building a task management application with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [graphql]
comments: true
share: true
---

In today's fast-paced world, staying organized and managing tasks efficiently is crucial. With the power of Javascript and GraphQL, we can create a robust task management application that helps us stay on top of our responsibilities. In this blog post, we will guide you through the step-by-step process of building such an application.

## Prerequisites

- Basic knowledge of Javascript and Node.js
- Understanding of GraphQL concepts

## Setting up the Project

To start building our task management application, we need to set up our project first. Follow these steps:

1. Create a new directory for your project.
2. Initialize a new Node.js project using the command `npm init -y` in your project directory.
3. Install the necessary dependencies by running `npm install express express-graphql graphql` in your terminal.

## Setting up the Server

Next, we need to set up our server with Express and GraphQL. Follow these steps:

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');

// Construct a schema
const schema = buildSchema(`
  type Task {
    id: ID!
    title: String!
    description: String
    completed: Boolean!
  }

  type Query {
    getTask(id: ID!): Task
    getAllTasks: [Task]
  }

  type Mutation {
    createTask(title: String!, description: String): Task
    updateTask(id: ID!, title: String, description: String, completed: Boolean): Task
    deleteTask(id: ID!): Boolean
  }
`);

// Create resolvers
const root = {
  getTask: ({ id }) => {
    // Logic to get task by id
  },
  getAllTasks: () => {
    // Logic to get all tasks
  },
  createTask: ({ title, description }) => {
    // Logic to create a new task
  },
  updateTask: ({ id, title, description, completed }) => {
    // Logic to update an existing task
  },
  deleteTask: ({ id }) => {
    // Logic to delete a task
  },
};

// Create the Express app
const app = express();

// Define the GraphQL endpoint
app.use('/graphql', graphqlHTTP({
  schema: schema,
  rootValue: root,
  graphiql: true,
}));

// Start the server
app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

## Modeling the Data

Now that our server is set up, let's model the data for our task management application. We will use MongoDB as our database, and Mongoose as the Object Data Modeling (ODM) library. Follow these steps:

1. Install the necessary dependencies by running `npm install mongoose` in your terminal.
2. Create a new `models` directory in your project.
3. Inside the `models` directory, create a new file called `task.js`.
4. Define the `Task` schema using Mongoose in the `task.js` file:

```javascript
const mongoose = require('mongoose');

const taskSchema = new mongoose.Schema({
  title: { type: String, required: true },
  description: { type: String },
  completed: { type: Boolean, default: false },
});

module.exports = mongoose.model('Task', taskSchema);
```

5. Connect to MongoDB in your server code:

```javascript
const mongoose = require('mongoose');

mongoose.connect('mongodb://localhost/task_manager', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('Connected to MongoDB'))
  .catch((error) => console.error(error));
```

## Adding CRUD Operations

With our server and data model set up, it's time to implement the CRUD operations for our task management application:

1. Implement the logic to get a task by id, get all tasks, create a task, update a task, and delete a task in the `root` resolvers of our server code. 
2. Use the `Task` model from Mongoose to perform database operations. For example, to create a task:

```javascript
createTask: async ({ title, description }) => {
  const task = new Task({ title, description });
  await task.save();
  return task;
},
```

Remember to handle errors appropriately.

## Testing GraphQL Queries and Mutations

To test our GraphQL queries and mutations, we can use tools such as Apollo Client or Postman. Send queries and mutations to the GraphQL endpoint (`http://localhost:3000/graphql` in our example) and observe the results. Here's an example mutation to create a task:

```graphql
mutation {
  createTask(title: "Complete Blog Post", description: "Write a blog post about building a task management application") {
    id
    title
    description
    completed
  }
}
```

## Conclusion

Congratulations! You have successfully built a task management application using Javascript and GraphQL. This application will help you stay organized and manage your tasks effectively. Feel free to enhance it by adding more features or integrating it with other tools.

#javascript #graphql