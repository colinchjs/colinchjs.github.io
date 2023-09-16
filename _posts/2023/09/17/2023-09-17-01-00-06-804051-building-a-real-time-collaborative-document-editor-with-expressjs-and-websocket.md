---
layout: post
title: "Building a real-time collaborative document editor with Express.js and WebSocket"
description: " "
date: 2023-09-17
tags: [ExpressJS, WebSocket]
comments: true
share: true
---

In today's connected world, collaboration has become an essential part of our work. Real-time collaborative document editors allow multiple users to work together on a single document simultaneously. In this blog post, we will explore how to build a real-time collaborative document editor using Express.js and WebSocket.

## Prerequisites

Before we get started, ensure that you have the following installed on your machine:

- Node.js and npm
- Express.js

## Setting up the project

1. Create a new directory for your project.

```
mkdir document-editor
cd document-editor
```

2. Initialize a new npm project.

```
npm init -y
```

3. Install required dependencies.

```
npm install express ws
```

## Creating the server

1. Create a new file called `server.js` and require the necessary dependencies.

```javascript
const express = require('express');
const WebSocket = require('ws');
```

2. Create an Express.js app and define a route to serve the document editor HTML page.

```javascript
const app = express();

app.get('/', (req, res) => {
  res.sendFile(__dirname + '/index.html');
});
```

3. Create a WebSocket server and attach it to the Express.js server.

```javascript
const server = app.listen(3000, () => {
  console.log('Server is running on http://localhost:3000');
});

const wss = new WebSocket.Server({ server });
```

4. Define WebSocket event listeners to handle client connections and messages.

```javascript
wss.on('connection', (ws) => {
  console.log('New client connected');

  ws.on('message', (message) => {
    console.log('Received message:', message);

    // Handle incoming messages from clients
  });
});
```

5. Start the server.

```javascript
app.listen(3000, () => {
  console.log('Server is running on http://localhost:3000');
});
```

## Building the client-side

1. Create a new HTML file called `index.html` and include the following code:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Real-time Document Editor</title>
  </head>
  <body>
    <textarea id="document-editor"></textarea>

    <script>
      const socket = new WebSocket('ws://localhost:3000');

      socket.onopen = () => {
        console.log('Connected to server');
        // Send a message to the server to identify the user
      };

      socket.onmessage = (event) => {
        console.log('Received message:', event.data);
        // Handle incoming messages from the server
      };

      const documentEditor = document.getElementById('document-editor');

      documentEditor.addEventListener('input', (event) => {
        const content = event.target.value;
        // Send the updated document content to the server
      });
    </script>
  </body>
</html>
```

## Collaborative editing

To implement collaborative editing functionality, you would need to handle various scenarios such as syncing the document content among clients, handling concurrent edits, and resolving conflicts.

You can store the document content on the server and broadcast any document changes to all connected clients. Clients can update their local document content whenever they receive a new message from the server.

The exact implementation details will depend on your specific use case and requirements.

## Conclusion

In this blog post, we learned how to build a real-time collaborative document editor using Express.js for the server-side and WebSocket for real-time communication. Collaborative editing allows users to work together seamlessly on a single document, improving productivity and fostering collaboration.

#ExpressJS #WebSocket