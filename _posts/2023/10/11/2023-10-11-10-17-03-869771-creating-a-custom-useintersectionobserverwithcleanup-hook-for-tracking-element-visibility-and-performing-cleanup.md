---
layout: post
title: "Creating a custom useIntersectionObserverWithCleanup hook for tracking element visibility and performing cleanup"
description: " "
date: 2023-10-11
tags: [React, IntersectionObserver]
comments: true
share: true
---

In this tutorial, we will learn how to create a custom React hook called `useIntersectionObserverWithCleanup` that allows us to track the visibility of an element using the Intersection Observer API and perform any necessary cleanup when the element is no longer visible. This is especially useful when working with infinite scroll or lazy loading functionality.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setting up the Project](#setting-up-the-project)
- [Implementing the Custom Hook](#implementing-the-custom-hook)
- [Using the Custom Hook](#using-the-custom-hook)
- [Conclusion](#conclusion)

## Prerequisites

To follow along with this tutorial, you should have a basic understanding of React hooks and functional components. Additionally, make sure you have a React project set up with the necessary dependencies.

## Setting up the Project

Start by creating a new React project using Create React App or any other method of your choice. Open a terminal and run the following command:

```bash
npx create-react-app intersection-observer-example
```

Once the project is set up, navigate to the project directory:

```bash
cd intersection-observer-example
```

## Implementing the Custom Hook

Create a new file called `useIntersectionObserverWithCleanup.js` in the `src` directory. This file will contain the implementation of our custom hook.

Start by defining the custom hook function:

```javascript
import React, { useEffect, useState, useRef } from 'react';

const useIntersectionObserverWithCleanup = (target, options, callback, cleanup) => {
  // ...
};

export default useIntersectionObserverWithCleanup;
```

Inside the custom hook function, we will use the `useRef` hook to create a reference for the target element, `useState` to keep track of the intersection observer, and `useEffect` to handle the intersection observer setup and cleanup.

```javascript
const useIntersectionObserverWithCleanup = (target, options, callback, cleanup) => {
  const observerRef = useRef(null);
  const [isIntersecting, setIsIntersecting] = useState(false);

  useEffect(() => {
    const observer = new IntersectionObserver(([entry]) => {
      setIsIntersecting(entry.isIntersecting);
      if (entry.isIntersecting) {
        callback();
      }
    }, options);

    observer.observe(target);
    observerRef.current = observer;

    return () => {
      observer.disconnect();
      cleanup();
    };
  }, [target, options, callback, cleanup]);

  return isIntersecting;
};
```

In the example above, we create a new instance of the Intersection Observer inside the `useEffect` hook. The callback function is executed whenever the target element intersect or stop intersecting with the viewport. Finally, we disconnect the observer and perform any necessary cleanup when the component unmounts.

## Using the Custom Hook

To demonstrate the usage of our custom hook, let's create a simple component called `ExampleComponent` that will make use of the `useIntersectionObserverWithCleanup` hook.

In your `App.js` file, replace the existing content with the following code:

```javascript
import React from 'react';
import ExampleComponent from './ExampleComponent';

function App() {
  return (
    <div>
      <h1>Intersection Observer Custom Hook Example</h1>
      <ExampleComponent />
    </div>
  );
}

export default App;
```

Create a new file called `ExampleComponent.js` in the `src` directory and add the following code:

```javascript
import React, { useCallback } from 'react';
import useIntersectionObserverWithCleanup from './useIntersectionObserverWithCleanup';

const ExampleComponent = () => {
  const callback = useCallback(() => {
    console.log('Element is visible!');
  }, []);

  const cleanup = useCallback(() => {
    console.log('Cleanup code here...');
  }, []);

  const isVisible = useIntersectionObserverWithCleanup(null, null, callback, cleanup);

  return (
    <div>
      <h2>Example Component</h2>
      <div style={{ height: '1000px' }}>
        <div style={{ height: '50px', background: 'red' }} ref={isVisible && callback}></div>
      </div>
    </div>
  );
};

export default ExampleComponent;
```

In the `ExampleComponent` component, we define the `callback` function that will be executed when the target element intersects with the viewport, and the `cleanup` function that will be executed when the component unmounts or the target element is no longer visible. We pass these functions along with `null` values for the target and options parameters to the `useIntersectionObserverWithCleanup` hook.

Lastly, we create a `div` element with a red background that acts as our target element. The `isVisible` flag returned from the hook determines whether the callback function should be applied as the ref of the target element, making it visible or not based on its visibility.

## Conclusion

In this tutorial, we have created a custom React hook called `useIntersectionObserverWithCleanup` that allows us to track the visibility of an element using the Intersection Observer API and perform any necessary cleanup when the element is no longer visible. This hook can be a powerful tool for implementing infinite scroll or lazy loading functionality in your React applications.

Feel free to explore and expand upon this hook to suit your specific needs. Happy coding!

---
Tags: #React #IntersectionObserver #CustomHook