---
layout: post
title: "How to handle versioning and dependencies in JavaScript Module Federation with Webpack 5"
description: " "
date: 2023-09-18
tags: [javascript, webpack]
comments: true
share: true
---

With the release of Webpack 5, JavaScript Module Federation has become a popular approach for building micro-frontends and sharing code between different applications. However, one challenge that arises with this approach is managing versioning and dependencies across multiple federated modules.

Fortunately, Webpack 5 provides a solution to this problem through the use of `share` scope, which allows you to define shared modules and their versions. 

Here are the steps to handle versioning and dependencies in JavaScript Module Federation with Webpack 5:

## Step 1: Configure the Webpack 5 Federation Plugin

To utilize module federation in your Webpack 5 configuration, you need to add the `ModuleFederationPlugin` to your webpack config. Inside the plugin configuration, you can define the shared modules and their versions.

```javascript
const { ModuleFederationPlugin } = require('webpack').container;

module.exports = {
  // ... other webpack config options
  plugins: [
    new ModuleFederationPlugin({
      shared: {
        react: { // example shared module
          eager: true, // load the module eagerly in all federated modules
          singleton: true, // only one version of the module will be installed
        },
        // Define additional shared modules and their configuration
        // ...
      },
      // ... other plugin configuration options
    }),
  ],
};
```

In the above example, we define `react` as a shared module and configure it to be loaded eagerly in all federated modules. We also specify that only one version of `react` should be installed.

## Step 2: Use Shared Modules in Federated Modules

Once you have defined the shared modules in your Webpack 5 configuration, you can use them in your federated modules by importing them like any other module.

```javascript
import React from 'react'; // import shared react module

// Use the shared react module
function App() {
  return <div>Hello World!</div>;
}

export default App;
```

In the above example, we import the shared `React` module and use it in our `App` component.

## Step 3: Handling Dependencies

With module federation, it's important to ensure that the shared modules and their dependencies are compatible across federated modules. If there are conflicting dependencies or different versions of a module being used, it can lead to unexpected behavior.

To handle dependencies, it's recommended to use a package manager like Yarn or npm to manage your project dependencies. By using a lock file (such as `yarn.lock` or `package-lock.json`), you can ensure that the same version of a shared module is installed across all federated modules.

If you encounter dependency conflicts, you can try using the `resolve` configuration in your webpack config to enforce a specific version of a module.

```javascript
module.exports = {
  // ... other webpack config options
  resolve: {
    alias: {
      react: path.resolve('./node_modules/react'), // enforce a specific version
    },
  },
};
```

By specifying the exact path to a module, you can enforce a specific version.

## Conclusion

JavaScript Module Federation with Webpack 5 provides a powerful mechanism for sharing code and building micro-frontends. By properly configuring shared modules and managing dependencies, you can ensure a smooth development experience. Remember to leverage the `share` scope in the Module Federation Plugin to define shared modules and their versions, and use a package manager with a lock file to handle dependencies effectively.

#javascript #webpack-module-federation