---
layout: post
title: "Creating a custom useWindowSizeEffect hook for handling side effects based on window size changes"
description: " "
date: 2023-10-11
tags: [React, Hooks]
comments: true
share: true
---

In modern web development, it is crucial to provide a seamless user experience across different devices and screen sizes. One common requirement is to update the UI or perform certain actions based on the window size. In this blog post, we will learn how to create a custom React hook called `useWindowSizeEffect` that allows us to handle side effects based on window size changes.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Implementation](#implementation)
- [Usage](#usage)
- [Conclusion](#conclusion)

## Prerequisites

Before we begin, make sure you have the following prerequisites set up:

- Basic knowledge of React hooks and functional components.
- Familiarity with JavaScript and React syntax.
- A basic React project set up.

## Implementation

Let's start by creating a new file named `useWindowSizeEffect.js` and open it in your favorite code editor.

```javascript
import { useEffect } from 'react';

const useWindowSizeEffect = (effect) => {
  useEffect(() => {
    const handleWindowSizeChange = () => {
      effect(window.innerWidth, window.innerHeight);
    };

    // Listen for window size changes
    window.addEventListener('resize', handleWindowSizeChange);

    // Clean up the event listener on unmount
    return () => {
      window.removeEventListener('resize', handleWindowSizeChange);
    };
  }, [effect]);
};

export default useWindowSizeEffect;
```

In the code snippet above, we defined our `useWindowSizeEffect` hook. It takes an `effect` function as a parameter, which will be called whenever the window size changes. We use the `useEffect` hook to set up the event listener for the `resize` event and clean it up on component unmount.

## Usage

To use the `useWindowSizeEffect` hook in your React component, follow these steps:

1. Import the `useWindowSizeEffect` hook into your component file.
2. Define an `effect` function that will be called when the window size changes.
3. Call the `useWindowSizeEffect` hook, passing the `effect` function as a parameter.

Here's an example of how you can use the `useWindowSizeEffect` hook:

```javascript
import React from 'react';
import useWindowSizeEffect from './useWindowSizeEffect';

const MyComponent = () => {
  const handleWindowSizeChange = (width, height) => {
    // Perform side effects based on window size
    // For example, update UI or trigger certain actions
    // Use the width and height values in your logic
  };

  useWindowSizeEffect(handleWindowSizeChange);

  return (
    <div>
      {/* Your component JSX */}
    </div>
  );
};

export default MyComponent;
```

In the example above, we define the `handleWindowSizeChange` function that will be called every time the window size changes. You can perform any side effects, such as updating the UI or triggering certain actions, inside this function.

## Conclusion

Handling side effects based on window size changes is a common requirement in modern web development. By creating a custom `useWindowSizeEffect` hook, we can encapsulate the logic for listening to window size changes and easily reuse it across different components.

In this blog post, we learned how to create a custom `useWindowSizeEffect` hook using React's `useEffect` hook and how to use it in a React component. We can now handle side effects based on window size changes effortlessly.

By using this hook, you can enhance the user experience of your web application by providing adaptive UI and performing responsive actions based on the window size.

---

Tags: #React #Hooks