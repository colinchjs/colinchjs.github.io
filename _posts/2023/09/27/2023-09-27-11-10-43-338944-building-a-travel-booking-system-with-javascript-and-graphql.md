---
layout: post
title: "Building a travel booking system with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [graphql]
comments: true
share: true
---

With the increasing popularity of online travel booking, building a robust and efficient travel booking system has become a priority for many businesses in the industry. In this blog post, we will explore how to build a travel booking system using JavaScript and GraphQL, two powerful technologies for developing modern web applications.

## Understanding GraphQL

GraphQL is a query language and runtime for APIs. It was developed by Facebook and has gained substantial adoption in the web development community. Unlike traditional REST APIs, GraphQL allows clients to specify the exact data requirements they need, minimizing the amount of data transferred over the network.

Let's say we want to build a travel booking system that allows users to search for flights based on various parameters such as departure city, destination, and date. With GraphQL, we can define a schema that represents our travel data and expose a set of queries that clients can use to retrieve this data efficiently.

## Setting up the Backend with Node.js

To get started, we will set up a backend server using Node.js. We will use Express.js as our web framework and `express-graphql` middleware to integrate GraphQL into our server. Additionally, we will use a database such as MongoDB or PostgreSQL to store our travel data.

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');

// Define the schema
const schema = buildSchema(`
  type Flight {
    id: ID!
    departureCity: String!
    destination: String!
    date: String!
    price: Float!
  }

  type Query {
    searchFlights(departureCity: String, destination: String, date: String): [Flight!]!
  }
`);

// Define the resolvers
const root = {
  searchFlights: ({ departureCity, destination, date }) => {
    // Perform the actual search and return flight data
  },
};

// Set up the GraphQL server
const app = express();
app.use('/graphql', graphqlHTTP({
  schema,
  rootValue: root,
  graphiql: true,  // Enable the GraphiQL IDE for testing
}));

// Start the server
app.listen(3000, () => {
  console.log('Server started on http://localhost:3000');
});
```

## Implementing the Frontend with React

Once we have our backend server set up, we can now focus on building the frontend of our travel booking system with React. React is a popular JavaScript library for building user interfaces. We will also use Apollo Client, a powerful GraphQL client for handling data fetching and state management.

First, let's install the required dependencies:

```shell
$ npm install react react-dom @apollo/client graphql
```

Next, we can create our main `App` component and implement the flight search functionality:

```javascript
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';
import { useState } from 'react';

const client = new ApolloClient({
  uri: 'http://localhost:3000/graphql',
  cache: new InMemoryCache(),
});

const App = () => {
  const [flights, setFlights] = useState([]);

  const searchFlights = async (departureCity, destination, date) => {
    const query = gql`
      query SearchFlights($departureCity: String, $destination: String, $date: String) {
        searchFlights(departureCity: $departureCity, destination: $destination, date: $date) {
          id
          departureCity
          destination
          date
          price
        }
      }
    `;

    const { data } = await client.query({
      query,
      variables: { departureCity, destination, date },
    });

    setFlights(data.searchFlights);
  };

  return (
    <div>
      {/* Add flight search form and flight list components */}
    </div>
  );
};

export default App;
```

## Conclusion

In this blog post, we explored how to build a travel booking system using JavaScript and GraphQL. We set up a backend server using Node.js and Express.js, defined a GraphQL schema, and implemented the frontend using React and Apollo Client. By leveraging the power of GraphQL, we can develop a performant and flexible travel booking system that meets the needs of our users.

#javascript #graphql