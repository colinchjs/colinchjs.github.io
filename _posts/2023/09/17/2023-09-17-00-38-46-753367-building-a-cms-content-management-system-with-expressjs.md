---
layout: post
title: "Building a CMS (Content Management System) with Express.js"
description: " "
date: 2023-09-17
tags: [Express]
comments: true
share: true
---

With the increasing need for dynamic and interactive web applications, having a versatile content management system (CMS) in place is crucial. In this tech blog post, we will explore how to build a CMS using Express.js, a popular Node.js web application framework.

## Why Express.js?

Express.js provides a powerful and flexible framework for building web applications. It is lightweight, easy to understand, and offers a wide range of features and middleware. Leveraging Express.js for building a CMS allows us to quickly prototype, develop, and deploy web applications with scalable backend infrastructure.

## Getting Started

To get started, make sure you have Node.js installed on your machine. This will include npm, the package manager for Node.js. 

### Setting Up the Project

1. Create a new directory for your project and navigate to it using the terminal or command prompt.
2. Initialize a new Node.js project by running the command `npm init` and following the instructions.
3. Install Express.js by running `npm install express`.
4. Create an `app.js` or `index.js` file and require Express.js:

```javascript
const express = require('express');
const app = express();
```

### Creating Routes

Routing is an essential part of building a CMS. It allows us to handle different URL paths and execute specific actions based on them. Let's create a basic route example:

```javascript
app.get('/', (req, res) => {
  res.send('Hello, CMS!');
});

app.get('/posts', (req, res) => {
  res.send('All Posts');
});
```

### Templating Engine

To dynamically render web pages, we need to employ a templating engine. [Pug](https://pugjs.org/) (formerly known as Jade) is a popular choice. 

1. Install Pug by running `npm install pug`.

2. Set the view engine to Pug in your Express application:

```javascript
app.set('view engine', 'pug');
```

3. Create a `views` directory and add a `layout.pug` file with the basic structure of your website:

```pug
html
  head
    title My CMS
  body
    block content
```

### Creating Views

Next, let's create our first view file, `index.pug`, which will display the homepage:

```pug
extends layout

block content
  h1 Welcome to the CMS!
  p This is the homepage.
```

### Serving Static Files

In a CMS, we often need to serve static files like stylesheets, images, or JavaScript files. Express.js provides a built-in middleware for this purpose. To serve static files from a `public` directory, add the following line:

```javascript
app.use(express.static('public'));
```

### Running the Application

To start the Express.js server and run the CMS, add the following code at the end of your `app.js` or `index.js` file:

```javascript
const port = 3000;
app.listen(port, () => {
  console.log(`CMS is running on http://localhost:${port}`);
});
```

Save all the changes and run the application using the command `node app.js` or `node index.js`. Open your browser and visit http://localhost:3000 to see the CMS homepage.

## Conclusion

In this blog post, we learned how to build a CMS using Express.js. We touched upon setting up the project, creating routes, using a templating engine, serving static files, and running the application. With Express.js, you can create a powerful and scalable CMS to manage and deliver content in a dynamic and efficient way.

#Express #CMS