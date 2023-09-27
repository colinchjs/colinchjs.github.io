---
layout: post
title: "Implementing file uploads with GraphQL in Javascript"
description: " "
date: 2023-09-27
tags: [graphql]
comments: true
share: true
---

In modern web development, it is common for applications to allow users to upload files. Traditionally, file uploads were handled using techniques such as form submissions or AJAX requests. However, with the rise of GraphQL as a powerful query language for APIs, there are now more efficient and elegant ways to handle file uploads.

In this blog post, we will explore how to implement file uploads using GraphQL in JavaScript. We will be using the popular Apollo Server library for our GraphQL server implementation.

## Setting Up the Server

To get started, let's set up a basic GraphQL server using Apollo Server. First, make sure you have Node.js and npm installed on your machine. Then, create a new directory for your project and navigate to it in your terminal.

Next, initialize a new Node.js project by running the following command:

```bash
npm init -y
```

This will generate a new `package.json` file in your project directory. Now, let's install the necessary dependencies:

```bash
npm install apollo-server graphql
```

Once the installation is complete, create a new file called `server.js` and open it in your preferred code editor. Here's a basic setup for our GraphQL server:

```javascript
const { ApolloServer, gql } = require('apollo-server');

// Schema definition
const typeDefs = gql`
  type Query {
    hello: String
  }
`;

// Resolvers
const resolvers = {
  Query: {
    hello: () => 'Hello, world!',
  },
};

// Apollo Server setup
const server = new ApolloServer({
  typeDefs,
  resolvers,
});

// Start the server
server.listen().then(({ url }) => {
  console.log(`Server running at ${url}`);
});
```

With this setup, we have a basic GraphQL server that responds with "Hello, world!" when the `hello` query is executed. Now, let's move on to implementing file uploads.

## Adding File Upload Support

To support file uploads in GraphQL, we need to extend our server setup with additional configurations. First, we need to install the necessary dependencies:

```bash
npm install apollo-server-express graphql-upload express
```

Next, update `server.js` with the following changes:

```javascript
const express = require('express');
const { ApolloServer, gql } = require('apollo-server-express');
const { GraphQLUpload } = require('graphql-upload');

// Schema definition
const typeDefs = gql`
  scalar Upload

  type Query {
    hello: String
  }

  type Mutation {
    uploadFile(file: Upload!): String
  }
`;

// Resolvers
const resolvers = {
  Query: {
    hello: () => 'Hello, world!',
  },
  Mutation: {
    uploadFile: async (_, { file }) => {
      const { createReadStream, filename } = await file;
      // Handle file upload logic here
      // e.g. save the file to disk or process it in some way
      // Return a meaningful response

      return `File ${filename} uploaded successfully!`;
    },
  },
};

// Apollo Server setup
const server = new ApolloServer({
  typeDefs,
  resolvers,
  uploads: false,
});

const app = express();

// Enable file uploads
server.applyMiddleware({
  app,
  uploads: false,
});

// Start the server
app.listen({ port: 4000 }, () => {
  console.log(`Server running at http://localhost:4000${server.graphqlPath}`);
});
```

In the updated code, we have added a new scalar type `Upload` to represent file uploads in our schema definition. We also added a new mutation field `uploadFile` that accepts an argument of type `Upload`.

The resolver for `uploadFile` demonstrates how to handle file uploads. The file object received as an argument contains a `createReadStream` function, which allows us to access the file's content. You can then handle the file upload logic based on your needs, such as saving the file to disk or processing it in some way. In this example, we simply return a success message.

To enable file uploads, we need to use the `graphql-upload` package and configure Apollo Server to support uploads. Finally, we use the `express` library to create an HTTP server and apply the Apollo Server middleware.

## Testing File Uploads

To test file uploads, you can use a GraphQL client or tools like `curl` or `Postman`. Here's an example `curl` command for testing the `uploadFile` mutation:

```bash
curl -X POST -F "operations={\"query\": \"mutation($file: Upload!) { uploadFile(file: $file) }\", \"variables\": { \"file\": null } }" -F "map={\"0\": [\"variables.file\"]}" -F "0=@path/to/file.jpg" http://localhost:4000/graphql
```

Replace `path/to/file.jpg` with the actual file path you want to upload. The response from the server should indicate that the file was uploaded successfully.

## Conclusion

In this blog post, we have learned how to implement file uploads with GraphQL in JavaScript using Apollo Server. By leveraging the support for file uploads provided by GraphQL, we can simplify the handling of file uploads in our applications. Whether it's uploading user avatars, attachments, or any other file type, GraphQL makes it easy to handle file uploads efficiently.

#graphql #javascript