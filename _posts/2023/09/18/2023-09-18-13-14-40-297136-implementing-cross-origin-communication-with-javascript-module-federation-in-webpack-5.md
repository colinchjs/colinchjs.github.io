---
layout: post
title: "Implementing cross-origin communication with JavaScript Module Federation in Webpack 5"
description: " "
date: 2023-09-18
tags: [hashtags]
comments: true
share: true
---

Cross-origin communication refers to the ability of JavaScript modules to communicate and share data across different origins or domains. This can be useful when working with complex, microfrontends-based architectures or when integrating multiple applications that reside on different domains.

Webpack 5, along with the JavaScript Module Federation feature, allows for seamless cross-origin communication between modules. In this blog post, we'll explore how to enable and implement this feature in your Webpack-powered projects.

## Prerequisites

To follow along with this tutorial, you'll need the following:

- Basic knowledge of JavaScript and Webpack
- Webpack 5 installed globally or locally in your project

## Setting up the Host Application

Before we can enable cross-origin communication, we need to set up a host application that will serve as the entry point for our module federation. Here are the steps:

1. Create a new directory for your project and navigate to it in your terminal.
2. Initialize a new npm project by running the command:

```bash
npm init -y
```

3. Install Webpack and its related dependencies:

```bash
npm install webpack webpack-cli webpack-dev-server
```

4. Create the following file structure for your host application:

```
- src
  - index.js
- public
  - index.html
- webpack.config.js
```

5. Open `src/index.js` and add the following code:

```javascript
import('./remoteApp').then(({ run }) => {
  run(document.getElementById('root'));
});
```

This code imports a remote application called `remoteApp` and executes its `run` function by passing in the root element of the host application.

6. Create a new file `public/index.html` and add the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Host Application</title>
</head>
<body>
  <div id="root"></div>
  <script src="/dist/main.js"></script>
</body>
</html>
```

This HTML file defines the root element for the host application and includes the bundled JavaScript file `main.js`.

7. Open `webpack.config.js` and add the following configuration:

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js',
  },
  devServer: {
    static: {
      directory: path.join(__dirname, 'public'),
    },
    port: 3000,
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
  ],
};
```

This Webpack configuration sets the entry point to `src/index.js` and creates the bundle file `main.js` in the `dist` directory. It also configures the dev server to serve static files from the `public` directory and sets the port to 3000.

## Configuring the Remote Application

To enable cross-origin communication, we need to configure the remote application that will be loaded into the host application. Here are the steps:

1. Create a new directory called `remote-app` in the root of your project.
2. Navigate to the `remote-app` directory in your terminal and run the following command to initialize a new npm project:

```bash
npm init -y
```

3. Install Webpack and its related dependencies:

```bash
npm install webpack webpack-cli
```

4. Create the following file structure for your remote application:

```
- src
  - index.js
```

5. Open `src/index.js` and add the following code:

```javascript
export const run = (rootElement) => {
  const container = document.createElement('div');
  container.textContent = 'Remote Application';

  rootElement.appendChild(container);
};
```

This code exports a `run` function that takes in a root element and appends a container div with the text "Remote Application" to it.

6. Create a new file `webpack.config.js` in the `remote-app` directory and add the following configuration:

```javascript
module.exports = {
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'remoteApp.js',
    publicPath: 'http://localhost:3001/',
  },
};
```

This Webpack configuration sets the output path to `dist`, the bundle filename to `remoteApp.js`, and the public path to `http://localhost:3001/`.

## Enabling Module Federation

With the host and remote applications set up, we can now enable JavaScript Module Federation to allow for cross-origin communication. Here are the steps:

1. Open the `webpack.config.js` file in the root of your project (host application) and update the configuration as follows:

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ModuleFederationPlugin = require('webpack').container.ModuleFederationPlugin;

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js',
  },
  devServer: {
    static: {
      directory: path.join(__dirname, 'public'),
    },
    port: 3000,
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
    new ModuleFederationPlugin({
      name: 'hostApp',
      remotes: {
        remoteApp: 'remoteApp@http://localhost:3001/remoteApp.js',
      },
    }),
  ],
};
```

This updated configuration adds the `ModuleFederationPlugin` as a webpack plugin. The `name` property is set to `'hostApp'`, which is the name of the host application. The `remotes` property defines the remote application `remoteApp` and its URL.

2. Open the `webpack.config.js` file in the `remote-app` directory (remote application) and update the configuration as follows:

```javascript
const ModuleFederationPlugin = require('webpack').container.ModuleFederationPlugin;

module.exports = {
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'remoteApp.js',
    publicPath: 'http://localhost:3001/',
  },
  plugins: [
    new ModuleFederationPlugin({
      name: 'remoteApp',
      filename: 'remoteEntry.js',
      exposes: {
        './remoteApp': './src/index.js',
      },
    }),
  ],
};
```

This updated configuration adds the `ModuleFederationPlugin` as a webpack plugin for the remote application. The `name` property is set to `'remoteApp'`, which is the name of the remote application. The `filename` property specifies the name of the remote entry file. The `exposes` property defines the module that will be exposed for consumption by other applications.

## Running the Applications

Now that everything is set up, let's run the applications and see the magic of cross-origin communication!

1. In your terminal, navigate to the root of your project (host application) and run the command:

```bash
npm start
```

This will start the dev server and serve the host application on `http://localhost:3000/`.

2. In a new terminal window, navigate to the `remote-app` directory and run the command:

```bash
npm start
```

This will build and serve the remote application on `http://localhost:3001/`.

3. Open your browser and visit `http://localhost:3000/`. You should see the host application with the text "Remote Application" appended to it. This indicates that the host and remote applications are successfully communicating across origins!

## Conclusion

In this tutorial, we explored how to implement cross-origin communication using JavaScript Module Federation in Webpack 5. By following the steps outlined, you can enable seamless communication between different applications and domains, enabling powerful integrations and modular architectures.

Remember to configure the host and remote applications accordingly and leverage the `ModuleFederationPlugin` to establish the necessary connections. Happy coding!

#hashtags: #JavaScript #Webpack