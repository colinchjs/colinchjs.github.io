---
layout: post
title: "Creating a custom useEventListenerEffect hook for adding/removing event listeners as side effects"
description: " "
date: 2023-10-11
tags: [customhook]
comments: true
share: true
---

In this blog post, we will learn how to create a custom React hook called `useEventListenerEffect` that allows us to add and remove event listeners as side effects in our components. Event listeners are common in web development, and managing their lifecycle can be tedious. By encapsulating this logic in a custom hook, we can make our code more modular and reusable.

## Table of Contents

- [Introduction](#introduction)
- [Creating the Hook](#creating-the-hook)
- [Using the Hook](#using-the-hook)
- [Conclusion](#conclusion)

## Introduction

Event listeners are used to listen for various user interactions such as mouse clicks, keyboard inputs, or window resizing. In React, adding and removing event listeners is typically done inside lifecycle methods like `componentDidMount` and `componentWillUnmount` for class components or the `useEffect` hook for functional components.

However, managing event listeners manually in each component can become repetitive and error-prone. By creating a custom hook, we can abstract away the complexity and provide a clean API for adding and removing event listeners when needed.

## Creating the Hook

Let's start by creating the `useEventListenerEffect` hook. This hook will take in three arguments:

1. `eventName`: The name of the event to listen for (e.g., "click", "keydown").
2. `handler`: The event handler function that will be called when the event is triggered.
3. `element`: (optional) The DOM element on which the event listener should be attached. If not provided, the event listener will be attached to the `window` object.

```javascript
import { useEffect } from 'react';

const useEventListenerEffect = (eventName, handler, element = window) => {
  useEffect(() => {
    // Add the event listener
    element.addEventListener(eventName, handler);

    // Remove the event listener on cleanup
    return () => {
      element.removeEventListener(eventName, handler);
    };
  }, [eventName, handler, element]);
};

export default useEventListenerEffect;
```

In this hook, we use the `useEffect` hook to ensure that the event listener is added only once when the component mounts and removed when the component unmounts. The dependency array `[eventName, handler, element]` ensures that the effect is only re-run if any of these values change.

## Using the Hook

Now that we have our custom hook, let's see how we can use it in a component.

```javascript
import React from 'react';
import useEventListenerEffect from './useEventListenerEffect';

const ExampleComponent = () => {
  const handleKeyPress = (event) => {
    // Handle key press event
  };

  useEventListenerEffect('keydown', handleKeyPress);

  return (
    <div>
      {/* Component content */}
    </div>
  );
};

export default ExampleComponent;
```

In the above example, we import and use our `useEventListenerEffect` hook to add a keydown event listener to the `window` object. The `handleKeyPress` function will be called when a key is pressed. You can replace `'keydown'` with any other event name and provide a different element to attach the event listener if needed.

## Conclusion

By creating a custom `useEventListenerEffect` hook, we can easily add and remove event listeners as side effects in our React components. This approach reduces duplication and makes our code more readable and maintainable. Additionally, it promotes reusability by abstracting away the low-level event handling logic.

Using custom hooks allows us to encapsulate common tasks and share them across different components, improving productivity and code quality.

By using this hook, we can focus on the actual functionality of our components without worrying about adding or removing event listeners manually. Happy coding!

#seo #customhook