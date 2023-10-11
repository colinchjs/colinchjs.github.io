---
layout: post
title: "Creating a custom useIdleTimeout hook for implementing idle timeout logic"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In this blog post, we will explore how to create a custom React hook called `useIdleTimeout` that can be used to implement idle timeout functionality in a React application. Idle timeout refers to the concept of detecting when a user has been inactive for a certain period of time and taking some action as a result, such as logging them out or showing a timeout message.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Creating the useIdleTimeout hook](#creating-the-useidletimeout-hook)
- [Using the useIdleTimeout hook](#using-the-useidletimeout-hook)
- [Conclusion](#conclusion)

## Introduction
Idle timeout functionality is commonly required in applications where user authentication and session management are important. By implementing this functionality, you can improve the security and user experience of your application. In this blog post, we will create a custom React hook that encapsulates the logic for detecting user inactivity and triggering a callback function after a specified idle time.

## Prerequisites
To follow along with this tutorial, you should have a basic understanding of React and React hooks. You will also need a React project set up with the necessary dependencies.

## Creating the useIdleTimeout hook

```jsx
import { useState, useEffect } from 'react';

const useIdleTimeout = (idleTime, callback) => {
  const [idle, setIdle] = useState(false);

  useEffect(() => {
    let idleTimeout;

    const resetIdleTimeout = () => {
      if (idleTimeout) {
        clearTimeout(idleTimeout);
      }

      idleTimeout = setTimeout(() => {
        setIdle(true);
        callback();
      }, idleTime);
    };

    const handleActivity = () => {
      if (idle) {
        setIdle(false);
      }

      resetIdleTimeout();
    };

    window.addEventListener('mousemove', handleActivity);
    window.addEventListener('keydown', handleActivity);

    resetIdleTimeout();

    return () => {
      clearTimeout(idleTimeout);
      window.removeEventListener('mousemove', handleActivity);
      window.removeEventListener('keydown', handleActivity);
    };
  }, [idleTime, callback]);

  return idle;
};

export default useIdleTimeout;
```

The `useIdleTimeout` hook takes two parameters: `idleTime` and `callback`. `idleTime` is the amount of time (in milliseconds) after which the user is considered idle, and `callback` is the function that will be called when the idle time elapses.

Inside the hook, we use the `useState` and `useEffect` hooks from React to manage state and side effects. we maintain the `idle` state using the `useState` hook. The `idle` state variable indicates whether the user is currently idle or not.

In the `useEffect` hook, we set up event listeners for `mousemove` and `keydown` events to detect user activity. When an activity is detected, we reset the idle timeout by clearing the existing timeout using `clearTimeout` and setting up a new timeout using `setTimeout`. If the idle timeout elapses, we set the `idle` state to `true` and call the `callback` function.

Finally, we clean up the event listeners and clear the idle timeout when the component is unmounted.

## Using the useIdleTimeout hook
Now that we have our custom `useIdleTimeout` hook, let's see how we can use it in a React component:

```jsx
import React from 'react';
import useIdleTimeout from './useIdleTimeout';

const MyComponent = () => {
  const handleIdleTimeout = () => {
    // Perform actions when user is idle
  };

  const isIdle = useIdleTimeout(60000, handleIdleTimeout);

  return (
    <div>
      {isIdle ? (
        <p>You have been idle for too long. Please log in again.</p>
      ) : (
        <p>Do something...</p>
      )}
    </div>
  );
};

export default MyComponent;
```

In the example above, we import the `useIdleTimeout` hook and define a `handleIdleTimeout` function to be called when the user is considered idle. We then use the `useIdleTimeout` hook in our component passing the desired idle time and the `handleIdleTimeout` function as parameters. The `useIdleTimeout` hook returns a boolean value indicating whether the user is currently idle or not. Based on this value, we can conditionally render different content in our component.

## Conclusion
Creating a custom `useIdleTimeout` hook allows us to encapsulate the logic for detecting user inactivity and triggering a callback function. By using this hook, we can easily implement idle timeout functionality in our React applications, enhancing both the security and user experience.