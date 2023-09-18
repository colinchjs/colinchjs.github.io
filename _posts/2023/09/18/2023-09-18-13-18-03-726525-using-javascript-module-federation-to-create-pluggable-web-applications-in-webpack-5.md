---
layout: post
title: "Using JavaScript Module Federation to create pluggable web applications in Webpack 5"
description: " "
date: 2023-09-18
tags: [webpack, ModuleFederation]
comments: true
share: true
---

In the world of web development, creating modular and pluggable applications is essential for scalability and maintainability. With the introduction of Webpack 5, a new feature called **Module Federation** has been introduced, allowing developers to create pluggable applications by sharing code between different projects without the need for a monolithic architecture.

## What is Module Federation?

Module Federation is a feature in Webpack 5 that enables developers to share dependencies and code between different JavaScript applications or microfrontends. It allows for the creation of independent, encapsulated modules that can be loaded and consumed by multiple applications in a distributed manner.

## Why use Module Federation?

There are several benefits to using Module Federation in your projects:

1. **Code sharing**: Module Federation allows you to share code and dependencies between different applications or microfrontends, reducing duplication and increasing efficiency.

2. **Independent deployment**: Each module can be developed and deployed independently without affecting other parts of the application, resulting in faster development cycles and the ability to release updates separately.

3. **Dynamic loading**: With Module Federation, modules can be loaded dynamically at runtime, allowing for lazy loading and reducing the initial bundle size of your applications.

## Getting Started with Module Federation in Webpack 5

To get started with Module Federation in Webpack 5, follow these steps:

1. **Ensure you're using Webpack 5**: Make sure you have Webpack 5 installed in your project. If not, you can install it using npm or yarn:

   ```shell
   npm install webpack@5 --save-dev
   ```

2. **Create the host application**: Create a new webpack configuration file for the host application. In this file, define the `ModuleFederationPlugin` and configure the remotes and shared modules.

   ```javascript
   const { ModuleFederationPlugin } = require('webpack').container;
   
   module.exports = {
     // ...
     plugins: [
       new ModuleFederationPlugin({
         name: 'host',
         remotes: {
           remoteApp1: 'remoteApp1@http://localhost:3001/remoteEntry.js',
           remoteApp2: 'remoteApp2@http://localhost:3002/remoteEntry.js',
         },
         shared: ['react', 'react-dom'],
       }),
     ],
   };
   ```

   In the above example, `remoteApp1` and `remoteApp2` are the names of the remote applications, `http://localhost:3001/remoteEntry.js` and `http://localhost:3002/remoteEntry.js` are the URLs to their entry points, and `react` and `react-dom` are shared modules.

3. **Create the remote applications**: Create separate webpack configurations for each remote application. Similar to the host application, define the `ModuleFederationPlugin` and configure the exposed modules.

   ```javascript
   const { ModuleFederationPlugin } = require('webpack').container;
   
   module.exports = {
     // ...
     plugins: [
       new ModuleFederationPlugin({
         name: 'remoteApp1',
         exposes: {
           './Button': './src/Button',
         },
       }),
     ],
   };
   ```

   In the above example, `remoteApp1` is the name of the remote application, and `./src/Button` is the path to the module that is exposed and can be consumed by the host application or other remote applications.

4. **Start the applications**: Start the host application and the remote applications separately. You can use webpack-dev-server or any other server of your choice to run the applications.

5. **Load the remote modules**: In your host application, import and use the modules that are exposed by the remote applications.

   ```javascript
   import React from 'react';
   import ReactDOM from 'react-dom';
   import Button from 'remoteApp1/Button';
   
   const App = () => {
     return (
       <div>
         <Button />
       </div>
     );
   }
   
   ReactDOM.render(<App />, document.getElementById('root'));
   ```

   In the above example, the `Button` component from the `remoteApp1` remote application is imported and used in the host application.

## Conclusion

JavaScript Module Federation in Webpack 5 offers a powerful way to create pluggable web applications by sharing code and dependencies between applications. It provides the ability to develop and deploy modules independently, reducing duplication and increasing code reuse. By leveraging Module Federation, you can build scalable and modular applications that can easily adapt and grow over time.

#webpack #ModuleFederation