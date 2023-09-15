---
layout: post
title: "Implementing WebSocket-based chat application in JavaScript"
description: " "
date: 2023-09-15
tags: [websockets, chatapplication]
comments: true
share: true
---

In today's era of real-time communication, WebSocket has become a popular choice for building chat applications. WebSocket is a communication protocol that provides full-duplex communication channels over a single TCP connection, allowing for efficient and low-latency communication.

In this blog post, we will walk you through the process of implementing a WebSocket-based chat application in JavaScript. Let's get started!

## Prerequisites

To follow along with this tutorial, you will need the following:

- Basic knowledge of JavaScript
- Any modern web browser that supports WebSocket

## Step 1: Setting up the project

Create a new directory for your project and navigate to it in the command line. Then, initialize a new npm project by running the following command:

```
npm init -y
```

## Step 2: Installing dependencies

Next, we need to install the `express` and `ws` packages. `express` is a popular web framework for Node.js, and `ws` is a WebSocket library.

```
npm install express ws
```

## Step 3: Creating the server

In your project directory, create a new file `server.js` and add the following code:

```javascript
const express = require('express');
const http = require('http');
const WebSocket = require('ws');

const app = express();
const server = http.createServer(app);
const wss = new WebSocket.Server({ server });

wss.on('connection', (ws) => {
  ws.on('message', (message) => {
    // Handle incoming message from clients
    console.log(`Received message: ${message}`);
    
    // Broadcast the message to all clients
    wss.clients.forEach(client => {
      if (client !== ws && client.readyState === WebSocket.OPEN) {
        client.send(message);
      }
    });
  });
});

server.listen(3000, () => {
  console.log('Server started on port 3000');
});
```

## Step 4: Creating the client-side HTML

Create a new file `index.html` in your project directory and add the following code:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>WebSocket Chat</title>
  </head>
  <body>
    <h1>WebSocket Chat</h1>
    <div id="messages"></div>
    <input type="text" id="messageInput" placeholder="Enter your message" />
    <button onclick="sendMessage()">Send</button>

    <script>
      const socket = new WebSocket('ws://localhost:3000');

      socket.onmessage = (event) => {
        // Handle incoming message from server
        const message = event.data;
        const messagesContainer = document.getElementById('messages');
        messagesContainer.innerHTML += `<p>${message}</p>`;
      };

      function sendMessage() {
        // Send message to server
        const input = document.getElementById('messageInput');
        const message = input.value;
        socket.send(message);
        input.value = '';
      }
    </script>
  </body>
</html>
```

## Step 5: Starting the server

In the command line, run the following command to start the server:

```
node server.js
```

## Step 6: Testing the application

Open your web browser and navigate to `http://localhost:3000`. You should see a simple chat interface with an input field and a send button. Enter a message and click the send button. The message will be displayed on the page and broadcasted to all connected clients.

You can open multiple browser tabs or windows and test the chat application by sending messages between different clients.

## Conclusion

Congratulations! You have successfully implemented a WebSocket-based chat application in JavaScript. WebSocket provides a powerful mechanism for real-time communication between client and server, making it ideal for building chat applications and other interactive web experiences.

#websockets #chatapplication