---
layout: post
title: "React.js hooks: useEffect"
description: " "
date: 2023-09-25
tags: [reactjs, useEffect]
comments: true
share: true
---

React.js is a popular JavaScript library for building user interfaces. One of the key features in React.js is the ability to work with hooks, which allow us to manage state and perform side effects within functional components. One of the most commonly used hooks is useEffect.

## What is useEffect?

`useEffect` is a hook in React.js that allows us to perform side effects in functional components. Side effects in this context refer to any function that has an effect outside of the component's scope, such as updating the DOM, making HTTP requests, subscribing to events, or setting up timers.

## How to use useEffect?

To use `useEffect`, we need to import it from the `react` package:

```javascript
import React, { useEffect } from 'react';
```

We can then use `useEffect` within our functional component to declare any side effects we want to perform. The `useEffect` function takes two parameters: a callback function and an optional dependencies array.

Here's an example of how to use `useEffect` to fetch data from an API when the component mounts:

```javascript
import React, { useEffect, useState } from 'react';

function MyComponent() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data));
  }, []);

  return (
    <div>
      {/* Render the fetched data */}
    </div>
  );
}

export default MyComponent;
```

In this example, the `useEffect` hook is called with a callback function that fetches data from an API using the `fetch` function. The fetched data is then stored in the component's state using the `setData` function. The empty dependencies array `[]` ensures that the side effect is only executed once when the component mounts.

## Cleaning up side effects

`useEffect` also provides a mechanism to clean up after the side effect. The callback function can return a cleanup function that will be called when the component unmounts or before the next side effect is executed.

Here's an example of how to use a cleanup function:

```javascript
useEffect(() => {
  // Perform side effect
  return () => {
    // Clean up side effect
  };
}, []);
```

In this example, the cleanup function is returned from the callback function. This function can be used to clean up any resources used by the side effect, such as closing timers or unsubscribing from events.

## Conclusion

The `useEffect` hook in React.js is a powerful tool for managing side effects in functional components. It allows us to perform tasks like fetching data, updating the DOM, or setting up timers. By using `useEffect` correctly, we can ensure our components are efficient and performant.

#reactjs #useEffect