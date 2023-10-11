---
layout: post
title: "Creating a custom usePrevious hook for getting previous state or props"
description: " "
date: 2023-10-11
tags: [react, hooks]
comments: true
share: true
---

When working with React hooks, you may often come across situations where you need to access the previous state or props in a functional component. While React provides a way to access the previous props via the `componentDidUpdate` lifecycle method, there is no built-in way to get the previous state in functional components.

To overcome this limitation, we can create a custom hook called `usePrevious` that allows us to store and retrieve the previous state or props. Let's dive into the implementation.

## Setting up the Hook

To create the `usePrevious` hook, we'll follow these steps:

1. Import the necessary hooks from the React library.
2. Define a function called `usePrevious` that takes an argument (state or props).
3. Inside the `usePrevious` function, use the `useState` hook to create a variable called `previous` and its corresponding setter function.
4. Use the `useEffect` hook with a dependency array containing the value being passed to `usePrevious`.
5. In the effect callback, update the `previous` state to the current value of the state or props argument.

```javascript
import { useState, useEffect } from 'react';

function usePrevious(value) {
  const [previous, setPrevious] = useState();

  useEffect(() => {
    setPrevious(value);
  }, [value]);

  return previous;
}
```

## How to Use the usePrevious Hook

Once we have our custom hook, we can use it in any functional component to access the previous state or props. Here's an example of how to use it:

```javascript
import React, { useState } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);
  const previousCount = usePrevious(count);

  return (
    <div>
      <p>Current Count: {count}</p>
      <p>Previous Count: {previousCount}</p>
      
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
```

In the above example, we have a component called `MyComponent` that tracks a count state using the `useState` hook. We use the `usePrevious` hook to assign the previous value of `count` to the `previousCount` variable.

Now, whenever the count value changes, the `previousCount` will be updated with the previous value of `count`. This allows us to track changes in state and use the previous value for comparison or any other required logic.

## Conclusion

Creating a custom `usePrevious` hook can be a handy way to access the previous state or props in functional components. It provides a simple and reusable solution to track state changes, allowing for more flexible component logic. Remember to utilize this hook whenever you need to access the previous state or props in your React applications.

#react #hooks