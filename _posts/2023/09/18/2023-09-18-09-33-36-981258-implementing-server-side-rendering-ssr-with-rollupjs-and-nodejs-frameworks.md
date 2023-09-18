---
layout: post
title: "Implementing server-side rendering (SSR) with Rollup.js and Node.js frameworks"
description: " "
date: 2023-09-18
tags: [webdevelopment, serversiderendering]
comments: true
share: true
---

Server-Side Rendering (SSR) has become a popular technique for web development, as it allows a website to be rendered on the server and delivered to the client as a fully rendered page. This can improve performance, SEO, and provide a better user experience.

In this article, we will explore how to implement SSR using Rollup.js, a bundler, and Node.js frameworks like Express.js or Koa.js.

## Why Use Server-Side Rendering?

Server-Side Rendering offers several benefits over traditional client-side rendering (CSR). Let's take a look at a couple of them:

1. **Improved Performance**: SSR delivers fully rendered pages to the client, reducing the time required to render on the client-side. This can result in faster page load times and improved performance, especially on slower devices or networks.

2. **SEO-Friendly**: Search engines can easily crawl and index the content of SSR pages, as the fully rendered HTML is available in the initial response. This can improve your website's visibility in search engine rankings.

## Setting Up the Project

1. Start by creating a new directory for your project and navigate into it:
   ```
   mkdir my-ssr-project
   cd my-ssr-project
   ```

2. Initialize a new npm project:
   ```
   npm init -y
   ```

3. Install the required dependencies:
   ```
   npm install rollup rollup-plugin-node-resolve rollup-plugin-commonjs express
   ```

4. Create a new file named `server.js` in the project directory and add the following code:

```javascript
const express = require('express');
const app = express();

app.use(express.static('public'));

app.get('*', (req, res) => {
  // Server-side rendering logic goes here
});

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

In this example, we are using Express.js, but you can replace it with any other Node.js framework you prefer.

## Implementing Server-Side Rendering Logic

To implement server-side rendering logic, we will use Rollup.js to bundle our server-side code and handle imports.

1. Create a new file named `src/server.js` and add the following code:

```javascript
import express from 'express';
import { renderToString } from 'react-dom/server';
import App from './App.jsx';

const app = express();

app.use(express.static('public'));

app.get('*', (req, res) => {
  const html = renderToString(<App />);
  res.send(`
    <!DOCTYPE html>
    <html>
    <head>
      <title>My SSR App</title>
    </head>
    <body>
      ${html}
    </body>
    </html>
  `);
});

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

In this example, we use React and the `renderToString` function from `react-dom/server` to render our application to an HTML string.

2. Next, modify your `package.json` file to add a build script:

```json
{
  "scripts": {
    "build": "rollup -c",
    "start": "node dist/server.js"
  }
}
```

3. Create a new file named `rollup.config.js` in the project directory and add the following code:

```javascript
import commonjs from 'rollup-plugin-commonjs';
import resolve from 'rollup-plugin-node-resolve';

export default {
  input: 'src/server.js',
  output: {
    file: 'dist/server.js',
    format: 'cjs',
  },
  plugins: [commonjs(), resolve()],
};
```

4. Build the project by running the following command:
   ```
   npm run build
   ```

5. Finally, start the server by running:
   ```
   npm start
   ```

## Conclusion

Server-Side Rendering can provide significant benefits for your web application. With the help of Rollup.js and Node.js frameworks like Express.js or Koa.js, you can easily implement SSR and improve the performance and SEO of your application.

Remember to optimize your server-side code for better performance and leverage caching techniques to further improve the user experience.

#webdevelopment #serversiderendering