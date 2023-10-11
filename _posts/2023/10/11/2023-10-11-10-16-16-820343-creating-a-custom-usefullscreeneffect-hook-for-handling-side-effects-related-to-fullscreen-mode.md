---
layout: post
title: "Creating a custom useFullscreenEffect hook for handling side effects related to fullscreen mode"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In this tutorial, we will create a custom React hook called `useFullscreenEffect` that will allow us to handle side effects related to fullscreen mode. We will be using React and the `fullscreenchange` event provided by the browser's `Document` object.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Creating the `useFullscreenEffect` Hook](#creating-the-usefullscreeneffect-hook)
- [Using the `useFullscreenEffect` Hook](#using-the-usefullscreeneffect-hook)
- [Conclusion](#conclusion)

## Introduction
Fullscreen mode is a common feature in many web applications. It allows users to view content in fullscreen without any distractions. When working with fullscreen mode, we might need to perform certain actions or invoke specific side effects. This is where our custom `useFullscreenEffect` hook comes into play.

## Prerequisites
To follow along with this tutorial, make sure you have the following installed:
- Node.js
- npm (Node Package Manager)
- React

## Creating the `useFullscreenEffect` Hook
Let's start by creating a new file called `useFullscreenEffect.js` and define our custom hook. The hook will take a callback function as an argument, which will be called whenever the fullscreen mode changes.

```javascript
import { useEffect } from 'react';

const useFullscreenEffect = (callback) => {
  useEffect(() => {
    const handleFullscreenChange = () => {
      callback(document.fullscreenElement !== null);
    };

    document.addEventListener('fullscreenchange', handleFullscreenChange);

    return () => {
      document.removeEventListener('fullscreenchange', handleFullscreenChange);
    };
  }, [callback]);
};

export default useFullscreenEffect;
```

Here, we are using the `useEffect` hook to add and remove event listeners for the `fullscreenchange` event. In the `handleFullscreenChange` function, we check if `document.fullscreenElement` is `null` to determine if the fullscreen mode is active or not. We then call the provided `callback` function with a boolean parameter indicating the current fullscreen mode.

## Using the `useFullscreenEffect` Hook
Now that we have created our custom hook, let's see how we can use it in a React component.

```javascript
import React from 'react';
import useFullscreenEffect from './useFullscreenEffect';

const App = () => {
  const handleFullscreenChange = (isFullscreen) => {
    if (isFullscreen) {
      // Logic for fullscreen mode enabled
    } else {
      // Logic for fullscreen mode disabled
    }
  };

  useFullscreenEffect(handleFullscreenChange);

  return (
    <div>
      {/* Your app content */}
    </div>
  );
};

export default App;
```

In this example, we import our custom `useFullscreenEffect` hook and define a callback function `handleFullscreenChange`. Inside this function, we can implement the logic that needs to be executed when the fullscreen mode changes. We then call the `useFullscreenEffect` hook with the `handleFullscreenChange` function.

## Conclusion
Creating a custom hook like `useFullscreenEffect` allows us to encapsulate the logic for handling side effects related to fullscreen mode in a reusable manner. It simplifies the management of fullscreen mode changes and provides a clean and structured approach.

Now you can easily incorporate fullscreen mode in your React applications and handle any related side effects with ease.