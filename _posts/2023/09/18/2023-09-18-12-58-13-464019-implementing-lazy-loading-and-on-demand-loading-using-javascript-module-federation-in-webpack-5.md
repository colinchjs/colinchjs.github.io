---
layout: post
title: "Implementing lazy loading and on-demand loading using JavaScript Module Federation in Webpack 5"
description: " "
date: 2023-09-18
tags: [webdevelopment, webpack]
comments: true
share: true
---

In today's web development world, optimizing the loading speed of websites is crucial. One popular technique to achieve this is lazy loading, which involves loading only the required resources when they are needed. Another technique is on-demand loading, where modules are loaded only when a specific action is triggered.

Webpack 5's JavaScript Module Federation allows us to implement both lazy loading and on-demand loading easily. Let's explore how we can leverage this feature to optimize our website.

## What is JavaScript Module Federation?

JavaScript Module Federation is a feature introduced in Webpack 5 that enables us to share code across different Webpack projects. It allows us to dynamically load and communicate between multiple applications, enabling us to build micro frontends and improve code sharing.

## Lazy Loading with JavaScript Module Federation

To implement lazy loading, we need to split our application into smaller chunks called federated modules. These modules are loaded on-demand, reducing the initial load time of our application.

Here's an example of how we can implement lazy loading with JavaScript Module Federation:

```javascript
// Remote app webpack config
const ModuleFederationPlugin = require('webpack/lib/container/ModuleFederationPlugin');

module.exports = {
  // Other webpack configuration options...
  plugins: [
    new ModuleFederationPlugin({
      name: 'remoteApp',
      filename: 'remoteEntry.js',
      exposes: {
        './Component1': './src/components/Component1',
        './Component2': './src/components/Component2',
      },
      shared: {
        react: { singleton: true },
        'react-dom': { singleton: true },
      },
    }),
  ],
};
```

In the example above, we configure the webpack plugin to expose specific components from our application. These components can be dynamically loaded by other applications using the `import()` function.

## On-Demand Loading with JavaScript Module Federation

On-demand loading allows us to load modules only when a specific action is triggered, such as a user clicking on a button or navigating to a certain page. This helps reduce the initial load time and improves the user experience.

Here's an example of how we can implement on-demand loading with JavaScript Module Federation:

```javascript
// Remote app webpack config
const ModuleFederationPlugin = require('webpack/lib/container/ModuleFederationPlugin');

module.exports = {
  // Other webpack configuration options...
  plugins: [
    new ModuleFederationPlugin({
      name: 'remoteApp',
      filename: 'remoteEntry.js',
      exposes: {
        './Component1': './src/components/Component1',
        './Component2': './src/components/Component2',
      },
      shared: {
        react: { singleton: true },
        'react-dom': { singleton: true },
      },
    }),
  ],
};

// Host app
import { loadRemoteModule } from './utils/moduleLoader';

// On button click event handler
const handleClick = async () => {
  const remoteModule = await loadRemoteModule('remoteApp', './Component1');
  // Use the loaded module
  remoteModule.foo();
};

// Utility function to load remote modules
export const loadRemoteModule = async (remoteName, exposedModule) => {
  const container = window[remoteName]; // Reference to the remote application container
  await container.init(__webpack_share_scopes__.default); // Initialize the container
  const factory = await container.get(exposedModule); // Get the module factory
  const Module = factory(); // Create the module
  return Module;
};
```

In the example above, we have a button click event handler that loads a remote module named 'remoteApp' and uses a method called `foo()` from the loaded module.

## Conclusion

JavaScript Module Federation in Webpack 5 provides us with a powerful tool to implement lazy loading and on-demand loading, improving the loading speed and user experience of our web applications. By splitting our application into smaller federated modules, we can load resources only when needed, reducing the initial load time and optimizing performance.

#webdevelopment #webpack