---
layout: post
title: "React.js real-time chat applications with Socket.io"
description: " "
date: 2023-09-25
tags: [ReactJS, SocketIO]
comments: true
share: true
---

In this blog post, we will explore how to build a real-time chat application using React.js and Socket.io. Real-time chat applications have become incredibly popular, allowing users to communicate with each other instantly. React.js is a powerful JavaScript library for building user interfaces, and Socket.io is a JavaScript library that enables real-time, bidirectional communication between clients and servers.

## Setting up the project

To get started, make sure you have Node.js installed on your machine. Then, create a new directory for your project and navigate to it in your terminal.

**Step 1:** Initialize a new Node.js project by running the following command:
```
npm init -y
```

**Step 2:** Install the necessary dependencies:
```
npm install react socket.io express
```

## Creating the server

Let's begin by setting up the backend server using Express and Socket.io.

**Step 1:** Create a new file called `server.js` and add the following code:

```javascript
const express = require('express');
const socketIO = require('socket.io');
const http = require('http');

const app = express();
const server = http.createServer(app);
const io = socketIO(server);

// Handle socket connection
io.on('connection', (socket) => {
  console.log('User connected');
  
  // Handle incoming messages
  socket.on('chat message', (message) => {
    console.log('Message received:', message);
  
    // Broadcast the message to all connected clients
    io.emit('chat message', message);
  });
  
  // Handle disconnection
  socket.on('disconnect', () => {
    console.log('User disconnected');
  });
});

// Start the server
const port = process.env.PORT || 3000;
server.listen(port, () => {
  console.log(`Server listening on port ${port}`);
});
```

**Step 2:** Start the server by running `node server.js`. You should see the message "Server listening on port 3000" in the console.

## Building the React.js client

**Step 1:** Create a new file called `Chat.js` and add the following React component code:

```javascript
import React, { useState, useEffect } from 'react';
import io from 'socket.io-client';

const socket = io('http://localhost:3000');

const Chat = () => {
  const [message, setMessage] = useState('');
  const [messages, setMessages] = useState([]);

  useEffect(() => {
    // Listen for incoming messages
    socket.on('chat message', (message) => {
      setMessages((prevMessages) => [...prevMessages, message]);
    });

    return () => {
      // Clean up socket connection on component unmount
      socket.disconnect();
    };
  }, []);

  const handleSendMessage = (e) => {
    e.preventDefault();

    // Send message to the server
    socket.emit('chat message', message);

    setMessage('');
  };

  return (
    <div>
      <div>
        {messages.map((message, index) => (
          <div key={index}>{message}</div>
        ))}
      </div>
      <form onSubmit={handleSendMessage}>
        <input
          type="text"
          value={message}
          onChange={(e) => setMessage(e.target.value)}
        />
        <button type="submit">Send</button>
      </form>
    </div>
  );
};

export default Chat;
```

**Step 2:** Use the `Chat` component in your main React app component or wherever you want to display the chat interface.

```javascript
import React from 'react';
import Chat from './Chat';

const App = () => {
  return (
    <div>
      <h1>Real-Time Chat</h1>
      <Chat />
    </div>
  );
}

export default App;
```

## Testing the Application

To test the application, open two or more browser tabs and navigate to `http://localhost:3000`. Each tab represents a connected user, and any messages sent will be displayed in real-time across all connected clients.

That's it! You've successfully built a real-time chat application using React.js and Socket.io. Feel free to enhance the app by adding more features such as user authentication or message timestamps.

#ReactJS #SocketIO