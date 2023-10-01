---
layout: post
title: "Logging WebSocket events in real-time with Node.js"
description: " "
date: 2023-10-01
tags: [WebSocket, NodeJS]
comments: true
share: true
---

## Setup

Before we dive into logging WebSocket events, let's set up a basic WebSocket server using the `ws` library in Node.js. Open your favorite terminal and follow these steps:

1. Create a new directory for your project:
   ```bash
   mkdir websocket-logger
   cd websocket-logger
   ```

2. Initialize a new Node.js project and install the `ws` package:
   ```bash
   npm init -y
   npm install ws
   ```

3. Create a new file called `server.js` and add the following code:

   ```javascript
   const WebSocket = require('ws');

   const wss = new WebSocket.Server({ port: 8080 });

   wss.on('connection', (ws) => {
     ws.on('message', (message) => {
       console.log('Received message:', message);
     });

     ws.on('close', () => {
       console.log('WebSocket connection closed');
     });
   });
   ```

4. Run the server:
   ```bash
   node server.js
   ```

Now we have a WebSocket server listening on port 8080. Any messages received will be logged to the console.

## Logging WebSocket Events

To log WebSocket events in real-time, we can modify the server code to listen for additional event types. Let's add logging for the `open` and `error` events.

```javascript
const WebSocket = require('ws');

const wss = new WebSocket.Server({ port: 8080 });

wss.on('connection', (ws) => {
  ws.on('message', (message) => {
    console.log('Received message:', message);
  });

  ws.on('close', () => {
    console.log('WebSocket connection closed');
  });

  ws.on('open', () => {
    console.log('WebSocket connection opened');
  });

  ws.on('error', (error) => {
    console.error('WebSocket error:', error);
  });
});
```

With these additional event handlers, we can now log the `open` and `error` events along with the existing `message` and `close` events.

## Real-time Logging

To view the WebSocket events in real-time, we can use a logging library like `winston` and configure it to log to a file. Here's how to set it up:

1. Install `winston` as a dependency:
   ```bash
   npm install winston
   ```

2. Update the `server.js` file:

   ```javascript
   const WebSocket = require('ws');
   const winston = require('winston');

   const logger = winston.createLogger({
     transports: [
       new winston.transports.File({ filename: 'websocket.log' }),
     ],
   });

   const wss = new WebSocket.Server({ port: 8080 });

   wss.on('connection', (ws) => {
     ws.on('message', (message) => {
       logger.info('Received message:', message);
     });

     ws.on('close', () => {
       logger.info('WebSocket connection closed');
     });

     ws.on('open', () => {
       logger.info('WebSocket connection opened');
     });

     ws.on('error', (error) => {
       logger.error('WebSocket error:', error);
     });
   });
   ```

3. Run the server again:
   ```bash
   node server.js
   ```

Now, every WebSocket event will be logged to the `websocket.log` file in real-time.

## Conclusion

Logging WebSocket events in real-time is crucial for monitoring and debugging WebSocket connections. By listening to the `open`, `message`, `close`, and `error` events, we can log important information about the connection. Additionally, using a logging library like `winston` allows us to store the logs and analyze them later if needed.

Start logging your WebSocket events today and gain valuable insights into your real-time communication system.

#WebSocket #NodeJS