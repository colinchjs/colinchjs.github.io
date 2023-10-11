---
layout: post
title: "Creating a custom useInterval hook for setting intervals"
description: " "
date: 2023-10-11
tags: [ReactHooks, CustomHook]
comments: true
share: true
---

In this blog post, we will explore how to create a custom React hook called `useInterval` for setting intervals in functional components. This hook will simplify the process of using the `setInterval` function in a React component, making it easy to manage and clean up intervals.

## Table of Contents
- [Introduction](#introduction)
- [Creating the `useInterval` Hook](#creating-the-useinterval-hook)
- [Using the `useInterval` Hook](#using-the-useinterval-hook)
- [Conclusion](#conclusion)

## Introduction

In React, managing intervals using the built-in `setInterval` function can be quite cumbersome. You need to manually clear the interval when the component unmounts, which can be prone to errors and can create memory leaks. 

To address this issue, we can create a custom hook called `useInterval` that handles the interval setup and cleanup automatically.

## Creating the `useInterval` Hook

```javascript
import { useEffect, useRef } from 'react';

const useInterval = (callback, delay) => {
  const savedCallback = useRef();

  useEffect(() => {
    savedCallback.current = callback;
  }, [callback]);

  useEffect(() => {
    const tick = () => {
      savedCallback.current();
    };

    if (delay !== null) {
      const intervalId = setInterval(tick, delay);
      return () => clearInterval(intervalId);
    }
  }, [delay]);
};

export default useInterval;
```

The `useInterval` hook takes two arguments: `callback` and `delay`. The `callback` function will be invoked repeatedly with the specified `delay` in milliseconds, and it returns a cleanup function to clear the interval.

Inside the hook, we use the `useRef` hook to hold the latest callback value and save it in a `ref` called `savedCallback`. This ensures that we always have access to the latest callback, even if the `callback` prop changes.

We use two separate `useEffect` hooks to properly handle the setup and cleanup of the interval. The first `useEffect` updates the `savedCallback` ref whenever the `callback` prop changes. The second `useEffect` sets up the interval when the component mounts and returns a cleanup function to clear the interval when the component unmounts or the `delay` prop changes.

## Using the `useInterval` Hook

Let's see how we can use the `useInterval` hook in a functional component:

```javascript
import React, { useState } from 'react';
import useInterval from './useInterval';

const MyComponent = () => {
  const [count, setCount] = useState(0);

  useInterval(() => {
    setCount((prevCount) => prevCount + 1);
  }, 1000);

  return (
    <div>
      <h1>{count}</h1>
    </div>
  );
};

export default MyComponent;
```

In this example, we create a simple counter that increments every second using the `useInterval` hook. We pass in a callback that updates the `count` state using the `setCount` function provided by the `useState` hook. The interval is set to 1000 milliseconds (1 second).

## Conclusion

The `useInterval` hook simplifies the process of setting intervals in React functional components. It handles interval setup and cleanup automatically, ensuring that intervals are properly managed without causing memory leaks or errors.

By creating custom hooks like `useInterval`, we can encapsulate complex logic into reusable units and enhance the overall modularity and readability of our React code.

Give the `useInterval` hook a try in your next React project and let us know how it simplifies your interval management!

**#ReactHooks #CustomHook**