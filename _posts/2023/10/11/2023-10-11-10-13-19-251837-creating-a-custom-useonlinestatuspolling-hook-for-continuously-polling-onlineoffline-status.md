---
layout: post
title: "Creating a custom useOnlineStatusPolling hook for continuously polling online/offline status"
description: " "
date: 2023-10-11
tags: [React, CustomHook]
comments: true
share: true
---

In modern web applications, it's often important to know whether a user is currently online or offline. While some browsers provide native APIs to detect online status changes, they may not cover all scenarios or provide real-time updates.

In this blog post, we'll explore how to create a custom React hook called `useOnlineStatusPolling` using the `navigator.onLine` API to continuously poll the online/offline status of a user.

## Table of Contents
1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Creating the `useOnlineStatusPolling` Hook](#creating-the-useonlinestatuspolling-hook)
4. [Using the `useOnlineStatusPolling` Hook](#using-the-useonlinestatuspolling-hook)
5. [Conclusion](#conclusion)
6. [Additional Resources](#additional-resources)
7. [Hashtags](#hashtags)

## Introduction <a name="introduction"></a>

The `navigator.onLine` property provides a quick and synchronous way to check if a user is currently online or offline in most modern browsers. However, it doesn't offer real-time updates as it only reflects the status when the page was last loaded.

To continuously monitor the online/offline status, we can create a custom React hook that periodically checks the `navigator.onLine` status and updates its state accordingly.

## Prerequisites <a name="prerequisites"></a>

Before we proceed, make sure you have the following:

- Basic knowledge of React JavaScript library.
- Node.js and npm (Node Package Manager) installed on your machine.

Let's get started by creating the `useOnlineStatusPolling` hook.

## Creating the `useOnlineStatusPolling` Hook <a name="creating-the-useonlinestatuspolling-hook"></a>

Start by creating a new file `useOnlineStatusPolling.js` and add the following code:

```javascript
import React, { useEffect, useState } from 'react';

const useOnlineStatusPolling = (interval = 1000) => {
  const [isOnline, setIsOnline] = useState(navigator.onLine);

  useEffect(() => {
    const checkOnlineStatus = () => {
      setIsOnline(navigator.onLine);
    }

    const intervalId = setInterval(checkOnlineStatus, interval);

    // Cleanup the interval on component unmount
    return () => {
      clearInterval(intervalId);
    }
  }, [interval]);

  return isOnline;
}

export default useOnlineStatusPolling;
```

Let's break down the code:

- We import the required dependencies from React: `useEffect` and `useState`.
- The `useOnlineStatusPolling` hook accepts an optional `interval` parameter to determine the polling interval. The default interval is set to 1000ms (1 second).
- Inside the hook, we create a state variable `isOnline` using the `useState` hook and initialize it with the value of `navigator.onLine`.
- In the `useEffect` hook, we set up an interval using `setInterval` to periodically check the online status by updating the `isOnline` state variable.
- Upon component unmount, we clean up the interval using `clearInterval`.
- Finally, we return the `isOnline` state variable from the hook.

Now that we have our custom hook, let's see how to use it.

## Using the `useOnlineStatusPolling` Hook <a name="using-the-useonlinestatuspolling-hook"></a>

To use the `useOnlineStatusPolling` hook in your React component, follow these steps:

1. Import the hook:
    ```javascript
    import useOnlineStatusPolling from './useOnlineStatusPolling';
    ```

2. Use it inside your component:
    ```javascript
    function MyComponent() {
      const isOnline = useOnlineStatusPolling();

      return (
        <div>
          <h1>My Component</h1>
          <p>Status: {isOnline ? 'Online' : 'Offline'}</p>
        </div>
      );
    }
    ```

In the example above, we use the `isOnline` state variable returned from the `useOnlineStatusPolling` hook to render the current status as either "Online" or "Offline".

Now, whenever the online/offline status changes, the `isOnline` variable will be updated, triggering a re-render of the component.

## Conclusion <a name="conclusion"></a>

Creating a custom React hook like `useOnlineStatusPolling` allows us to continuously monitor the online/offline status of a user, providing real-time updates and flexibility in handling online/offline scenarios.

Feel free to modify the polling interval according to your application's requirements to achieve the desired balance between real-time updates and resource consumption.

## Additional Resources <a name="additional-resources"></a>

- [React Hooks Documentation](https://reactjs.org/docs/hooks-intro.html)

## Hashtags <a name="hashtags"></a>
#React #CustomHook