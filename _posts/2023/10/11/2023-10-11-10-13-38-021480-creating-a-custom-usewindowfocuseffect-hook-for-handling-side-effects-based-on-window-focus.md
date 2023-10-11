---
layout: post
title: "Creating a custom useWindowFocusEffect hook for handling side effects based on window focus"
description: " "
date: 2023-10-11
tags: [React, CustomHooks]
comments: true
share: true
---

In this blog post, we will explore how to create a custom React hook called `useWindowFocusEffect`. This hook will allow us to easily handle any side effects that depend on the focus of the window.

## Table of Contents
- [Introduction](#introduction)
- [Implementation](#implementation)
- [Usage](#usage)
- [Conclusion](#conclusion)

## Introduction

In web application development, there are often cases where we want to trigger certain actions when the browser window gains or loses focus. This can be useful for pausing video playback, updating real-time data, or adding visual indicators to the user interface.

By using the provided `useEffect` hook in React, we can create a custom hook that encapsulates the logic for subscribing and unsubscribing to the window focus event.

## Implementation

Here's an example of how we can implement the `useWindowFocusEffect` hook:

```javascript
import React, { useEffect } from 'react';

const useWindowFocusEffect = (callback) => {
  useEffect(() => {
    const handleFocus = () => callback(true);
    const handleBlur = () => callback(false);

    window.addEventListener('focus', handleFocus);
    window.addEventListener('blur', handleBlur);

    return () => {
      window.removeEventListener('focus', handleFocus);
      window.removeEventListener('blur', handleBlur);
    };
  }, [callback]);
};

export default useWindowFocusEffect;
```

In the above code, we define a custom hook `useWindowFocusEffect` that accepts a `callback` function as a parameter. We then set up event listeners for the `'focus'` and `'blur'` events on the `window` object. When the focus event occurs, the `callback` function is called with `true` as the argument, indicating that the window is in focus. Similarly, when the blur event occurs, the `callback` function is called with `false`.

We also include a cleanup function in the `useEffect` hook's return statement to remove the event listeners when the component using this hook is unmounted.

## Usage

To use the `useWindowFocusEffect` hook in a component, simply import it and call it inside your functional component, providing the necessary callback function. Here's an example:

```javascript
import React, { useState } from 'react';
import useWindowFocusEffect from './useWindowFocusEffect';

const App = () => {
  const [isWindowFocused, setIsWindowFocused] = useState(true);

  useWindowFocusEffect(setIsWindowFocused);

  return (
    <div>
      {isWindowFocused ? (
        <p>The window is in focus</p>
      ) : (
        <p>The window is not in focus</p>
      )}
    </div>
  );
};

export default App;
```

In the above example, we create a basic React component `App` that renders a message based on the value of the `isWindowFocused` state. We pass the `setIsWindowFocused` function as the callback to the `useWindowFocusEffect` hook. This allows the state to be updated whenever the window gains or loses focus, resulting in a re-render of the component.

## Conclusion

Creating a custom hook like `useWindowFocusEffect` allows us to abstract away the complexity of handling window focus logic and makes it easy to reuse this functionality across different components in our React applications. By encapsulating the subscription and unsubscription to window focus events, we ensure clean and efficient code.

By using this hook, developers can easily add side effects to their applications that depend on the window focus, enhancing the user experience and improving the interaction of their web applications.

*#React #CustomHooks*