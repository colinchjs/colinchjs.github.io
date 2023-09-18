---
layout: post
title: "Implementing server-side rendering with JavaScript Module Federation and Webpack 5"
description: " "
date: 2023-09-18
tags: [javascript, webpack5]
comments: true
share: true
---

In today's tech-driven world, server-side rendering (SSR) is an essential technique for improving web performance and user experience. By rendering web pages on the server and sending the pre-rendered content to the client, we can achieve faster initial page loads and enable better search engine optimization (SEO).

One popular approach to SSR is using JavaScript Module Federation, a feature introduced in Webpack 5. Module Federation allows us to share and dynamically load modules across multiple applications, making it an ideal choice for building micro-frontends and implementing SSR. In this article, we will explore how to implement SSR using JavaScript Module Federation and Webpack 5.

## Prerequisites

Before we get started, make sure you have the following prerequisites in place:

1. Node.js installed on your machine
2. A basic understanding of Webpack 5 and JavaScript Module Federation

## Step 1: Setting up the project

First, let's create a new project directory and initialize it with npm:

```bash
mkdir ssr-project
cd ssr-project
npm init -y
```

Next, we need to install some dependencies. We will use Express as our server framework and Webpack 5 for bundling our client-side code. Run the following command to install these dependencies:

```bash
npm install express webpack webpack-cli webpack-node-externals
```

## Step 2: Configuring Webpack

Create a `webpack.config.js` file in the root of your project directory. This file will contain the configuration for both the client-side and server-side Webpack builds.

First, let's configure the client-side build. Add the following code to your `webpack.config.js`:

```javascript
// webpack.config.js
const path = require('path');

module.exports = {
  mode: 'development',
  entry: './src/client/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'client.js',
  },
  // Add your client-side webpack configuration here
};
```

Next, let's configure the server-side build. Add the following code to your `webpack.config.js`:

```javascript
// webpack.config.js
// ...

module.exports = {
  // ...
  target: 'node',
  entry: './src/server/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'server.js',
  },
  // Add your server-side webpack configuration here
};
```

## Step 3: Implementing server-side rendering

Now that we have our Webpack configuration in place, let's set up our server-side rendering code.

Create a `src` folder in the root of your project directory. Inside the `src` folder, create two files: `index.js` for the client-side entry file and `server.js` for the server-side entry file.

In the `server.js` file, add the following code to set up a basic Express server and handle the SSR logic:

```javascript
// server.js
const express = require('express');
const React = require('react');
const ReactDOMServer = require('react-dom/server');
const App = require('./App');

const server = express();

server.get('/', (req, res) => {
  const appHtml = ReactDOMServer.renderToString(<App />);
  res.send(`
    <!DOCTYPE html>
    <html>
      <head>
        <!-- Add your SEO tags here -->
      </head>
      <body>
        <div id="app">${appHtml}</div>
        <script src="/client.js"></script>
      </body>
    </html>
  `);
});

server.listen(3000, () => {
  console.log('Server is listening on port 3000');
});
```

## Step 4: Building and running the project

With everything set up, it's time to build and run the project.

Add the following scripts to your `package.json` file:

```json
"scripts": {
  "build": "webpack --config webpack.config.js",
  "start": "node dist/server.js"
}
```

To build the project, run the following command:

```bash
npm run build
```

Once the build is complete, start the server by running:

```bash
npm start
```

Visit `http://localhost:3000` in your browser, and you should see your server-side rendered content.

## Conclusion

In this article, we explored how to implement server-side rendering using JavaScript Module Federation and Webpack 5. By leveraging the power of shared modules and dynamic loading, we can achieve efficient SSR and improve web performance. The combination of JavaScript Module Federation and Webpack 5 opens up exciting possibilities for building scalable and performant micro-frontends. Happy coding!

#javascript #webpack5 #ssr #javascriptmodulefederation