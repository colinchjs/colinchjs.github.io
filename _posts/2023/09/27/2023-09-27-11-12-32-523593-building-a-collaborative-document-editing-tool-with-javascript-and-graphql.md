---
layout: post
title: "Building a collaborative document editing tool with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [graphql]
comments: true
share: true
---

In today's digital age, collaboration is a key aspect of many projects. Whether it is brainstorming ideas or working on a report, having a tool that allows multiple users to edit and collaborate in real-time is highly valuable. In this blog post, we will explore how to build a collaborative document editing tool using Javascript and GraphQL.

## What is GraphQL?

GraphQL is an open-source query language for APIs and a runtime for executing those queries with your existing data. It provides a more efficient and flexible approach to client-server communication by allowing clients to request specific data and shape the response according to their needs.

## Setting up the project

To get started, we need to set up the project. We will use [Node.js](https://nodejs.org) as our runtime environment and a few libraries to build our collaborative document editing tool. Here are the steps to follow:

1. Install Node.js if you don't have it already.
2. Create a new directory for your project.
3. Open a terminal and navigate to the project directory.
4. Run the following command to initialize a new Node.js project:
```bash
npm init -y
```
5. Install the required dependencies:
```bash
npm install express express-graphql graphql subscriptions-transport-ws
```
6. Create a new file `index.js` for our server implementation.

## Setting up the server

Our collaborative document editing tool will require a server to handle real-time updates and communicate with clients. We will be using the Express.js framework along with the express-graphql middleware for handling GraphQL requests. Open the `index.js` file and add the following code:

```javascript
const express = require('express');
const { ApolloServer, gql, PubSub } = require('apollo-server-express');

const app = express();
const pubsub = new PubSub();

const typeDefs = gql`
  type Document {
    id: ID!
    content: String!
  }
  
  type Query {
    getDocument(id: ID!): Document
  }
  
  type Mutation {
    updateDocument(id: ID!, content: String!): Document
  }
  
  type Subscription {
    documentUpdated(id: ID!): Document
  }
`;

const documents = {};

const resolvers = {
  Query: {
    getDocument: (parent, args) => {
      return documents[args.id];
    },
  },
  Mutation: {
    updateDocument: (parent, args) => {
      documents[args.id] = {
        id: args.id,
        content: args.content,
      };

      pubsub.publish('DOCUMENT_UPDATED', { documentUpdated: documents[args.id] });

      return documents[args.id];
    },
  },
  Subscription: {
    documentUpdated: {
      subscribe: (parent, { id }, { pubsub }) => {
        return pubsub.asyncIterator('DOCUMENT_UPDATED');
      },
    },
  },
};

const server = new ApolloServer({
  typeDefs,
  resolvers,
  context: { pubsub }
});

server.applyMiddleware({ app });

app.listen({ port: 4000 }, () =>
  console.log(`Server ready at http://localhost:4000${server.graphqlPath}`)
);
```

In the code above, we define our GraphQL schema using the `gql` tag and set up our resolvers for handling queries, mutations, and subscriptions. We also create an instance of the ApolloServer and connect it to our Express.js app.

## Client-side implementation

Now that we have our server set up, let's move on to the client-side implementation. We will utilize React.js for building our UI components and Apollo Client to interact with the GraphQL server. Here are the steps to follow:

1. Create a new directory called `client` within your project folder.
2. Navigate to the `client` directory and run the following command to create a new React app:
```bash
npx create-react-app .
```
3. Install the required dependencies:
```bash
npm install @apollo/client graphql
```
4. Open the `src/App.js` file and replace its content with the following code:

```jsx
import React, { useEffect, useState } from 'react';
import { ApolloClient, InMemoryCache, ApolloProvider, useSubscription, gql, useMutation } from '@apollo/client';

const client = new ApolloClient({
  uri: 'http://localhost:4000/graphql',
  cache: new InMemoryCache(),
});

const DOCUMENT_UPDATED = gql`
  subscription DocumentUpdated($id: ID!) {
    documentUpdated(id: $id) {
      id
      content
    }
  }
`;

const UPDATE_DOCUMENT = gql`
  mutation UpdateDocument($id: ID!, $content: String!) {
    updateDocument(id: $id, content: $content) {
      id
      content
    }
  }
`;

const DocumentEditor = ({ id }) => {
  const [content, setContent] = useState('');

  const { data } = useSubscription(DOCUMENT_UPDATED, {
    variables: { id },
  });

  const [updateDocument] = useMutation(UPDATE_DOCUMENT);

  useEffect(() => {
    if (data && data.documentUpdated.content !== content) {
      setContent(data.documentUpdated.content);
    }
  }, [data, content]);

  const handleChange = (event) => {
    const newContent = event.target.value;
    setContent(newContent);
    updateDocument({ variables: { id, content: newContent } });
  };

  return (
    <textarea value={content} onChange={handleChange} />
  );
};

const App = () => {
  return (
    <ApolloProvider client={client}>
      <div className="App">
        <h1>Collaborative Document Editing Tool</h1>
        <DocumentEditor id="1" />
      </div>
    </ApolloProvider>
  );
};

export default App;
```

In the code above, we import the necessary components and hooks from the Apollo Client library. We define two GraphQL operations: `DOCUMENT_UPDATED` subscription and `UPDATE_DOCUMENT` mutation. The `DocumentEditor` component subscribes to real-time updates using the subscription and updates the document content on change.

## Conclusion

In this blog post, we learned how to build a collaborative document editing tool using Javascript and GraphQL. By leveraging the power of GraphQL subscriptions, we were able to achieve real-time collaboration and updates. The combination of Javascript, GraphQL, and React makes it possible to create rich and interactive collaborative applications that meet the needs of modern teams.

#javascript #graphql