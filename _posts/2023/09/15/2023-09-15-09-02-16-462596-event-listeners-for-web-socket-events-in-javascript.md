---
layout: post
title: "Event listeners for web socket events in JavaScript"
description: " "
date: 2023-09-15
tags: [WebSocket]
comments: true
share: true
---

WebSocket is a communication protocol that enables bidirectional communication between a client and a server over a single, long-lived connection. In JavaScript, you can handle WebSocket events by adding event listeners to your WebSocket object. This allows you to respond to different WebSocket events and perform actions based on the server's responses.

Here are some common WebSocket events and how to add event listeners for them in JavaScript:

## 1. Connecting to the WebSocket server

To connect to a WebSocket server, you need to create a new WebSocket object and pass the server's URL as an argument. You can add an event listener to the WebSocket object to handle the connection event.

```javascript
const socket = new WebSocket('ws://example.com');

socket.addEventListener('open', () => {
  console.log('Connected to the WebSocket server');
});
```

## 2. Receiving messages from the server

When the server sends a message to the client, the WebSocket object emits a `message` event. You can listen to this event and perform actions based on the received message.

```javascript
socket.addEventListener('message', (event) => {
  const message = event.data;
  console.log('Received message:', message);
  // Perform actions based on the received message
});
```

## 3. Handling connection errors

If there is an error connecting to the WebSocket server, the WebSocket object emits an `error` event. You can add an event listener to handle any connection errors.

```javascript
socket.addEventListener('error', (event) => {
  console.error('WebSocket error:', event);
  // Perform error handling logic
});
```

## 4. Closing the WebSocket connection

When you want to close the WebSocket connection, you can use the `close` method on the WebSocket object. The WebSocket object emits a `close` event when the connection is closed gracefully.

```javascript
socket.close();

socket.addEventListener('close', () => {
  console.log('WebSocket connection closed');
});
```

These are just a few examples of how to use event listeners for WebSocket events in JavaScript. By utilizing event listeners, you can handle various WebSocket events and create dynamic, real-time applications.

#JavaScript #WebSocket