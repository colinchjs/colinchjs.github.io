---
layout: post
title: "Creating a custom useFullscreen hook for toggling fullscreen mode"
description: " "
date: 2023-10-11
tags: [react, hook]
comments: true
share: true
---

In this blog post, we will explore how to create a custom `useFullscreen` hook in React that allows us to easily toggle fullscreen mode for a specific element in our application.

## Table of Contents
- [What is fullscreen mode](#what-is-fullscreen-mode)
- [Setting up our project](#setting-up-our-project)
- [Creating the useFullscreen hook](#creating-the-usefullscreen-hook)
- [Using the useFullscreen hook](#using-the-usefullscreen-hook)
- [Conclusion](#conclusion)

## What is fullscreen mode
Fullscreen mode refers to displaying content on the entire screen, hiding other elements like browser tabs, address bars, and toolbars. It can be useful when you want to provide an immersive experience for your users or when working with media-intensive applications.

## Setting up our project
To demonstrate the use of the `useFullscreen` hook, we will create a simple React component that has a button. When the button is clicked, it will toggle fullscreen mode for a specific element within the component.

Let's start by setting up our project:
1. Create a new React app using your preferred tooling (`create-react-app`, for example).
2. Navigate to the project directory and install the required dependencies:
```bash
npm install react react-dom
```

## Creating the useFullscreen hook
Now, let's create our custom `useFullscreen` hook. This hook will handle enabling and disabling fullscreen mode for a given element using the `Fullscreen API`.

```javascript
import { useEffect, useState } from 'react';

const useFullscreen = (ref) => {
  const [isFullscreen, setIsFullscreen] = useState(false);

  const enterFullscreen = () => {
    if (ref.current) {
      if (ref.current.requestFullscreen) {
        ref.current.requestFullscreen();
      } else if (ref.current.mozRequestFullScreen) {
        ref.current.mozRequestFullScreen();
      } else if (ref.current.webkitRequestFullscreen) {
        ref.current.webkitRequestFullscreen();
      } else if (ref.current.msRequestFullscreen) {
        ref.current.msRequestFullscreen();
      }
    }
  };

  const exitFullscreen = () => {
    if (document.exitFullscreen) {
      document.exitFullscreen();
    } else if (document.mozCancelFullScreen) {
      document.mozCancelFullScreen();
    } else if (document.webkitExitFullscreen) {
      document.webkitExitFullscreen();
    } else if (document.msExitFullscreen) {
      document.msExitFullscreen();
    }
  };

  useEffect(() => {
    const handleFullscreenChange = () => {
      setIsFullscreen(
        document.fullscreenElement ||
        document.mozFullScreenElement ||
        document.webkitFullscreenElement ||
        document.msFullscreenElement
      );
    };

    document.addEventListener('fullscreenchange', handleFullscreenChange);
    document.addEventListener('mozfullscreenchange', handleFullscreenChange);
    document.addEventListener('webkitfullscreenchange', handleFullscreenChange);
    document.addEventListener('msfullscreenchange', handleFullscreenChange);

    return () => {
      document.removeEventListener('fullscreenchange', handleFullscreenChange);
      document.removeEventListener('mozfullscreenchange', handleFullscreenChange);
      document.removeEventListener('webkitfullscreenchange', handleFullscreenChange);
      document.removeEventListener('msfullscreenchange', handleFullscreenChange);
    };
  }, []);

  return { enterFullscreen, exitFullscreen, isFullscreen };
};

export default useFullscreen;
```

In the above code, we define our `useFullscreen` hook that takes a `ref` as an argument. Inside the hook, we create helper functions `enterFullscreen` and `exitFullscreen` which will be responsible for toggling fullscreen mode. We also include an `isFullscreen` state variable to keep track of the current fullscreen state.

We then set up event listeners in the `useEffect` hook to detect changes in fullscreen mode and update the `isFullscreen` state accordingly. Finally, we return the necessary functions and state values from the hook.

## Using the useFullscreen hook
Now that we have our `useFullscreen` hook, we can use it in our React component to toggle fullscreen mode for a specific element.

```jsx
import React, { useRef } from 'react';
import useFullscreen from './hooks/useFullscreen';

const App = () => {
  const elementRef = useRef(null);
  const { enterFullscreen, exitFullscreen, isFullscreen } = useFullscreen(elementRef);

  return (
    <div>
      <div ref={elementRef}>
        {/* Your content here */}
      </div>
      <button onClick={isFullscreen ? exitFullscreen : enterFullscreen}>
        {isFullscreen ? 'Exit Fullscreen' : 'Enter Fullscreen'}
      </button>
    </div>
  );
};

export default App;
```

In this example, we create a `div` element and assign it a `ref` using the `useRef` hook. We then pass the `elementRef` to our `useFullscreen` hook, which handles enabling and disabling fullscreen mode for that element.

Finally, we render a button that toggles fullscreen mode based on the `isFullscreen` value returned by the `useFullscreen` hook.

## Conclusion
In this blog post, we explored how to create a custom `useFullscreen` hook in React. This hook allows us to easily toggle fullscreen mode for a specific element in our application.

By encapsulating the logic in a reusable hook, we can easily incorporate fullscreen functionality into any React component, enhancing the user experience and providing a more immersive interface. Happy coding!

#seo #react #hook #fullscreen #mode