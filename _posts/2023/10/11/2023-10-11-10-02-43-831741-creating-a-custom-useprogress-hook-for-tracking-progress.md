---
layout: post
title: "Creating a custom useProgress hook for tracking progress"
description: " "
date: 2023-10-11
tags: [React, CustomHooks]
comments: true
share: true
---

In this blog post, we will learn how to create a custom React hook called `useProgress` that allows us to track the progress of a task or operation. This hook will be reusable and can be utilized in various scenarios where progress tracking is required.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Building the `useProgress` Hook](#building-the-useprogress-hook)
- [Using the `useProgress` Hook](#using-the-useprogress-hook)
- [Conclusion](#conclusion)

## Introduction
Tracking progress is essential in many applications, especially when performing time-consuming operations like file uploads, API requests, or form submissions. With the help of React hooks, we can easily create a custom hook to handle this functionality in a declarative and reusable manner.

## Prerequisites
Before we start, make sure you have the following set up:

- Basic knowledge of React hooks and functional components
- Installed Node.js and npm or yarn to create a React project

## Building the `useProgress` Hook
Let's begin by creating a new file called `useProgress.js` and define our custom hook inside it.

```javascript
import React, { useState, useEffect } from 'react';

const useProgress = (initialValue = 0) => {
  const [progress, setProgress] = useState(initialValue);

  useEffect(() => {
    const interval = setInterval(() => {
      setProgress((prevProgress) => {
        if (prevProgress === 100) {
          clearInterval(interval);
          return 100;
        }
        return prevProgress + 1;
      });
    }, 100);

    return () => clearInterval(interval);
  }, []);

  return progress;
}

export default useProgress;
```

In the code snippet above, we import the necessary dependencies from React, and define our custom hook `useProgress`. The hook takes an optional `initialValue` parameter, which defaults to 0 if not provided.

Inside the hook, we use the `useState` hook to create a `progress` state variable and its corresponding `setProgress` function. The `progress` state represents the current progress value, and `setProgress` is used to update it.

We also use the `useEffect` hook to start a timer interval that increments the progress value by 1 every 100 milliseconds, until it reaches 100. Once the progress reaches 100, the interval is cleared and the `useEffect` hook cleans up by returning a function that clears the interval.

Finally, the `useProgress` hook returns the `progress` value for external use.

## Using the `useProgress` Hook
Now that we have our custom `useProgress` hook ready, let's see how we can use it in a practical example.

```javascript
import React from 'react';
import useProgress from './useProgress';

const App = () => {
  const progress = useProgress(0);

  return (
    <div>
      <h1>Progress: {progress}%</h1>
    </div>
  );
}

export default App;
```

In the example code above, we import the `useProgress` hook from our `useProgress.js` file and use it inside our functional component `App`. We store the progress value in the `progress` variable and display it as a percentage in the component's JSX.

## Conclusion
By creating a custom `useProgress` hook, we can easily track the progress of any task or operation in our React applications. This hook is highly reusable and can be utilized in various scenarios where progress tracking is needed. Feel free to extend the functionality of the hook according to your project requirements.

We hope you found this tutorial helpful in understanding how to create a custom hook for tracking progress in React. If you have any questions or suggestions, please feel free to reach out to us.

**#React** **#CustomHooks**