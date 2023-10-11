---
layout: post
title: "Creating a custom useViewportSize hook for tracking viewport size"
description: " "
date: 2023-10-11
tags: [webdevelopment, reactjs]
comments: true
share: true
---

In this blog post, we'll learn how to create a custom `useViewportSize` hook using React. This hook will allow us to track the size of the viewport and update it whenever it changes. This can be useful for building responsive web applications or implementing dynamic UI based on the viewport dimensions.

## Table of Contents
- [Introduction](#introduction)
- [Setting Up a React App](#setting-up-a-react-app)
- [Creating the useViewportSize Hook](#creating-the-useviewportsize-hook)
- [Using the useViewportSize Hook](#using-the-useviewportsize-hook)
- [Conclusion](#conclusion)

## Introduction
Tracking the size of the viewport is important when building responsive web applications that need to adapt to different screen sizes. The `window` object in JavaScript provides the `innerWidth` and `innerHeight` properties that can be used to retrieve the current dimensions of the viewport. By creating a custom React hook, we can easily track the changes to the viewport size and respond accordingly.

## Setting Up a React App
Before we start creating our custom hook, let's set up a basic React app to work with. Assuming you have Node.js and npm installed, you can follow these steps:

1. Open your terminal and navigate to the desired directory for your project.
2. Run the following command to create a new React app:

```shell
npx create-react-app viewport-size-app
```

3. Once the installation is complete, navigate into the newly created project directory:

```shell
cd viewport-size-app
```

4. Start the development server:

```shell
npm start
```

Now that our React app is set up, we can move on to creating the `useViewportSize` hook.

## Creating the useViewportSize Hook
Let's create a new file called `useViewportSize.js` in the `src` directory of our React app. This file will contain the custom hook logic.

```javascript
import { useState, useEffect } from 'react';

const useViewportSize = () => {
  const [viewportSize, setViewportSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });

  useEffect(() => {
    const handleResize = () => {
      setViewportSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    };

    window.addEventListener('resize', handleResize);

    return () => {
      window.removeEventListener('resize', handleResize);
    };
  }, []);

  return viewportSize;
};

export default useViewportSize;
```

In the `useViewportSize` hook, we initialize the state with the current viewport dimensions using the `useState` hook. We then add an event listener to the `resize` event of the `window` object to update the viewport size whenever the window is resized. Finally, we remove the event listener in the cleanup function of the `useEffect` hook to prevent memory leaks.

## Using the useViewportSize Hook
Now that we have our custom hook, let's use it in our React app to track the viewport size. Open the `App.js` file in the `src` directory of our project and modify it as follows:

```javascript
import React from 'react';
import useViewportSize from './useViewportSize';

function App() {
  const viewportSize = useViewportSize();

  return (
    <div>
      <h1>Viewport Size Tracking</h1>
      <p>Width: {viewportSize.width}px</p>
      <p>Height: {viewportSize.height}px</p>
    </div>
  );
}

export default App;
```

In this example, we import the `useViewportSize` hook from the `useViewportSize.js` file and call it to obtain the current viewport size. We then render the width and height of the viewport in the HTML markup.

## Conclusion
In this blog post, we have learned how to create a custom `useViewportSize` hook using React. By tracking the dimensions of the viewport, we can create responsive web applications that adapt to different screen sizes. The `useViewportSize` hook can be a useful tool in building dynamic UI and improving user experience.

Thank you for reading!

#webdevelopment #reactjs