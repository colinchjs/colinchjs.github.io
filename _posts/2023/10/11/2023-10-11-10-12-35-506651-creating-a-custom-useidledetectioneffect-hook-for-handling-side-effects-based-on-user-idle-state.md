---
layout: post
title: "Creating a custom useIdleDetectionEffect hook for handling side effects based on user idle state"
description: " "
date: 2023-10-11
tags: [reactjs, customhook]
comments: true
share: true
---

In modern web applications, it's common to have side effects triggered based on user activity or inactivity. One such use case is to perform certain actions when the user is idle for a specified amount of time.

In this blog post, we will create a custom React hook, `useIdleDetectionEffect`, that will allow us to handle side effects based on the user's idle state. 

## Table of Contents
- [Understanding the concept](#understanding-the-concept)
- [Building the `useIdleDetectionEffect` hook](#building-the-useidledetectioneffect-hook)
- [Using the custom hook](#using-the-custom-hook)
- [Conclusion](#conclusion)

## Understanding the concept

Before we dive into the implementation, let's understand the concept of detecting user idle state. When a user is idle, it means that they haven't interacted with the application for a certain period of time. This period can be defined as the time window within which no user activity is considered as idle. 

We can track user activity using events like mouse movement, keyboard presses, or touch gestures. By monitoring these events, we can update a timer that resets each time a user activity is detected. When the timer reaches the idle threshold, we can assume that the user is idle.

## Building the `useIdleDetectionEffect` hook

Let's start by creating the `useIdleDetectionEffect` custom hook using React's `useEffect` and `useState` hooks.

```jsx
import { useEffect, useState } from 'react';

const useIdleDetectionEffect = (idleTimeout, onIdle) => {
  const [idle, setIdle] = useState(false);

  useEffect(() => {
    let timeout;

    const resetTimer = () => {
      clearTimeout(timeout);
      timeout = setTimeout(() => {
        setIdle(true);
        onIdle();
      }, idleTimeout);
    };

    const handleActivity = () => {
      setIdle(false);
      resetTimer();
    };

    const handleVisibilityChange = () => {
      if (document.visibilityState === 'hidden') {
        setIdle(true);
        onIdle();
      } else {
        handleActivity();
      }
    };

    document.addEventListener('visibilitychange', handleVisibilityChange);
    document.addEventListener('mousemove', handleActivity);
    document.addEventListener('keydown', handleActivity);
    document.addEventListener('scroll', handleActivity);

    resetTimer();

    return () => {
      clearTimeout(timeout);
      document.removeEventListener('visibilitychange', handleVisibilityChange);
      document.removeEventListener('mousemove', handleActivity);
      document.removeEventListener('keydown', handleActivity);
      document.removeEventListener('scroll', handleActivity);
    };
  }, [idleTimeout, onIdle]);

  return idle;
};

export default useIdleDetectionEffect;
```

In the `useIdleDetectionEffect` hook, we create a state variable called `idle` using `useState`. This state variable tracks the user's idle state.

Inside the `useEffect` hook, we set up event listeners for various user activities such as `mousemove`, `keydown`, `scroll`, and `visibilitychange`. When any of these events occur, we reset the idle timer. When the idle timer reaches the specified `idleTimeout`, we set the `idle` state to `true`, indicating that the user is idle. Finally, we call the `onIdle` callback to handle the side effect associated with the user being idle.

The hook also cleans up the event listeners when the component unmounts or when the dependencies `idleTimeout` or `onIdle` change.

## Using the custom hook
Now that we have our custom `useIdleDetectionEffect` hook, let's see how we can use it in a React component.

```jsx
import React from 'react';
import useIdleDetectionEffect from './useIdleDetectionEffect';

const App = () => {
  const handleIdle = () => {
    // Perform side effects when the user is idle
    console.log('User is idle');
  };

  const isIdle = useIdleDetectionEffect(30000, handleIdle);

  return (
    <div>
      <h1>Idle Detection Example</h1>
      {isIdle ? (
        <p>The user is currently idle.</p>
      ) : (
        <p>The user is active.</p>
      )}
    </div>
  );
};

export default App;
```

In this example, we import our custom hook `useIdleDetectionEffect` and use it in the `App` component. We pass the idle timeout of `30000` milliseconds (30 seconds) and provide a callback `handleIdle` to be executed when the user is idle. The hook returns a boolean value, `isIdle`, which we use to conditionally render the UI.

## Conclusion

In this blog post, we explored how to create a custom `useIdleDetectionEffect` hook in React for handling side effects based on the user's idle state. By monitoring user activity and setting up a timer, we can reliably detect when the user is idle and perform actions accordingly.

This custom hook can be a useful addition to web applications that require specific behavior or actions when the user is inactive for a certain period of time.

#reactjs #customhook