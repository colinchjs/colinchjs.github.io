---
layout: post
title: "Using WebSockets in Express.js for real-time communication"
description: " "
date: 2023-09-17
tags: [WebSockets, Express]
comments: true
share: true
---

WebSockets are a powerful technology that enables real-time, bidirectional communication between clients and servers. With the help of WebSockets, you can create applications that can push data from the server to the clients instantly, eliminating the need for traditional request-response cycles.

In this blog post, we'll explore how to use WebSockets in Express.js, a popular web framework for Node.js, to enable real-time communication in your applications.

## Prerequisites

Before we dive into the implementation, make sure you have the following prerequisites in place:

1. Node.js and npm installed on your machine
2. Basic knowledge of JavaScript and Express.js

## Getting Started

To use WebSockets in Express.js, we'll start by installing the `express-ws` package. Open your terminal and run the following command:

```shell
npm install express-ws
```

Next, let's create a basic Express.js server that includes WebSocket support. Create a new file, `server.js`, and add the following code:

```javascript
const express = require('express');
const expressWs = require('express-ws');

// Create an Express app
const app = express();
const wsInstance = expressWs(app);

// Handle WebSocket connections
app.ws('/websocket', (ws, req) => {
  // WebSocket connection established
  console.log('WebSocket connection established');

  // Handle incoming messages
  ws.on('message', (message) => {
    console.log('Received message:', message);

    // Send a response back to the client
    ws.send('Server received: ' + message);
  });

  // Handle WebSocket disconnections
  ws.on('close', () => {
    console.log('WebSocket connection closed');
  });
});

// Start the server
app.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

In the above code, we import the `express` and `express-ws` packages, create an Express app, and initialize WebSocket support using `expressWs`. We then define a route `/websocket` for WebSocket connections. Inside the route handler, we handle incoming messages using the `message` event and send responses back to the client using the `ws.send()` method. We also handle WebSocket disconnections using the `close` event.

To start the server, run the following command in your terminal:

```shell
node server.js
```

You should see the following message in your console: `Server started on port 3000`.

## Client-Side Implementation

Now that our server is ready to handle WebSocket connections, let's create a simple HTML file to establish a WebSocket connection and exchange messages with the server. Create a new file, `index.html`, and add the following code:

```html
<!DOCTYPE html>
<html>
<head>
  <title>WebSocket Example</title>
  <script>
    // Establish WebSocket connection
    const ws = new WebSocket('ws://localhost:3000/websocket');

    // WebSocket connection opened
    ws.onopen = () => {
      console.log('WebSocket connection opened');
    };

    // Handle incoming messages
    ws.onmessage = (event) => {
      const message = event.data;
      console.log('Received message:', message);
    };

    // Send a message to the server
    const sendButton = document.getElementById('sendButton');
    sendButton.addEventListener('click', () => {
      const messageInput = document.getElementById('messageInput');
      const message = messageInput.value;

      ws.send(message);
    });
  </script>
</head>
<body>
  <input type="text" id="messageInput" placeholder="Enter a message">
  <button id="sendButton">Send</button>
</body>
</html>
```

In the above code, we create a WebSocket connection using the URL `ws://localhost:3000/websocket`, which matches the route we defined on the server-side. We listen for the `open` event to be notified when the connection is established. Incoming messages are handled using the `message` event, and we log the received message in the console. We also add an input field and a button to send messages to the server.

To test the WebSocket communication, open the `index.html` file in your browser. Open the browser's developer console to view the log messages. Enter a message in the input field and click the "Send" button. You should see the message logged in both the server and client consoles.

Congratulations! You have successfully implemented a basic WebSocket communication using Express.js.

## Conclusion

In this blog post, we explored how to use WebSockets in Express.js for real-time communication. We covered the installation of the `express-ws` package, setting up the server-side implementation, and creating a basic client-side interface to connect with the server.

WebSockets open up endless possibilities for real-time applications such as chat systems, collaborative editing tools, and live dashboards. With the power of Express.js and WebSockets, you can create highly interactive and responsive applications that deliver data in real-time.

#WebSockets #Express.js