---
layout: post
title: "Creating a custom useWindowSize hook for tracking window size"
description: " "
date: 2023-10-11
tags: [React, WindowResize]
comments: true
share: true
---

In this blog post, we will explore how to create a custom `useWindowSize` hook in React for tracking the size of the window. This hook can be useful in scenarios where you need to dynamically adjust the layout or perform specific actions based on the window size changes.

## Table of Contents
- [Introduction](#introduction)
- [Creating the `useWindowSize` hook](#creating-the-usewindowsize-hook)
- [Using the `useWindowSize` hook](#using-the-usewindowsize-hook)
- [Conclusion](#conclusion)

## Introduction
In many cases, it is crucial to adapt the user interface of a web application based on the window size. For instance, you might want to hide certain components on smaller screens or adjust the layout dynamically to provide a better user experience. In such scenarios, having knowledge about the current window size becomes essential.

React provides a powerful `useEffect` hook for performing side effects, such as subscribing to window resize events. By utilizing this hook, we can create a custom `useWindowSize` hook that provides the current window size as state variables.

## Creating the `useWindowSize` hook
Let's start by creating our custom `useWindowSize` hook:

```jsx
import { useState, useEffect } from 'react';

const useWindowSize = () => {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });

  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    };

    window.addEventListener('resize', handleResize);

    // Cleanup the event listener on component unmount
    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return windowSize;
};

export default useWindowSize;
```

In the code snippet above, we import the necessary dependencies from React (`useState` and `useEffect`) and define our custom hook `useWindowSize`. 

We initialize the `windowSize` state with the current window width and height using `window.innerWidth` and `window.innerHeight`. 

Next, we add an event listener for the `resize` event and update the `windowSize` state whenever the window is resized. The cleanup function ensures that the event listener is removed when the component unmounts.

Finally, we return the `windowSize` state from our custom hook.

## Using the `useWindowSize` hook
Now that we have our custom `useWindowSize` hook, let's explore how to use it in a functional component:

```jsx
import React from 'react';
import useWindowSize from './useWindowSize';

const App = () => {
  const windowSize = useWindowSize();

  return (
    <>
      <h1>Window Size: {windowSize.width}x{windowSize.height}</h1>
      {/* Render other components based on window size */}
    </>
  );
};

export default App;
```

In the above example, we import our custom hook `useWindowSize` and use it within the functional component `App`. We destructure the `windowSize` object returned by the hook and display the width and height on the screen. 

You can now implement specific logic based on the `windowSize` state to adjust the user interface or perform any necessary actions.

## Conclusion
In this blog post, we learned how to create a custom `useWindowSize` hook in React for tracking the size of the window. By leveraging the `useEffect` hook and subscribing to the window resize event, we can efficiently update the window size state. This custom hook can be utilized in various scenarios where dynamic adjustments based on the window size are required. Experiment with it and adapt it to suit your specific needs.

Remember to check out our [GitHub repository](https://github.com/example) for the complete code. 

Keep an eye out for more interesting React hooks and React-related content on our blog!

---

Hashtags: #React #WindowResize