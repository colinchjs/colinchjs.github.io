---
layout: post
title: "Implementing real-time logging with Elastic APM in Node.js applications"
description: " "
date: 2023-10-01
tags: [nodejs, elasticapm]
comments: true
share: true
---

In today's world of distributed systems, it is crucial to have visibility into how our applications perform and behave in real-time. Logging plays a vital role in troubleshooting and monitoring these systems. Elastic APM (Application Performance Monitoring) provides a comprehensive solution for monitoring the performance of applications, including real-time logging. In this blog post, we will explore how to implement real-time logging with Elastic APM in Node.js applications.

## Prerequisites

To follow along with this tutorial, make sure you have the following prerequisites:

- Node.js installed on your machine
- Elastic APM Server and APM agents set up (optional, but recommended)

## Step 1: Setting up Elastic APM agent for Node.js

To start, we need to install the Elastic APM agent for Node.js. Open your terminal and run the following command:

```shell
npm install elastic-apm-node
```

Next, we need to require the Elastic APM agent in our application code. Add the following lines to the top of your main entry file:

```javascript
const apm = require('elastic-apm-node').start({
  // Configuration options
});
```

Replace `// Configuration options` with the appropriate configuration options if required. It is recommended to set up the APM agent with your APM server details, such as the server URL and service name.

## Step 2: Implementing real-time logging

Once we have the APM agent set up, we can start implementing real-time logging. Elastic APM agent provides a built-in logger that logs events to the APM server. To log an event, use the following code snippet:

```javascript
apm.logger.info('This is an example log message');
```

You can also log messages with different log levels such as error, debug, and warning:

```javascript
apm.logger.error('An error occurred', { custom: 'metadata' });
apm.logger.debug('Debug log message');
apm.logger.warning('Warning log message');
```

You can include additional metadata as an object in the second parameter of the log functions.

## Step 3: Configuring log levels

By default, the Elastic APM agent logs messages with the log level set to `info`. However, you can configure the log level to control which messages to log. To set the log level, add the following configuration option when starting the APM agent:

```javascript
const apm = require('elastic-apm-node').start({
  logLevel: 'error',
});
```

The available log levels are `trace`, `debug`, `info`, `warning`, and `error`. Set the desired log level as per your application's requirements.

## Conclusion

In this blog post, we explored how to implement real-time logging with Elastic APM in Node.js applications. By leveraging the Elastic APM agent, we can easily log events and monitor our application's performance in real-time. With this valuable information, we can quickly identify and resolve issues, ensuring a smooth and reliable user experience.

Start implementing real-time logging with Elastic APM in your Node.js applications today and gain better insights into your application's performance.

#nodejs #apm #elasticapm