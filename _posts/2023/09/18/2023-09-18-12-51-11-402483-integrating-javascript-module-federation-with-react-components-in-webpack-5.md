---
layout: post
title: "Integrating JavaScript Module Federation with React components in Webpack 5"
description: " "
date: 2023-09-18
tags: [JavaScriptModuleFederation, Webpack5]
comments: true
share: true
---

In the latest release of Webpack 5, the **JavaScript Module Federation** feature has been introduced. This feature allows you to share and consume JavaScript modules dynamically between different applications, enabling seamless integration and code reuse. In this blog post, we will focus on integrating JavaScript Module Federation with React components in Webpack 5.

## What is JavaScript Module Federation?

JavaScript Module Federation is a concept that enables developers to share code between applications in a more efficient way. With Module Federation, you can consume remote components as if they were part of your local application, making it easier to build distributed applications where different parts of the UI are developed and deployed independently.

## Integrating JavaScript Module Federation with React components

To integrate JavaScript Module Federation with React components in Webpack 5, follow these steps:

### Step 1: Set up the host application

1. In your host application, install the necessary dependencies:

```bash
npm install webpack@5 module-federation-plugin react react-dom
```

2. Create a `webpack.config.js` file at the root of your project and configure the Module Federation plugin:

```javascript
const { ModuleFederationPlugin } = require('webpack').container;

module.exports = {
  // ... other webpack configurations
  plugins: [
    new ModuleFederationPlugin({
      name: 'host',
      remotes: {
        remoteApp: 'remoteApp@http://localhost:3001/remoteEntry.js', // Replace with the actual remote URL
      },
    }),
  ],
};
```

3. Import and render the remote React component in your host application:

```jsx
import React from 'react';
import ReactDOM from 'react-dom';

const RemoteComponent = React.lazy(() => import('remoteApp/RemoteComponent'));

function App() {
  return (
    <div>
      <h1>Host Application</h1>
      <React.Suspense fallback="Loading remote component...">
        <RemoteComponent />
      </React.Suspense>
    </div>
  );
}

ReactDOM.render(<App />, document.getElementById('root'));
```

### Step 2: Set up the remote application

1. In your remote application, install the necessary dependencies:

```bash
npm install webpack@5 module-federation-plugin react react-dom
```

2. Create a `webpack.config.js` file at the root of your project and configure the Module Federation plugin:

```javascript
const { ModuleFederationPlugin } = require('webpack').container;

module.exports = {
  // ... other webpack configurations
  output: {
    publicPath: 'http://localhost:3001/',
  },
  plugins: [
    new ModuleFederationPlugin({
      name: 'remoteApp',
      filename: 'remoteEntry.js',
      exposes: {
        "./RemoteComponent": "./src/RemoteComponent", // Replace with the actual path to your remote component
      },
    }),
  ],
};
```

3. Create your remote React component `RemoteComponent.js`:

```jsx
import React from 'react';

function RemoteComponent() {
  return <h2>Remote Component</h2>;
}

export default RemoteComponent;
```

### Step 3: Run the applications

1. Start the host application:

```bash
npx webpack serve --open
```

2. Start the remote application:

```bash
npx webpack serve --port 3001
```

## Conclusion

By integrating JavaScript Module Federation with React components in Webpack 5, we can leverage the power of code sharing and remote components. This allows us to build more modular and scalable applications, where different parts of the UI can be developed and deployed independently. JavaScript Module Federation is a powerful feature that simplifies the development and maintenance of distributed applications.

#JavaScriptModuleFederation #Webpack5 #ReactComponents