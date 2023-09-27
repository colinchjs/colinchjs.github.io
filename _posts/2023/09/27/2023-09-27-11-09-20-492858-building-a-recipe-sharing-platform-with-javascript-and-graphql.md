---
layout: post
title: "Building a recipe sharing platform with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [GraphQL, JavaScript]
comments: true
share: true
---

In today's digital age, sharing recipes online has become increasingly popular. Whether you're a food blogger, a home chef, or a food enthusiast, having a platform to share and discover new recipes can be a great way to connect with others who share your passion. In this blog post, we'll explore how to build a recipe sharing platform using JavaScript and GraphQL, two powerful technologies that can help make your platform fast, scalable, and user-friendly.

## What is GraphQL?

Before we dive into the technical details of building our recipe sharing platform, let's briefly understand what GraphQL is. GraphQL is an open-source query language developed by Facebook. It allows clients to request only the specific data they need from a server, reducing the amount of data transferred over the network. With GraphQL, clients have the flexibility to request different sets of data in a single round trip to the server, making it efficient and ideal for building APIs.

## Setting up the Backend

To start building our recipe sharing platform, we need to set up the backend infrastructure. We'll use Node.js and the popular JavaScript framework, Express, to create a GraphQL server. To begin, let's initialize a new Node.js project and install the necessary dependencies:

```shell
mkdir recipe-sharing-platform
cd recipe-sharing-platform
npm init -y
npm install express graphql express-graphql
```

Next, let's create a `index.js` file and set up our Express server along with the GraphQL middleware:

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');

// Build your schema here

const app = express();

app.use('/graphql', graphqlHTTP({
  schema: yourSchema,
  graphiql: true
}));

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

In the code above, we import the necessary modules and use the `buildSchema` function from the `graphql` package to define our GraphQL schema. Next, we create an Express server and use the `graphqlHTTP` middleware to handle GraphQL requests. We specify the schema and enable the GraphiQL tool, which provides an interface for testing our GraphQL API.

## Defining the Recipe Schema

Now let's define the schema for our recipe sharing platform. The schema describes the types and relationships in our application. Open the `index.js` file and add the following code before the server setup:

```javascript
const { buildSchema } = require('graphql');

const schema = buildSchema(`
  type Recipe {
    id: ID!
    title: String!
    description: String!
    ingredients: [String!]!
    instructions: String!
  }

  type Query {
    getRecipe(id: ID!): Recipe
    getAllRecipes: [Recipe!]!
  }

  type Mutation {
    createRecipe(title: String!, description: String!, ingredients: [String!]!, instructions: String!): Recipe!
    deleteRecipe(id: ID!): Recipe
  }
`);
```

In the code above, we define the `Recipe` type with its fields and their types. We also define the `Query` type, which allows us to fetch recipes by ID or get all recipes. In addition, we define the `Mutation` type that enables us to create and delete recipes. Feel free to modify the schema based on your requirements.

## Implementing Resolvers

To make our GraphQL queries and mutations work, we need to provide resolvers, which are functions that define how to fetch or modify the data. Below the schema definition, add the following code:

```javascript
const recipes = [];

const root = {
  getRecipe: ({ id }) => {
    return recipes.find(recipe => recipe.id === id);
  },
  getAllRecipes: () => {
    return recipes;
  },
  createRecipe: ({ title, description, ingredients, instructions }) => {
    const recipe = {
      id: Math.random().toString(),
      title,
      description,
      ingredients,
      instructions
    };

    recipes.push(recipe);
    return recipe;
  },
  deleteRecipe: ({ id }) => {
    const index = recipes.findIndex(recipe => recipe.id === id);

    if (index !== -1) {
      const deletedRecipe = recipes.splice(index, 1);
      return deletedRecipe[0];
    }
    return null;
  },
};

```

In the code above, we define an empty array `recipes` that will act as our in-memory data store. We then create a `root` object with resolver functions for each defined query and mutation. For example, `getRecipe` resolver retrieves a recipe by its ID from the `recipes` array.

## Testing the API

With everything set up, we can now test our recipe sharing platform API using GraphiQL. Start your server by running `node index.js` and open GraphiQL in your browser by visiting `http://localhost:3000/graphql`. You can now execute queries and mutations to interact with your API.

Here's an example query to get a recipe by ID:

```graphql
query {
  getRecipe(id: "recipe1") {
    id
    title
    description
    ingredients
    instructions
  }
}
```

And here's a mutation to create a new recipe:

```graphql
mutation {
  createRecipe(
    title: "Spaghetti Bolognese",
    description: "A classic Italian dish",
    ingredients: ["pasta", "tomatoes", "ground beef", "onions", "garlic"],
    instructions: "1. Cook the pasta ... 2. Dice the onions ... "
  ) {
    id
    title
    description
    ingredients
    instructions
  }
}
```

Congratulations! You have successfully built a recipe sharing platform using JavaScript and GraphQL. This is just the beginning, and you can expand and enhance your platform by adding features like authentication, user comments, and ratings. Happy cooking and coding!

## #GraphQL #JavaScript