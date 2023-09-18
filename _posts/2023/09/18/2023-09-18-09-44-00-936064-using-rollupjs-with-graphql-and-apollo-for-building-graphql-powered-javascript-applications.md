---
layout: post
title: "Using Rollup.js with GraphQL and Apollo for building GraphQL-powered JavaScript applications"
description: " "
date: 2023-09-18
tags: [GraphQL, Apollo]
comments: true
share: true
---

In today's modern web development landscape, GraphQL has gained significant popularity for its ability to efficiently fetch and manipulate data from a server. To leverage the power of GraphQL in JavaScript applications and enhance the development workflow, using a module bundler like Rollup.js along with Apollo client can be a game-changer. In this blog post, we will explore how to use Rollup.js with GraphQL and Apollo to create GraphQL-powered JavaScript applications.

## What is Rollup.js?

**Rollup.js** is a module bundler that quickly and efficiently bundles JavaScript code for production. It is commonly used to bundle libraries, frameworks, and applications. With its tree-shaking feature, Rollup.js can eliminate unused code and create smaller bundle sizes, resulting in faster loading times for your applications.

## Setting up Rollup.js with GraphQL and Apollo

To get started, create a new directory for your project and navigate to it in your terminal. Initialize a new Node.js project by running the following command:

```
npm init -y
```

Next, install Rollup.js and its required plugins:

```
npm install rollup rollup-plugin-node-resolve rollup-plugin-commonjs rollup-plugin-babel --save-dev
```

You also need to install `@babel/core` and `@babel/preset-env` for transpiling the code:

```
npm install @babel/core @babel/preset-env --save-dev
```

Now, let's create a `rollup.config.js` file in the root of your project. This file will define the Rollup.js configuration:

```javascript
import resolve from 'rollup-plugin-node-resolve';
import commonjs from 'rollup-plugin-commonjs';
import babel from 'rollup-plugin-babel';

export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.js',
    format: 'umd',
  },
  plugins: [
    resolve(),
    commonjs(),
    babel({
      presets: ['@babel/preset-env'],
    }),
  ],
};
```

In this configuration, we have specified the entry point (`src/index.js`) of our application and the output destination (`dist/bundle.js`) for the bundled code. Additionally, we have included Rollup.js plugins for resolving dependencies, transpiling the code with Babel, and handling commonjs formatted modules.

## Integrating Apollo client with Rollup.js

To use Apollo client alongside Rollup.js, we need to install the necessary packages:

```
npm install apollo-boost graphql --save
```

Next, create a new file `src/index.js` and import the required modules:

```javascript
import ApolloClient from 'apollo-boost';
import gql from 'graphql-tag';

const client = new ApolloClient({
  uri: 'https://api.example.com/graphql',
});

client.query({
  query: gql`
    query {
      todos {
        id
        title
      }
    }
  `,
})
  .then(result => console.log(result))
  .catch(error => console.error(error));
```

In this example, we create a new instance of `ApolloClient` and provide the GraphQL endpoint (`uri`) for your server. We then use `client.query` to send a query to the GraphQL server and log the result to the console.

## Building the application

To bundle your application with Rollup.js, add the following script to your `package.json`:

```json
{
  "scripts": {
    "build": "rollup -c"
  }
}
```

You can now build your application by running the following command:

```
npm run build
```

This will create a bundled JavaScript file (`bundle.js`) in the `dist` directory. You can include this file in your HTML and start using the GraphQL-powered JavaScript application.

## Conclusion

By combining the power of Rollup.js, GraphQL, and Apollo client, you can build efficient and performant JavaScript applications with ease. Rollup.js enables you to bundle your code effectively, while Apollo client simplifies the process of working with GraphQL. This combination allows developers to create GraphQL-powered applications quickly and efficiently. Start exploring the world of GraphQL-powered JavaScript applications today!

## #GraphQL #Apollo