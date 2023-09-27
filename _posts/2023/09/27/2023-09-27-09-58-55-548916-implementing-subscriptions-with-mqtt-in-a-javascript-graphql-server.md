---
layout: post
title: "Implementing subscriptions with MQTT in a Javascript GraphQL server"
description: " "
date: 2023-09-27
tags: [MQTT, GraphQL]
comments: true
share: true
---

MQTT (Message Queuing Telemetry Transport) is a lightweight messaging protocol that is commonly used in Internet of Things (IoT) applications. In this blog post, we will explore how to implement subscriptions using MQTT in a JavaScript-based GraphQL server.

## Why use MQTT for subscriptions?

Subscriptions allow real-time data updates in GraphQL servers, making it ideal for scenarios where immediate data is required, such as live chat apps or real-time analytics. MQTT is well-suited for this purpose due to its lightweight nature and publish-subscribe messaging model.

## Setting up the environment

Before we dive into the code, let's ensure that we have the necessary tools and libraries installed:

1. **Node.js**: Ensure that you have Node.js installed on your machine. You can download the latest version from the official Node.js website.

2. **npm**: Node Package Manager (npm) is bundled with Node.js. Check if npm is installed by running `npm -v` in your terminal.

3. **Express**: Express is a popular Node.js framework for building web applications. Install it by running `npm install express` in your project directory.

4. **GraphQL**: GraphQL is a query language for APIs. Install it by running `npm install graphql` in your project directory.

5. **Apollo Server**: Apollo Server is a community-driven, open-source GraphQL server that works with any GraphQL schema. Install it by running `npm install apollo-server-express` in your project directory.

6. **MQTT.js**: MQTT.js is a client library for the MQTT protocol. Install it by running `npm install mqtt` in your project directory.

## Setting up the MQTT client

First, we need to set up an MQTT client to subscribe to MQTT topics and handle incoming messages. Here's an example code snippet to get you started:

```javascript
const mqtt = require('mqtt');
const client = mqtt.connect('mqtt://broker.example.com'); // Replace with your MQTT broker URL

client.on('connect', () => {
  console.log('Connected to MQTT broker');

  client.subscribe('myTopic'); // Replace with your MQTT topic
});

client.on('message', (topic, message) => {
  console.log(`Received message on topic ${topic}: ${message.toString()}`);
});
```

Replace the `mqtt://broker.example.com` with the URL of your MQTT broker, and `myTopic` with the desired MQTT topic to subscribe to. When a message is received, it will be logged to the console.

## Integrating MQTT with a GraphQL server

Next, we need to integrate the MQTT client with a GraphQL server to enable subscriptions. We'll be using Apollo Server to handle GraphQL requests. Here's an example code snippet to set up a basic GraphQL server with subscription support:

```javascript
const express = require('express');
const { ApolloServer, PubSub } = require('apollo-server-express');

const app = express();
const pubsub = new PubSub();
const MESSAGE_CREATED = 'MESSAGE_CREATED'; // Custom event name

const typeDefs = `
  type Message {
    id: ID!
    content: String!
  }
  
  type Query {
    messages: [Message!]!
  }

  type Subscription {
    messageCreated: Message!
  }
`;

const resolvers = {
  Query: {
    messages: () => {
      // Implement your query logic here
    }
  },
  Subscription: {
    messageCreated: {
      subscribe: () => {
        // Implement your MQTT subscription logic here
      }
    }
  }
};

const server = new ApolloServer({ typeDefs, resolvers, context: { pubsub } });

server.applyMiddleware({ app });

const httpServer = require('http').createServer(app);
server.installSubscriptionHandlers(httpServer);

httpServer.listen({ port: 4000 }, () => {
  console.log('GraphQL server with MQTT subscriptions ready at http://localhost:4000/graphql');
});
```

Replace the query and subscription resolvers with your desired logic, and customize the schema to fit your application needs.

## Testing the subscriptions

To test the subscriptions, you can use a GraphQL client like [GraphiQL](https://github.com/graphql/graphiql). Open GraphiQL in your browser and execute the following subscription query:

```graphql
subscription {
  messageCreated {
    id
    content
  }
}
```

Whenever a new message is created, you should see the result in the subscription response.

## Conclusion

In this blog post, we explored how to implement subscriptions using MQTT in a JavaScript-based GraphQL server. By combining the lightweight MQTT protocol with the powerful GraphQL subscriptions, we can create real-time updates for our applications. Give it a try and see how MQTT can enhance your GraphQL server with real-time capabilities!

#MQTT #GraphQL #JavaScript #Subscriptions