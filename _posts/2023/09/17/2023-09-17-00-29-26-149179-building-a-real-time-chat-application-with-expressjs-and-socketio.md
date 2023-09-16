---
layout: post
title: "Building a real-time chat application with Express.js and Socket.IO"
description: " "
date: 2023-09-17
tags: [ExpressJS, SocketIO]
comments: true
share: true
---

In this tutorial, we will walk through the process of building a real-time chat application using Express.js and Socket.IO. Socket.IO is a JavaScript library that enables real-time, bidirectional and event-based communication between the browser and the server. Express.js is a fast and minimal web application framework for Node.js.

## Prerequisites

Before we start, make sure you have the following prerequisites installed on your machine:

* Node.js and npm
* Express.js
* Socket.IO

## Setting up the project

1. Create a new directory for your project and navigate into it:

```shell
$ mkdir chat-app
$ cd chat-app
```

2. Initialize a new Node.js project:

```shell
$ npm init -y
```

3. Install Express.js and Socket.IO:

```shell
$ npm install express socket.io
```

## Creating the server

1. Create a new file named `server.js` and open it in your preferred code editor.

2. Import the required packages:

```javascript
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
```

3. Create an Express.js app and a server instance:

```javascript
const app = express();
const server = http.createServer(app);
const io = socketIO(server);
```

4. Set up the server to listen on a specific port:

```javascript
const PORT = 3000;

server.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

## Adding real-time chat functionality with Socket.IO

1. Inside the `io.on('connection', (socket) => {})` event listener, handle the `message` event when a new message is received:

```javascript
io.on('connection', (socket) => {
  socket.on('message', (data) => {
    // Handle the received message
  });
});
```

2. Emit the `message` event to all connected clients when a new message is received:

```javascript
io.on('connection', (socket) => {
  socket.on('message', (data) => {
    io.emit('message', data);
  });
});
```

3. Handle the `message` event on the client-side using JavaScript:

```javascript
const socket = io();

socket.on('message', (data) => {
  // Handle the received message
});
```

4. Emit a `message` event when the user sends a new message from the client-side:

```javascript
const socket = io();
const messageInput = document.getElementById('message-input');

messageInput.addEventListener('keypress', (event) => {
  if (event.key === 'Enter') {
    const message = event.target.value;
    socket.emit('message', message);
    event.target.value = '';
  }
});
```

## Testing the chat application

1. Start the server:

```shell
$ node server.js
```

2. Open your browser and navigate to `http://localhost:3000`. You should see a chat interface.

3. Open multiple browser tabs and start sending messages. The messages should be displayed in real-time on all connected tabs.

## Conclusion

In this tutorial, we have built a real-time chat application using Express.js and Socket.IO. Socket.IO allows us to create real-time, bidirectional communication between the browser and the server, making it perfect for building chat applications. Express.js provides a robust and efficient framework for building the server-side of the application.

#ExpressJS #SocketIO