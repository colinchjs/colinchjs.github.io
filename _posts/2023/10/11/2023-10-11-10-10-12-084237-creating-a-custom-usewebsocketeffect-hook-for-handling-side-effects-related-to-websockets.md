---
layout: post
title: "Creating a custom useWebsocketEffect hook for handling side effects related to WebSockets"
description: " "
date: 2023-10-11
tags: [React, WebSockets]
comments: true
share: true
---

WebSockets are a powerful way to establish a bidirectional communication channel between a client and a server. To handle side effects related to WebSockets in a React application, we can create a custom hook called `useWebsocketEffect`. This hook will encapsulate the necessary logic to establish a WebSocket connection, handle incoming messages, and clean up the connection when needed.

Let's dive into the implementation of the `useWebsocketEffect` hook:

```jsx
import { useEffect } from 'react';

const useWebsocketEffect = (url, onMessageReceived) => {
  useEffect(() => {
    const socket = new WebSocket(url);

    socket.addEventListener('message', (event) => {
      onMessageReceived(event.data);
    });

    return () => {
      socket.close();
    };
  }, [url, onMessageReceived]);
};

export default useWebsocketEffect;
```

Here's a breakdown of the code:

1. We import the `useEffect` hook from the React library.
2. The `useWebsocketEffect` hook takes two parameters: `url` (the WebSocket server URL) and `onMessageReceived` (a callback function to handle incoming messages).
3. Inside the hook, we call `useEffect` and provide a callback function as the first parameter. This callback function will be executed when the component mounts or when the `url` or `onMessageReceived` dependencies change.
4. Inside the `useEffect` callback function, we create a new WebSocket instance using the provided `url`.
5. We add an event listener to the WebSocket instance to handle incoming messages. When a message is received, we call the `onMessageReceived` callback with the message data.
6. Finally, we return a cleanup function that will be executed when the component unmounts. This cleanup function closes the WebSocket connection.

To use the `useWebsocketEffect` hook in a React component, we can write code like this:

```jsx
import React, { useState } from 'react';
import useWebsocketEffect from './useWebsocketEffect';

const WebSocketComponent = () => {
  const [message, setMessage] = useState('');

  const handleIncomingMessage = (data) => {
    setMessage(data);
  };

  useWebsocketEffect('wss://example.com', handleIncomingMessage);

  return (
    <div>
      <p>{message}</p>
    </div>
  );
};

export default WebSocketComponent;
```

In the above example, we use the `useState` hook to manage the state of `message`. The `handleIncomingMessage` function updates the state with the received message. We then pass the `handleIncomingMessage` function to the `useWebsocketEffect` hook along with the WebSocket server URL.

By using the `useWebsocketEffect` hook, we can easily handle side effects related to WebSockets in a reusable and declarative manner within our React components.

<!--hashtags-->
#React #WebSockets