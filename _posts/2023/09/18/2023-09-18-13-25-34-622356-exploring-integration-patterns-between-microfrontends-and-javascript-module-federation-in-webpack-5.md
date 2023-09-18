---
layout: post
title: "Exploring integration patterns between microfrontends and JavaScript Module Federation in Webpack 5"
description: " "
date: 2023-09-18
tags: [techblog, webpack]
comments: true
share: true
---

In the world of web development, the concept of microfrontends has gained a lot of popularity. It allows teams to build and deploy independent frontend modules that can be composed to create a cohesive user interface. This modular approach empowers teams to work in isolation on different parts of their application, making development and scaling much easier.

One of the tools that can help in implementing microfrontends is **JavaScript Module Federation** - a feature introduced in **Webpack 5**. This feature enables modules to be shared across different builds and allows for **dynamic remoting** of those modules in real-time over the network.

## Setting up a basic microfrontend architecture

To begin, you need to create separate microfrontend projects. Each project will be responsible for its own functionality. These microfrontends are typically implemented as separate webpack builds.

In the root of each microfrontend project, you should have a `webpack.config.js` file. Here's a basic example for one of the microfrontends:

```javascript
const path = require('path');

module.exports = {
   entry: './src/index.js',
   output: {
      filename: 'bundle.js',
      path: path.resolve(__dirname, 'dist')
   },
   // Other webpack config options...
};
```

Repeat this setup for each microfrontend project.

## Implementing JavaScript Module Federation

With Webpack 5 and JavaScript Module Federation, you can easily share and remotely load modules between microfrontends. Here's how you can set it up.

1. In each microfrontend's webpack config, add the `ModuleFederationPlugin`:

```javascript
const { ModuleFederationPlugin } = require('webpack').container;

module.exports = {
   // Other webpack config options...
   plugins: [
      new ModuleFederationPlugin({
         name: 'microfrontend1',
         filename: 'remoteEntry.js',
         exposes: {
            './MicrofrontendComponent': './src/MicrofrontendComponent',
         },
         shared: {
            react: {
               requiredVersion: '^16.0.0',
            },
            // Other shared modules...
         },
      }),
   ],
};
```

2. In the consuming microfrontend's `webpack.config.js`, add the `ContainerPlugin` to initialize the federation module:

```javascript
const { ContainerPlugin } = require('webpack').container;

module.exports = {
   // Other webpack config options...
   plugins: [
      new ContainerPlugin({
         name: 'container',
         remotes: {
            microfrontend1: 'microfrontend1@http://localhost:5001/remoteEntry.js',
         },
      }),
   ],
};
```

3. In the consuming microfrontend's HTML file, add a container div for the remote microfrontend:

```html
<div id="microfrontend1"></div>
```

4. Finally, in the consuming microfrontend's entry point, load the remote module:

```javascript
import('./MicrofrontendComponent')
   .then((module) => {
      // Use the remote module
   })
   .catch((err) => {
      // Handle error if module loading fails
   });
```

## Conclusion

JavaScript Module Federation in Webpack 5 provides a powerful and flexible approach to integrating microfrontends. By sharing modules between projects, you can create a more modular and scalable architecture.

Remember to make use of versioning and other best practices when using shared modules to ensure compatibility and avoid conflicts.

With the growing adoption of microfrontends, exploring integration patterns like JavaScript Module Federation can help you build more maintainable and scalable web applications.

#techblog #webpack