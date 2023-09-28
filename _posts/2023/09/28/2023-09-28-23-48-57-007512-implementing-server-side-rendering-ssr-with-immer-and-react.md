---
layout: post
title: "Implementing server-side rendering (SSR) with Immer and React"
description: " "
date: 2023-09-28
tags: [webdevelopment, server]
comments: true
share: true
---

In this tutorial, we will explore how to implement server-side rendering using Immer and React. Immer is a powerful library that simplifies immutable state management in JavaScript applications.

## Prerequisites

To follow along with this tutorial, you should have a basic understanding of React and Node.js. Make sure you have Node.js and npm installed on your machine.

Let's get started!

## Setting up the project

Create a new directory for your project and navigate to it in the terminal. Run the following commands to set up a new React project:

```shell
npx create-react-app ssr-app
cd ssr-app
```

Next, install the `express` and `react-dom` packages by running the following command:

```shell
npm install express react-dom
```

## Implementing server-side rendering

### Step 1: Create a server.js file

Create a new file called `server.js` at the root of your project. Open it in your code editor.

### Step 2: Import the required modules

In the `server.js`, add the following code to import the necessary modules:

```javascript
import express from 'express';
import React from 'react';
import { renderToString } from 'react-dom/server';
import App from './src/App';
```

### Step 3: Set up the server

Below the import statements, add the following code to set up our Express server:

```javascript
const app = express();
const port = 3000;

app.use(express.static('build'));

app.get('/', (req, res) => {
  const html = renderToString(<App />);
  res.send(`
    <!DOCTYPE html>
    <html>
      <head>
        <title>Server-side Rendering</title>
      </head>
      <body>
        <div id="root">${html}</div>
        <script src="/bundle.js"></script>
      </body>
    </html>
  `);
});

app.listen(port, () => {
  console.log(`Server is listening on port ${port}`);
});
```

Here, we set up a basic Express server that serves the static files from the `build` directory. The `/` route renders our React component (`<App />`) to a string using `renderToString` and sends the resulting markup to the client.

### Step 4: Modify the package.json

Open the `package.json` file and replace the `"scripts"` section with the following code:

```json
"scripts": {
  "start": "react-scripts build && node server.js",
  "build": "react-scripts build"
}
```

This script will build the React app using `react-scripts` and start the server simultaneously.

### Step 5: Start the server

Run the following command to start the server:

```shell
npm start
```

Visit `http://localhost:3000` in your browser, and you should see your React app rendered on the server.

That's it! You have successfully implemented server-side rendering with Immer and React. SSR improves the initial loading speed and enhances SEO for your web application.

#webdevelopment #server #SSR #Immer #React