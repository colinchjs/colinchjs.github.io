---
layout: post
title: "Implementing real-time logging with Fluentd in Node.js"
description: " "
date: 2023-10-01
tags: [tech, logging]
comments: true
share: true
---

In a modern application, logging plays a crucial role in monitoring and troubleshooting. One popular log management solution is Fluentd, which allows developers to centralize logs from various sources for analysis and visualization. In this blog post, we will explore how to implement real-time logging with Fluentd in a Node.js application.

## Prerequisites
Before we begin, make sure you have the following installed on your machine:

1. Node.js: You can download and install Node.js from https://nodejs.org.

2. Fluentd: Install Fluentd using the instructions provided in the official Fluentd documentation: https://docs.fluentd.org.

## Setting up Fluentd
1. Once Fluentd is installed, update the Fluentd configuration file (`td-agent.conf`) to define the input and output plugins.

```javascript
<source>
  @type forward
  port 24224
</source>

<match your-output-tag>
  @type stdout
</match>
```

This configuration sets up Fluentd to accept logs from the Node.js application on port 24224 and outputs them to the console.

2. Restart the Fluentd service for the changes to take effect.

## Integrating Fluentd with Node.js
To send logs from your Node.js application to Fluentd, you can use the `fluent-logger` package, which provides a client library for sending logs over TCP.

1. Install the `fluent-logger` package using npm:

```shell
npm install fluent-logger
```

2. Import the package and create a Fluentd logger instance in your Node.js application:

```javascript
const { createFluentSender } = require('fluent-logger');

const logger = createFluentSender({
  host: '<your-fluentd-host>',
  port: 24224,
  timeout: 3.0,
  reconnectInterval: 600000 // 10 minutes
});
```

Replace `<your-fluentd-host>` with the hostname or IP address of your Fluentd instance.

3. Start logging by calling the `emit` method on the logger instance:

```javascript
logger.emit('your-output-tag', {
  message: 'Sample log message',
  level: 'info',
  timestamp: new Date().toISOString()
});
```

Replace `'your-output-tag'` with the desired tag that matches the `<match>` block in the Fluentd configuration.

4. Run your Node.js application and check the Fluentd console to see the real-time logs.

## Conclusion
Logging is essential for monitoring and debugging applications, and Fluentd provides a powerful solution for centralizing logs. In this article, we explored how to implement real-time logging with Fluentd in a Node.js application. By following these steps, you can send your logs to Fluentd and have them readily available for analysis and visualization.

#tech #logging