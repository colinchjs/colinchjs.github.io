---
layout: post
title: "Using Morgan for real-time logging in Node.js"
description: " "
date: 2023-10-01
tags: [Node, logging]
comments: true
share: true
---

Logging is an essential part of any application as it helps developers troubleshoot issues and gain insights into the application's behavior. In Node.js, one popular logging library is Morgan. Morgan is a middleware that allows you to log HTTP requests in real-time, making it easier to monitor and debug your application. In this article, we will explore how to use Morgan for real-time logging in Node.js.

## Installing Morgan
To get started, you need to install Morgan in your Node.js project. You can do this by running the following command in your terminal:

```bash
npm install morgan
```

## Setting up Morgan
Once you have Morgan installed, you can start using it in your Node.js application. To use Morgan as a middleware, you need to require it and attach it to your Express app. Here's an example:

```javascript
const express = require('express');
const morgan = require('morgan');

const app = express();

app.use(morgan('dev'));

// Rest of your application code
```

In the example above, we required both Express and Morgan, then we created an instance of the Express app. Next, we attached Morgan to our app using the `app.use` method, passing `'dev'` as the parameter. The `'dev'` parameter is one of the pre-defined logging formats provided by Morgan. Alternatively, you can specify a custom format by passing a function to `morgan`.

## Running and Testing
With Morgan set up in your application, you can now run and test it. Start your Node.js server, and you should see the HTTP requests being logged to your console in real-time. Each log entry will include the HTTP method, URL, response status code, response time, and more.

You can also customize the logging output by using the various options provided by Morgan, such as the logging format and output destination. Refer to the [Morgan documentation](https://github.com/expressjs/morgan) for more details on the available options.

## Conclusion
In this article, we explored how to use Morgan for real-time logging in a Node.js application. Morgan simplifies the process of logging HTTP requests, providing valuable insights into your application's behavior. By utilizing Morgan's customizable options, you can tailor the logging output to fit your specific needs. Give Morgan a try in your Node.js projects and enhance your debugging capabilities.

#Node.js #logging