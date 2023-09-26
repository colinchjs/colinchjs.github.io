---
layout: post
title: "Module federation in JavaScript"
description: " "
date: 2023-09-26
tags: [webdevelopment]
comments: true
share: true
---

Module Federation is a powerful feature introduced in webpack 5 that allows you to share JavaScript modules across multiple applications or micro-frontends. It enables you to dynamically load remote modules at runtime, reducing duplication and improving code reuse.

## How does Module Federation work?

In a traditional application architecture, each application is standalone, with its own set of dependencies and bundled JavaScript files. This often leads to duplication of code and increased bundle sizes. Module Federation solves this problem by allowing applications to share modules between each other without the need for duplication.

With Module Federation, you can define remote components or modules in your webpack config, specifying their entry points and exposing specific modules or components. These remote modules can then be imported and used from other applications, breaking down the boundaries between different front-end microservices.

## Setting up Module Federation

To configure Module Federation in your project, you need to start by installing **webpack 5** and **webpack-dev-server**:

```javascript
npm install webpack@5 webpack-dev-server --save-dev
```

Next, you'll want to create a webpack.config.js file in the root of your project. This file will contain the configuration for Module Federation. 

Here's a basic example:

```javascript
const { ModuleFederationPlugin } = require('webpack').container;

module.exports = {
  entry: './src/index.js',
  output: {
    publicPath: 'http://localhost:3001/',
  },
  plugins: [
    new ModuleFederationPlugin({
      name: 'my-app',
      filename: 'remoteEntry.js',
      exposes: {
        './Button': './src/Button',
      },
    }),
  ],
};
```

In this example, we configure **my-app** as the name of our application and set **remoteEntry.js** as the name of the remote entry file that will be used by other applications to consume our modules.

We expose the `Button` component from the `./src/Button.js` file.

## Consuming remote modules

To consume the remote module in another application, we need to configure it to use the remote module. Here's an example of how to configure the consuming application's webpack.config.js file:

```javascript
const { ModuleFederationPlugin } = require('webpack').container;

module.exports = {
  // ...
  plugins: [
    new ModuleFederationPlugin({
      name: 'main-app',
      remotes: {
        'my-app': 'my-app@http://localhost:3001/remoteEntry.js',
      },
    }),
  ],
};
```

In this example, we configure **main-app** as the name of the consuming application. We define `remotes` as an object with the key **'my-app'** and the value as the URL to the remote entry file.

Now, we can import and use the remote module in our application:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';
import Button from 'my-app/Button';

const App = () => {
  return <Button />;
};

ReactDOM.render(<App />, document.getElementById('root'));
```

## Conclusion

Module Federation in JavaScript, introduced in webpack 5, enables efficient sharing and consumption of JavaScript modules across applications or micro-frontends. It eliminates code duplication, reduces bundle sizes, and promotes code reuse. By configuring your webpack setup to use Module Federation, you can improve the overall performance and maintainability of your projects.

#webdevelopment #javascript