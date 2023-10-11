---
layout: post
title: "Creating a custom useIdleTimeoutEffect hook for handling side effects when idle timeout occurs"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In web applications, it is common to have an idle timeout feature that automatically logs out the user after a certain period of inactivity. When the idle timeout occurs, it's often necessary to perform certain side effects, such as displaying a notification or redirecting the user to a specific page. In this blog post, we will explore how to create a custom `useIdleTimeoutEffect` hook to handle these side effects.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Implementing the `useIdleTimeoutEffect` hook](#implementing-the-useidletimeouteffect-hook)
- [Using the `useIdleTimeoutEffect` hook](#using-the-useidletimeouteffect-hook)
- [Final thoughts](#final-thoughts)

## Introduction
The `useIdleTimeoutEffect` hook will allow us to encapsulate the logic for handling side effects when an idle timeout occurs. It will provide an easy and reusable way to add this functionality to our components.

## Prerequisites
To follow along with this tutorial, you should have a basic understanding of React hooks and functional components.

## Implementing the `useIdleTimeoutEffect` hook
Let's start by creating a new file called `useIdleTimeoutEffect.js` and define our custom hook.

```javascript
import { useEffect, useRef } from 'react';

const useIdleTimeoutEffect = (timeoutDuration, idleCallback) => {
  const timeoutRef = useRef(null);

  useEffect(() => {
    const handleIdle = () => {
      clearTimeout(timeoutRef.current);
      timeoutRef.current = setTimeout(idleCallback, timeoutDuration);
    };

    handleIdle();

    document.addEventListener('mousemove', handleIdle);
    document.addEventListener('keydown', handleIdle);

    return () => {
      document.removeEventListener('mousemove', handleIdle);
      document.removeEventListener('keydown', handleIdle);
      clearTimeout(timeoutRef.current);
    };
  }, [timeoutDuration, idleCallback]);

  return timeoutRef.current;
};

export default useIdleTimeoutEffect;
```

Here, we import `useEffect` and `useRef` from the React library. Inside the `useIdleTimeoutEffect` hook, we create a `timeoutRef` using the `useRef` hook to store the timeout reference.

We then define the `handleIdle` function, which is responsible for resetting the timeout whenever there is an activity (mouse move or keydown event). Inside the `useEffect` hook, we add event listeners to the `'mousemove'` and `'keydown'` events to call the `handleIdle` function. We also clear the timeout and remove the event listeners when the component is unmounted.

Finally, we return the current value of the timeout reference for external use.

## Using the `useIdleTimeoutEffect` hook
To demonstrate the usage of our custom hook, let's create a simple example component called `IdleTimeoutNotifier`. This component will display a notification when the idle timeout occurs.

```javascript
import React from 'react';
import useIdleTimeoutEffect from 'path/to/useIdleTimeoutEffect';

const IdleTimeoutNotifier = () => {
  const idleTimeoutRef = useIdleTimeoutEffect(60000, () => {
    alert('You have been idle for too long. You will be logged out.');
  });

  return (
    <div>
      <h1>Idle Timeout Notifier</h1>
      <p>Time until idle timeout: {Math.ceil(idleTimeoutRef / 1000)} seconds</p>
    </div>
  );
};

export default IdleTimeoutNotifier;
```

In this example, we import the `useIdleTimeoutEffect` hook and use it inside the `IdleTimeoutNotifier` component. We pass the desired timeout duration (in milliseconds) and a callback function that displays an alert when the idle timeout occurs.

We also render the remaining time until the idle timeout in seconds, retrieved from the value returned by the `useIdleTimeoutEffect` hook.

## Final thoughts
Creating a custom hook like `useIdleTimeoutEffect` allows us to handle side effects when an idle timeout occurs in a reusable and encapsulated way. By abstracting this logic into a hook, we can easily add idle timeout functionality to any component in our application.

Remember to adjust the timeout duration and the desired side effects according to your application's requirements. With this custom hook, you can enhance the user experience of your web application by effectively managing idle timeouts.