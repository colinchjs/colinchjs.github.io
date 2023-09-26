---
layout: post
title: "A beginner's guide to implementing JavaScript Module Federation with Webpack 5"
description: " "
date: 2023-09-18
tags: [webpack]
comments: true
share: true
---

In recent years, there has been a growing need for modular JavaScript applications, allowing developers to break their code into smaller, reusable pieces. Webpack has been a popular choice for bundling these modules together, but with the release of Webpack 5, a new feature called **Module Federation** has been introduced, revolutionizing the way we create and share JavaScript modules across different applications.

## What is Module Federation?

**Module Federation** is a concept that enables us to share modules between different applications at runtime. Traditionally, modules were bundled and shipped with the main application, making it difficult to update or share modules across different applications. With Module Federation, we can create federated modules that can be dynamically loaded and shared across multiple applications, eliminating the need for building and shipping modules with each application.

## Setting Up Webpack 5 with Module Federation

To get started with Module Federation, you will need to install Webpack 5. Open your terminal and run the following command:

```
npm install webpack@5 webpack-cli@next --save-dev
```

Once you have Webpack 5 installed, create a `webpack.config.js` file in the root of your project. Add the following code to configure the module federation plugin:

```javascript
const ModuleFederationPlugin = require('webpack/lib/container/ModuleFederationPlugin');

module.exports = {
  entry: './src/index.js',
  output: {
    publicPath: 'http://localhost:3001/',
  },
  plugins: [
    new ModuleFederationPlugin({
      name: 'myApp',
      filename: 'remoteEntry.js',
      exposes: {
        './Button': './src/components/Button',
      },
      shared: ['react', 'react-dom'],
    }),
  ],
};
```

In this configuration, we specify the `name` of our application, the `filename` for the federated module entry file, and the `exposes` object to declare the modules that we want to share with other applications. We also specify the `shared` array to define the common dependencies that will be shared between different federated modules.

## Using Federated Modules in a Host Application

Now that we have set up Module Federation in our main application, let's see how we can use the federated modules in another application.

Create a new project for the host application and install Webpack 5:

```
npm install webpack@5 webpack-cli@next --save-dev
```

Create a `webpack.config.js` file in the root of your project with the following configuration:

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ModuleFederationPlugin = require('webpack/lib/container/ModuleFederationPlugin');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
    new ModuleFederationPlugin({
      name: 'hostApp',
      remotes: {
        myApp: 'myApp@http://localhost:3001/remoteEntry.js',
      },
      shared: ['react', 'react-dom'],
    }),
  ],
};
```

In this configuration, we define the `name` of our host application and specify the `remotes` object to declare the federated module that we want to import from the remote application. We also specify the `shared` array to indicate the common dependencies that will be shared between the host application and the federated module.

To import the federated module in our host application, create an `index.js` file in the `src` directory and add the following code:

```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import Button from 'myApp/Button';

ReactDOM.render(<Button />, document.getElementById('root'));
```

In this example, we import the `Button` component from the federated module `myApp` and render it using ReactDOM.

## Conclusion

JavaScript Module Federation is a powerful feature introduced in Webpack 5 that allows us to create and share modules between different applications dynamically. With its ability to load and update modules at runtime, it opens up new possibilities for building modular, scalable applications.

By following the steps outlined in this guide, you can start implementing Module Federation in your projects, making your code more modular and reusable.

#javascript #webpack