---
layout: post
title: "Implementing server-side rendering (SSR) with Immer and Svelte"
description: " "
date: 2023-09-28
tags: [webdevelopment, javascript]
comments: true
share: true
---

Server-side rendering (SSR) allows us to render web pages on the server and send them to the client, resulting in faster initial page load times and improved SEO. In this blog post, we will explore how to implement SSR with Immer and Svelte, two popular libraries in the JavaScript ecosystem.

## Prerequisites

Before we start, make sure you have a basic understanding of Node.js, Express.js, and Svelte. If you're new to these technologies, take some time to familiarize yourself with them.

## Getting started

To begin, let's create a new project and install the necessary dependencies:

```bash
$ mkdir my-svelte-ssr-app
$ cd my-svelte-ssr-app
$ npm init -y
$ npm install express svelte immer
```

## Setting up Express.js server

Next, let's set up our Express.js server to handle the SSR logic. Create a new file `server.js` and add the following code:

```javascript
const express = require('express');
const { createSSRApp } = require('vue');
const { renderToString } = require('@vue/server-renderer');
const App = require('./App.svelte').default;
const template = require('fs').readFileSync('index.html', 'utf-8');

const app = express();
const port = 3000;

app.get('/', async (req, res) => {
  const app = createSSRApp(App);
  const appContent = await renderToString(app);

  res.send(
    template.replace(
      '<div id="app"></div>',
      `<div id="app">${appContent}</div>`
    )
  );
});

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```

## Creating the Svelte component

Now, let's create our main Svelte component `App.svelte`:

```bash
$ mkdir src
$ touch src/App.svelte
```

Inside `App.svelte`, add the following code:

```html
<script>
  import { readable } from 'svelte/store';
  import { produce } from 'immer';

  const count = readable(0, (set) => {
    const interval = setInterval(() => {
      set(produce((state) => {
        state += 1;
      }));
    }, 1000);

    return () => clearInterval(interval);
  });
</script>

<main>
  <h1>Svelte SSR with Immer</h1>
  <p>Current count: {$count}</p>
</main>

<style>
  main {
    text-align: center;
    padding: 2rem;
    font-family: Arial, sans-serif;
  }
</style>
```

## Creating the HTML template

Lastly, let's create an HTML template for our SSR application. Create a file `index.html` in the root directory and add the following:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Svelte SSR with Immer</title>
</head>
<body>
  <div id="app"></div>
  <script src="/bundle.js"></script>
</body>
</html>
```

## Building and running the application

To build and start the application, add the following script entries to your `package.json`:

```json
{
  "scripts": {
    "build": "svelte-kit build",
    "dev": "svelte-kit dev",
    "start": "node server.js"
  }
}
```

Now, you can run the following commands:

```bash
$ npm run build
$ npm start
```

Visit `http://localhost:3000` in your browser to see the SSR application in action!

## Conclusion

In this tutorial, we learned how to implement server-side rendering (SSR) using Immer and Svelte. SSR can significantly improve page load times and enhance SEO. With the power of Immer and Svelte, we can build blazing fast and SEO-friendly applications. Make sure to explore the documentation of both libraries to fully utilize their features and create amazing web experiences.

#webdevelopment #ssr #javascript