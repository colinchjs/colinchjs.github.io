---
layout: post
title: "Building a multi-room chat application with Express.js and Socket.IO"
description: " "
date: 2023-09-17
tags: [chat, room, message, input, message, send, chatapplication, expressjs, socketio]
comments: true
share: true
---

In this tutorial, we will explore how to build a real-time multi-room chat application using Express.js and Socket.IO. With Socket.IO, we can create web applications that support bidirectional, event-driven communication between the client and the server.

## Prerequisites

To follow along with this tutorial, you need to have the following:

- Node.js installed on your machine
- A basic understanding of JavaScript and web development concepts

## Setting Up the Project

1. Create a new directory for your project and navigate into it.
2. Initialize a new Node.js project using the following command:

```bash
$ npm init -y
```

3. Install the necessary dependencies by running the following command:

```bash
$ npm install express socket.io
```

## Building the Server

1. Create a new file called `server.js` and open it in your favorite code editor.
2. Import the required modules:

```javascript
const express = require('express');
const http = require('http');
const socketIO = require('socket.io');
```

3. Create an instance of Express.js and initialize a server:

```javascript
const app = express();
const server = http.createServer(app);
```

4. Create an instance of Socket.IO:

```javascript
const io = socketIO(server);
```

5. Set up the route for serving the client-side files:

```javascript
app.use(express.static(__dirname + '/public'));
```

6. Set up the event handlers for when a client connects and disconnects:

```javascript
io.on('connection', (socket) => {
  console.log('A user connected');

  socket.on('disconnect', () => {
    console.log('A user disconnected');
  });
});
```

7. Start the server:

```javascript
const PORT = process.env.PORT || 3000;

server.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

## Implementing the Chat Functionality

1. Create a new folder called `public` in your project directory.
2. Inside the `public` folder, create `index.html` and `style.css` files.
3. Open `index.html` and add the following content:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Multi-Room Chat Application</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div id="chat-container">
    <div id="room-list">
      <h2>Rooms</h2>
      <ul id="rooms"></ul>
    </div>
  
    <div id="message-container">
      <h2>Messages</h2>
      <ul id="messages"></ul>
    </div>
  
    <div id="input-container">
      <input type="text" id="message-input" placeholder="Type your message...">
      <button id="send-button">Send</button>
    </div>
  </div>

  <script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/4.4.1/socket.io.js"></script>
  <script src="script.js"></script>
</body>
</html>
```

4. Open `style.css` and add the following styles:

```css
body {
  margin: 0;
  padding: 0;
  font-family: Arial, sans-serif;
}

#chat-container {
  display: flex;
  height: 100vh;
}

#room-list, #message-container {
  flex: 1;
  border-right: 1px solid #ccc;
  padding: 10px;
}

#input-container {
  display: flex;
  align-items: center;
  padding: 10px;
  border-top: 1px solid #ccc;
}

#message-input {
  flex: 1;
  margin-right: 10px;
  padding: 5px;
}

#send-button {
  padding: 5px 10px;
}
```

5. Create a new file called `script.js` inside the `public` folder.
6. Open `script.js` and add the following JavaScript code:

```javascript
const socket = io();

const roomsContainer = document.getElementById('rooms');
const messagesContainer = document.getElementById('messages');
const messageInput = document.getElementById('message-input');
const sendButton = document.getElementById('send-button');

socket.on('connect', () => {
  const username = prompt('Enter your username:');
  socket.emit('setUsername', username);
});

socket.on('roomList', (rooms) => {
  roomsContainer.innerHTML = '';

  rooms.forEach((room) => {
    const li = document.createElement('li');
    li.innerText = room;
    li.addEventListener('click', () => {
      socket.emit('joinRoom', room);
    });
    roomsContainer.appendChild(li);
  });
});

socket.on('message', (message) => {
  const li = document.createElement('li');
  li.innerText = message;
  messagesContainer.appendChild(li);
});

sendButton.addEventListener('click', () => {
  const message = messageInput.value;
  if (message) {
    socket.emit('sendMessage', message);
    messageInput.value = '';
  }
});
```

7. Finally, start the server by running the following command:

```bash
$ node server.js
```

## Conclusion

In this tutorial, we have built the foundation of a multi-room chat application using Express.js and Socket.IO. Socket.IO allows us to establish real-time, bidirectional communication between the client and the server, enabling seamless chat functionality. From here, you can expand the application by adding user authentication, implementing private messaging, and enhancing the user interface.

Don't forget to follow us for more exciting tutorials! #chatapplication #expressjs #socketio