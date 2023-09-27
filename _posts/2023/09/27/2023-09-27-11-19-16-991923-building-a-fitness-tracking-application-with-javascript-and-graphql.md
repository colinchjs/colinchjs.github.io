---
layout: post
title: "Building a fitness tracking application with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [fitness, graphql]
comments: true
share: true
---

In this tutorial, we will explore how to build a fitness tracking application using Javascript and GraphQL. We will leverage the power of GraphQL to efficiently query and mutate data for our application.

## Getting Started

To begin, let's set up our development environment.

### Prerequisites

Make sure you have the following installed on your machine:

- Node.js
- npm (Node Package Manager)

### Setting Up the Project

1. Create a new directory for your project:
   ```bash
   mkdir fitness-tracking-app
   cd fitness-tracking-app
   ```

2. Initialize the project using npm:
   ```bash
   npm init -y
   ```

3. Install the required dependencies:
   ```bash
   npm install express graphql express-graphql
   ```

4. Create a new file named `app.js` and add the following code:

   ```javascript
   const express = require('express');
   const { graphqlHTTP } = require('express-graphql');
   const { buildSchema } = require('graphql');

   // Define the schema
   const schema = buildSchema(`
       type Query {
           hello: String
       }
   `);

   // Define the resolvers
   const root = {
       hello: () => 'Hello, World!'
   };

   // Create an express app
   const app = express();

   // Configure the GraphQL endpoint
   app.use('/graphql', graphqlHTTP({
       schema: schema,
       rootValue: root,
       graphiql: true
   }));

   // Start the server
   app.listen(3000, () => {
       console.log(`Server running on port 3000`);
   });
   ```

5. Start the server by running the following command:
   ```bash
   node app.js
   ```

6. Open your browser and navigate to `http://localhost:3000/graphql`. You should be able to see the GraphiQL interface.

## Creating the Fitness Tracking Schema

Now that our server is up and running, let's define the schema for our fitness tracking application.

```javascript
const schema = buildSchema(`
    type Exercise {
        id: ID!
        name: String!
        caloriesBurned: Int!
        duration: Int!
    }

    type Query {
        exercises: [Exercise]
        exercise(id: ID!): Exercise
    }

    type Mutation {
        createExercise(name: String!, caloriesBurned: Int!, duration: Int!): Exercise
        updateExercise(id: ID!, name: String, caloriesBurned: Int, duration: Int): Exercise
        deleteExercise(id: ID!): String
    }
`);
```
#fitness #javascript #graphql