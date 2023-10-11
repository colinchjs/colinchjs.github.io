---
layout: post
title: "Creating a custom useOnlineStatusEffect hook for handling side effects based on online/offline status"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In modern web applications, it is often necessary to handle side effects based on the user's online/offline status. This can be particularly useful in scenarios where the application needs to synchronize data with a server, display notifications, or trigger certain actions when the user goes offline or comes back online.

In this blog post, we will walk through how to create a custom React hook called `useOnlineStatusEffect` that encapsulates the logic for handling these side effects based on the user's online/offline status.

## Table of Contents
- [What is a Custom Hook?](#what-is-a-custom-hook)
- [Understanding the `navigator.onLine` API](#understanding-the-navigatoronline-api)
- [Creating the `useOnlineStatusEffect` Hook](#creating-the-useonlinestatuseffect-hook)
- [Using the `useOnlineStatusEffect` Hook](#using-the-useonlinestatuseffect-hook)
- [Conclusion](#conclusion)

## What is a Custom Hook?

Custom hooks in React allow us to encapsulate reusable logic that can be shared across different components. They follow a specific naming convention by prefixing the function name with `use`, enabling them to leverage features such as state and lifecycle methods.

## Understanding the `navigator.onLine` API

The `navigator.onLine` property is a boolean that indicates whether the user agent is online or offline. It can be accessed using the `navigator.onLine` global variable in JavaScript.

### Example:

```javascript
if (navigator.onLine) {
  console.log("User is online");
} else {
  console.log("User is offline");
}
```

## Creating the `useOnlineStatusEffect` Hook

Let's create the `useOnlineStatusEffect` hook that captures the user's online/offline status and executes a given callback function when it changes.

```javascript
import { useEffect } from 'react';

const useOnlineStatusEffect = (callback) => {
  useEffect(() => {
    const handleStatusChange = () => {
      callback(navigator.onLine);
    };

    window.addEventListener('online', handleStatusChange);
    window.addEventListener('offline', handleStatusChange);

    return () => {
      window.removeEventListener('online', handleStatusChange);
      window.removeEventListener('offline', handleStatusChange);
    };
  }, [callback]);
};

export default useOnlineStatusEffect;
```

In the above code, we're using the `useEffect` hook to add event listeners for the `online` and `offline` events. When the event occurs, `callback(navigator.onLine)` is executed, passing the current online status to the callback function.

It's important to note that we're returning a cleanup function in the `useEffect` hook to remove the event listeners when the component using this hook is unmounted.

## Using the `useOnlineStatusEffect` Hook

To use the `useOnlineStatusEffect` hook, you simply need to import it and invoke it within a functional component. Here's an example of how you might use this hook in a component:

```javascript
import React from 'react';
import useOnlineStatusEffect from './useOnlineStatusEffect';

const App = () => {
  const handleOnlineStatusChange = (isOnline) => {
    if (isOnline) {
      console.log("You are online");
      // Perform actions specific to being online
    } else {
      console.log("You are offline");
      // Perform actions specific to being offline
    }
  };

  useOnlineStatusEffect(handleOnlineStatusChange);

  return (
    <div>
      {/* Your application content */}
    </div>
  );
};

export default App;
```

In the above example, we define a callback function `handleOnlineStatusChange` that takes the current `isOnline` status as an argument. We then invoke the `useOnlineStatusEffect` hook inside the `App` component, passing in our callback function.

Now, whenever the user's online/offline status changes, the `handleOnlineStatusChange` function will be called with the updated status.

## Conclusion

In this blog post, we've learned how to create a custom `useOnlineStatusEffect` hook that allows us to handle side effects based on the user's online/offline status. This hook improves code reusability, making it easier to manage server synchronization, notifications, and other actions in a more efficient and declarative manner. By leveraging custom hooks, we can write cleaner and more maintainable code in our React applications.