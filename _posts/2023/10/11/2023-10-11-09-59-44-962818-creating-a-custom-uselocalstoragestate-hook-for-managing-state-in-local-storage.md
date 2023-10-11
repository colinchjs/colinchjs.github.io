---
layout: post
title: "Creating a custom useLocalStorageState hook for managing state in local storage"
description: " "
date: 2023-10-11
tags: [React, Hooks]
comments: true
share: true
---

Managing state in React applications is crucial for building dynamic and interactive user interfaces. While React's built-in `useState` hook makes it easy to manage state within a component, there are scenarios where you may want to persist and retrieve that state from local storage.

In this blog post, we'll walk through the process of creating a custom React hook called `useLocalStorageState`, which provides the functionality of `useState` while automatically storing and retrieving the state from local storage.

## Table of Contents
- [Introduction](#introduction)
- [Understanding Local Storage](#understanding-local-storage)
- [Creating the `useLocalStorageState` Hook](#creating-the-uselocalstoragestate-hook)
- [Using the `useLocalStorageState` Hook](#using-the-uselocalstoragestate-hook)
- [Conclusion](#conclusion)

## Introduction

When working on web applications, it's common to have components that need to maintain state across page reloads or even when the browser is closed and reopened. Local storage offers a simple way to store key-value pairs in the browser - making it an excellent choice for persisting state.

## Understanding Local Storage

Local storage is a part of the web storage API, which provides a way to store persistent data in a web browser. It stores data as key-value pairs and supports values of various types, including strings, numbers, objects, and arrays.

In JavaScript, we can access the local storage via the `localStorage` object. It provides methods like `setItem`, `getItem`, `removeItem`, and `clear` for manipulating the stored data.

## Creating the `useLocalStorageState` Hook

Let's start by creating a new file called `useLocalStorageState.js` and defining our custom hook inside it.

```javascript
import { useState, useEffect } from 'react';

const useLocalStorageState = (key, defaultValue) => {
  const [state, setState] = useState(() => {
    // Retrieve the stored state from local storage
    const storedState = localStorage.getItem(key);
    return storedState ? JSON.parse(storedState) : defaultValue;
  });

  // Update local storage whenever the state changes
  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(state));
  }, [key, state]);

  return [state, setState];
};

export default useLocalStorageState;
```

In the code snippet above, we import the `useState` and `useEffect` hooks from React. These hooks will help us create and manage our custom hook.

Our `useLocalStorageState` hook takes two parameters:
- `key`: The key under which the state will be stored in local storage.
- `defaultValue`: The initial value for the state if no stored value is found in local storage.

Inside the hook, we set up our state using `useState` and provide a function as the initial value. This function checks if there is a stored state for the given key in local storage. If found, it parses the stored state using `JSON.parse`; otherwise, it uses the default value.

We then use `useEffect` to update the local storage whenever the state changes. The hook listens for changes in the `key` and `state` dependencies and calls `localStorage.setItem` to store the state as a stringified JSON object.

Finally, we return an array containing the current state and a function to update the state, just like the `useState` hook.

## Using the `useLocalStorageState` Hook

With our `useLocalStorageState` hook defined, let's see how we can use it in a React component.

```javascript
import React from 'react';
import useLocalStorageState from './useLocalStorageState';

const Counter = () => {
  const [count, setCount] = useLocalStorageState('counter', 0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <h1>Counter: {count}</h1>
      <button onClick={increment}>Increment</button>
    </div>
  );
};

export default Counter;
```

In this example, we import our custom hook and use it within the `Counter` component. We provide a unique key ("counter") and an initial value (0) to the `useLocalStorageState` hook.

The hook returns two values: `count` and `setCount`. We use the `count` value to display the current count, and the `setCount` function to update the count when the user clicks the "Increment" button.

Now, whenever the count changes, the state will also be automatically updated in local storage. The next time the component renders, it will retrieve the updated state from local storage.

## Conclusion

In this blog post, we learned how to create a custom React hook called `useLocalStorageState` for managing state in local storage. This hook provides a convenient way to persist and retrieve state across page reloads, allowing your application to seamlessly maintain a consistent user experience.

By leveraging local storage, you can store and retrieve key-value pairs in the browser, ensuring the persistence of state even in the face of page refreshes or browser restarts.

Give it a try in your React applications and experience the power of managing state in local storage with ease!

**#React #Hooks**