---
layout: post
title: "Creating a custom useLocalStorageEffect hook for handling side effects based on local storage changes"
description: " "
date: 2023-10-11
tags: [developer, reacthooks]
comments: true
share: true
---

In this blog post, we'll explore how to create a custom React hook called `useLocalStorageEffect` that allows us to handle side effects based on changes to the local storage in our application. This can be useful in scenarios where we need to synchronize our application state with the data stored in the browser's local storage.

## Table of Contents
1. [Introduction](#introduction)
2. [Setting up the project](#setting-up-the-project)
3. [Implementing the useLocalStorageEffect hook](#implementing-the-uselocalstorageeffect-hook)
4. [Using the useLocalStorageEffect hook](#using-the-uselocalstorageeffect-hook)
5. [Conclusion](#conclusion)

## Introduction
React hooks provide a way to reuse stateful logic in functional components. While React provides built-in hooks like useState and useEffect, there are scenarios where we may need to create our own custom hooks to handle specific scenarios. In this case, we want to create a hook that listens to changes in the local storage and triggers a side effect in response.

## Setting up the project
To follow along with this tutorial, make sure you have a React project set up. You can create a new project using `create-react-app` or use an existing one.

## Implementing the useLocalStorageEffect hook
Let's start by creating a new file called `useLocalStorageEffect.js`. This file will contain the implementation of our custom hook.

```javascript
import { useEffect } from 'react';

export const useLocalStorageEffect = (key, callback) => {
  useEffect(() => {
    const handleStorageChange = (event) => {
      if (event.key === key) {
        callback();
      }
    };

    window.addEventListener('storage', handleStorageChange);

    return () => {
      window.removeEventListener('storage', handleStorageChange);
    };
  }, [key, callback]);
};
```

In the code above, we define a function called `useLocalStorageEffect` that takes a `key` and a `callback` as arguments. Inside the hook, we use the `useEffect` hook to listen to changes in the local storage by adding a listener for the `'storage'` event. Whenever there is a change in the storage, we check if the changed key matches the provided `key` argument and invoke the `callback` if it does.

## Using the useLocalStorageEffect hook
Now that we have our custom hook, let's see how we can use it in a React component. Suppose we have a counter component that stores its value in the local storage. We want to update the counter value whenever it is changed in another tab or window.

```javascript
import React, { useState } from 'react';
import { useLocalStorageEffect } from './useLocalStorageEffect';

const Counter = () => {
  const [count, setCount] = useState(() => {
    const storedCount = parseInt(localStorage.getItem('count'), 10);
    return isNaN(storedCount) ? 0 : storedCount;
  });

  useLocalStorageEffect('count', () => {
    const storedCount = parseInt(localStorage.getItem('count'), 10);
    setCount(isNaN(storedCount) ? 0 : storedCount);
  });

  const increment = () => {
    setCount((prevCount) => prevCount + 1);
    localStorage.setItem('count', count + 1);
  };

  const decrement = () => {
    setCount((prevCount) => prevCount - 1);
    localStorage.setItem('count', count - 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default Counter;
```

In the code above, we define a component called `Counter` that maintains a count state using `useState`. We also use our `useLocalStorageEffect` hook to update the count whenever it changes in the local storage. The `increment` and `decrement` functions update the count state and store the updated value in the local storage.

## Conclusion
In this blog post, we learned how to create a custom React hook called `useLocalStorageEffect` that allows us to handle side effects based on changes in the local storage. This can be a powerful tool for synchronizing our application state with the data stored in the browser. By creating and using custom hooks in our React applications, we can encapsulate complex logic and make our code more reusable and maintainable. Happy coding!

#developer #reacthooks