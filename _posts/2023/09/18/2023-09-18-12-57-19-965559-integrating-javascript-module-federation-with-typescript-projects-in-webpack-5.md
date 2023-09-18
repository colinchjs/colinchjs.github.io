---
layout: post
title: "Integrating JavaScript Module Federation with TypeScript projects in Webpack 5"
description: " "
date: 2023-09-18
tags: [webpack, javascript]
comments: true
share: true
---

With the release of Webpack 5, JavaScript Module Federation has become a powerful feature for creating scalable and dynamic JavaScript applications. By leveraging Module Federation, we can easily share components and code between different applications or microfrontends.

If you're working on a TypeScript project and want to integrate Module Federation in your Webpack setup, you're in the right place. In this article, we'll walk through the steps to set up Module Federation in a TypeScript project.

## Setting up Webpack with TypeScript

Before we dive into Module Federation, let's first set up our Webpack configuration to work with TypeScript. Assuming you already have TypeScript installed in your project, let's install the necessary Webpack dependencies:

```bash
npm install webpack webpack-cli webpack-dev-server ts-loader --save-dev
```

Next, create a `webpack.config.js` file in the root of your project and add the following configuration:

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.ts',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.ts$/,
        exclude: /node_modules/,
        use: 'ts-loader',
      },
    ],
  },
  resolve: {
    extensions: ['.ts', '.js'],
  },
};
```

This configuration sets up the entry point to `./src/index.ts`, specifies the output path as `./dist/bundle.js`, and uses the `ts-loader` to handle TypeScript files.

## Adding JavaScript Module Federation

Now that we have our Webpack configuration ready, let's add Module Federation to enable component sharing. Install the necessary dependencies:

```bash
npm install @angular-architects/module-federation --save-dev
```

Next, in your Webpack configuration file, import the necessary modules and define the `moduleFederation` configuration:

```javascript
const { ModuleFederationPlugin } = require('@angular-architects/module-federation');

module.exports = {
  // ...existing configuration

  plugins: [
    new ModuleFederationPlugin({
      name: 'myApp',
      remotes: {},
      shared: ['react', 'react-dom'],
    }),
  ],
};
```

In this example, we have defined the `name` of our application as `'myApp'` and specified the `shared` modules as `react` and `react-dom`. You can modify these values based on your project requirements.

## Consuming Shared Components

To consume shared components from another application, you can add a remote configuration in the `remotes` section of the `ModuleFederationPlugin`. This allows you to load remote components dynamically.

```javascript
module.exports = {
  // ...existing configuration

  plugins: [
    new ModuleFederationPlugin({
      name: 'myApp',
      remotes: {
        remoteApp: 'remoteApp@http://localhost:3001/remoteEntry.js',
      },
      shared: ['react', 'react-dom'],
    }),
  ],
};
```

In this example, we have added a remote configuration for the `remoteApp` and specified its entry point as `http://localhost:3001/remoteEntry.js`. You can add as many remotes as necessary in your application.

## Conclusion

In this article, we have learned how to integrate JavaScript Module Federation with TypeScript projects in Webpack 5. By following these steps, you can easily set up component sharing and dynamically load remote components in your application.

With the power of Module Federation, you can create scalable and modular applications by sharing code between different projects or microfrontends. Make sure to explore the Module Federation documentation for more advanced features and configurations.

#webpack #javascript