---
layout: post
title: "Creating a custom useNetworkStatus hook for checking network status"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In this blog post, we will learn how to create a custom `useNetworkStatus` hook in React for checking the network status of our application. This hook will allow us to easily check whether the user is online or offline, and take appropriate actions based on the network status.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Implementing the useNetworkStatus Hook](#implementing-the-usenetworkstatus-hook)
- [Using the useNetworkStatus Hook](#using-the-usenetworkstatus-hook)
- [Conclusion](#conclusion)

## Introduction
When building web applications, it's important to handle network connectivity gracefully. By knowing the network status, we can provide a better user experience by showing appropriate messages or adapting the functionality of our application.

## Prerequisites
To follow along with this tutorial, you should have a basic understanding of React and hooks. If you are not familiar with hooks, I recommend checking out the [React Hooks documentation](https://reactjs.org/docs/hooks-intro.html) before proceeding.

## Implementing the useNetworkStatus Hook
Let's start by creating a new file named `useNetworkStatus.js`. Inside this file, we will define our custom hook.

```javascript
import { useEffect, useState } from 'react';

const useNetworkStatus = () => {
  const [isOnline, setIsOnline] = useState(navigator.onLine);

  useEffect(() => {
    const handleOnline = () => {
      setIsOnline(true);
    };

    const handleOffline = () => {
      setIsOnline(false);
    };

    window.addEventListener('online', handleOnline);
    window.addEventListener('offline', handleOffline);

    return () => {
      window.removeEventListener('online', handleOnline);
      window.removeEventListener('offline', handleOffline);
    };
  }, []);

  return isOnline;
};

export default useNetworkStatus;
```

Let's go through the implementation step by step:
1. We import the necessary hooks from React.
2. Inside our custom hook, we create a state variable `isOnline` and set its initial value based on `navigator.onLine`.
3. We use `useEffect` to add event listeners for the `'online'` and `'offline'` events. When these events occur, we update the `isOnline` state accordingly.
4. Lastly, we clean up the event listeners when the component unmounts by returning a cleanup function from `useEffect`.

## Using the useNetworkStatus Hook
Now that we have implemented our custom hook, let's see how we can use it in our components.

```javascript
import React from 'react';
import useNetworkStatus from './useNetworkStatus';

const App = () => {
  const isOnline = useNetworkStatus();

  return (
    <div>
      {isOnline ? (
        <p>You are online</p>
      ) : (
        <p>You are offline</p>
      )}
    </div>
  );
};

export default App;
```

We import the `useNetworkStatus` hook in our component and use it to get the `isOnline` status. Based on the `isOnline` value, we display appropriate messages to the user.

## Conclusion
In this tutorial, we learned how to create a custom `useNetworkStatus` hook in React for checking the network status of our application. By using this hook, we can easily handle different network conditions and provide a better user experience.