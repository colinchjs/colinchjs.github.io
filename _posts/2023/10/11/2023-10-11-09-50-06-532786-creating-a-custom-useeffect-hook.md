---
layout: post
title: "Creating a custom useEffect hook"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In React, the `useEffect` hook allows us to perform side effects such as data fetching, subscriptions, or manipulating the DOM. It is a powerful feature that helps us manage the lifecycle of our components. However, sometimes we find ourselves duplicating the same `useEffect` logic in multiple components. In such cases, it can be useful to create a custom `useEffect` hook that encapsulates the common functionality. In this blog post, we'll explore how to create a custom `useEffect` hook in React.

## Table of Contents

- [What is `useEffect`](#what-is-useeffect)
- [Why Create a Custom `useEffect` Hook](#why-create-a-custom-useeffect-hook)
- [How to Create a Custom `useEffect` Hook](#how-to-create-a-custom-useeffect-hook)
- [Example Usage of Custom `useEffect` Hook](#example-usage-of-custom-useeffect-hook)
- [Conclusion](#conclusion)

## What is `useEffect`

`useEffect` is a built-in React hook that allows us to perform side effects inside functional components. It has the following signature:

```jsx
useEffect(callback: Function, dependencies?: Array<any>)
```

The `callback` function is called after the component has rendered, and it can return a cleanup function to clean up any resources when the component unmounts. The optional `dependencies` array allows us to control when the effect is re-run.

## Why Create a Custom `useEffect` Hook

Creating a custom `useEffect` hook can have several benefits:

1. **Code Reusability**: If you find yourself using the same `useEffect` logic in multiple components, creating a custom hook allows you to encapsulate that logic in one place and reuse it across different components.

2. **Readability and Maintainability**: By encapsulating complex `useEffect` logic in a custom hook, you can make your components cleaner, easier to read, and maintain.

3. **Separation of Concerns**: Using a custom hook allows you to separate the side-effect logic from the actual component rendering logic, promoting better separation of concerns.

## How to Create a Custom `useEffect` Hook

Creating a custom `useEffect` hook is straightforward. Here are the steps to follow:

1. Create a new file in your project, for example, `useCustomEffect.js`.

2. Inside the file, import the necessary dependencies:

```jsx
import { useEffect } from "react";
```

3. Define your custom hook by exporting a function that takes the `callback` and `dependencies` as parameters:

```jsx
export function useCustomEffect(callback, dependencies) {
  useEffect(callback, dependencies);
}
```

4. That's it! You've created your custom `useEffect` hook. You can now import and use it in your components.

## Example Usage of Custom `useEffect` Hook

Let's say we want to create a custom hook that automatically increments a counter every second. Here's how we can write the custom `useEffect` hook:

```jsx
import { useEffect, useState } from "react";

export function useCounter() {
  const [count, setCount] = useState(0);

  useCustomEffect(() => {
    const intervalId = setInterval(() => {
      setCount((prevCount) => prevCount + 1);
    }, 1000);

    return () => {
      clearInterval(intervalId);
    };
  }, []);

  return count;
}
```

In this example, we define a custom hook `useCounter` that uses the custom `useCustomEffect` hook. The `useCounter` hook maintains a count state, increments it every second using `setCount`, and clears the interval on component unmount.

We can now use the `useCounter` hook in our components:

```jsx
import React from "react";
import { useCounter } from "./useCounter";

const Counter = () => {
  const count = useCounter();

  return (
    <div>
      <h1>{count}</h1>
    </div>
  );
};

export default Counter;
```

By using the custom `useCounter` hook, we can easily manage the counter functionality across multiple components without duplicating the `useEffect` logic.

## Conclusion

Creating a custom `useEffect` hook can be a useful technique to improve code reusability, readability, and maintainability in React applications. By encapsulating common side-effect logic in a custom hook, we can easily reuse it across different components, promoting better separation of concerns.