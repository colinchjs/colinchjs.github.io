---
layout: post
title: "Handling media queries with a custom useMediaQuery hook"
description: " "
date: 2023-10-11
tags: [webdevelopment, reactjs]
comments: true
share: true
---

## Table of Contents
- [Introduction to useMediaQuery](#introduction-to-useMediaQuery)
- [Implementing the useMediaQuery Hook](#implementing-the-useMediaQuery-hook)
- [Using the useMediaQuery Hook](#using-the-useMediaQuery-hook)
- [Conclusion](#conclusion)

## Introduction to useMediaQuery
The `useMediaQuery` hook allows us to determine if a particular media query matches the current viewport. With this information, we can conditionally render components or apply different styles based on the viewport size.

## Implementing the useMediaQuery Hook
Create a new file called `useMediaQuery.js` and define the `useMediaQuery` hook:

```javascript
import { useState, useEffect } from 'react';

const useMediaQuery = (query) => {
  const [matches, setMatches] = useState(false);

  useEffect(() => {
    const mediaQuery = window.matchMedia(query);
    const listener = (event) => {
      setMatches(event.matches);
    };

    mediaQuery.addEventListener('change', listener);

    // Initial check
    setMatches(mediaQuery.matches);

    return () => {
      mediaQuery.removeEventListener('change', listener);
    };
  }, [query]);

  return matches;
};

export default useMediaQuery;
```

The `useMediaQuery` hook takes a `query` string as input and returns a boolean value indicating whether the query matches the current viewport.

## Using the useMediaQuery Hook
Let's see how to use the `useMediaQuery` hook in a React component. Assume we want to render a different message based on whether the viewport width is less than 768 pixels.

```javascript
import React from 'react';
import useMediaQuery from './useMediaQuery';

const MyComponent = () => {
  const isSmallScreen = useMediaQuery('(max-width: 768px)');

  return (
    <div>
      {isSmallScreen ? (
        <p>This is a small screen</p>
      ) : (
        <p>This is a large screen</p>
      )}
    </div>
  );
};

export default MyComponent;
```

In this example, the `isSmallScreen` variable will be `true` if the viewport width is less than or equal to 768 pixels.

## Conclusion
The custom `useMediaQuery` hook simplifies the handling of media queries in React applications. It provides a convenient way to conditionally render components or apply different styles based on the viewport size. By using JavaScript to handle media queries, we have greater control over the behavior of our responsive layouts.

#webdevelopment #reactjs