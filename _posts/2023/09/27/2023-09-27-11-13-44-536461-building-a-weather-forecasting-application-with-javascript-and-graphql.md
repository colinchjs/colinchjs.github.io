---
layout: post
title: "Building a weather forecasting application with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [graphql]
comments: true
share: true
---

In this blog post, we will explore how to build a weather forecasting application using JavaScript and GraphQL. With the rise of GraphQL as a modern API technology, it has become easier to fetch and manage data from various sources. Combining this with JavaScript, we can create a highly interactive and real-time weather application.

## Setting up the Project

To begin, let's set up a new project directory and initialize it with npm:

```shell
mkdir weather-app
cd weather-app
npm init -y
```

Next, we need to install some packages to get started:

```shell
npm install express express-graphql graphql axios
```

We will be using **Express** as our server, **express-graphql** to integrate GraphQL with our Express server, **graphql** for defining our schema, and **axios** to make HTTP requests to external APIs.

## Creating the Server

Let's start by creating an `index.js` file and setting up our Express server:

```javascript
const express = require('express');
const {graphqlHTTP} = require('express-graphql');
const {buildSchema} = require('graphql');

const app = express();

// Define the GraphQL schema
const schema = buildSchema(`
  type Query {
    getWeather(city: String!): Weather
  }

  type Weather {
    city: String
    temperature: Float
    description: String
    humidity: Int
    windSpeed: Float
  }
`);

// Define the resolver
const root = {
  getWeather: async ({city}) => {
    // Fetch weather data from external API
    const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=YOUR_API_KEY`;
    const response = await axios.get(url);
    const {main, weather, wind} = response.data;

    // Format and return the weather data
    return {
      city: city,
      temperature: main.temp,
      description: weather[0].description,
      humidity: main.humidity,
      windSpeed: wind.speed
    };
  }
};

// Setup the GraphQL endpoint
app.use('/graphql', graphqlHTTP({
  schema: schema,
  rootValue: root,
  graphiql: true
}));

// Start the server
app.listen(3000, () => {
  console.log('Server running on http://localhost:3000');
});
```

## Testing the Application

You can now start the server by running `node index.js`. The server will be running on `http://localhost:3000`. We have defined a single GraphQL query named `getWeather` which takes a `city` argument and returns the weather information for that city.

To test the application, you can open your browser and navigate to `http://localhost:3000/graphql` to access the GraphiQL interface. You can use this interface to test the `getWeather` query by passing in a city as an argument.

## Conclusion

In this tutorial, we have seen how to build a weather forecasting application using JavaScript and GraphQL. We set up an Express server, defined a GraphQL schema, and made requests to an external API to fetch real-time weather data. This application can be extended by adding more queries or integrating with other APIs to provide additional weather information or functionalities.

#javascript #graphql