---
layout: post
title: "Creating a custom useReducer hook"
description: " "
date: 2023-10-11
tags: [react, hooks]
comments: true
share: true
---

In React, the `useReducer` hook is a powerful tool for managing complex state in functional components. It allows you to update state in a predictable way by dispatching actions to a reducer function. However, the syntax can be a bit verbose, especially if you have multiple state variables. 

In this blog post, we will explore how to create a custom `useReducer` hook that simplifies the syntax and provides a more convenient way to manage state in your components.

### The Problem with `useReducer`

First, let's take a look at the syntax of `useReducer` to understand why it can be verbose. 

```jsx
const [state, dispatch] = useReducer(reducer, initialState);
```

To update the state, you need to dispatch an action to the reducer function, which will handle the updates based on the action type.

```jsx
dispatch({ type: 'INCREMENT' });
```

This works well when you have a single state variable, but if you have multiple state variables, you need to handle each one separately.

```jsx
dispatch({ type: 'SET_NAME', payload: 'John' });
dispatch({ type: 'SET_AGE', payload: 30 });
```

This can quickly become cumbersome and error-prone, especially if you have a complex state object.

### Creating a Custom `useReducer` Hook

To simplify the syntax and provide a more convenient way to manage state, we can create a custom `useReducer` hook that encapsulates the dispatch and action creation logic.

```jsx
import { useReducer } from 'react';

function useCustomReducer(reducer, initialState) {
  const [state, dispatch] = useReducer(reducer, initialState);

  function createAction(type) {
    return (payload) => {
      dispatch({ type, payload });
    };
  }

  return [state, createAction];
}
```

With this custom hook, you can update state by creating actions using the `createAction` function. The `createAction` function takes the action type as an argument and returns an action creator function that can be called with a payload.

Let's see an example of how to use the custom `useCustomReducer` hook.

```jsx
function reducer(state, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { ...state, count: state.count + 1 };
    case 'DECREMENT':
      return { ...state, count: state.count - 1 };
    case 'SET_NAME':
      return { ...state, name: action.payload };
    default:
      return state;
  }
}

function Counter() {
  const [state, createAction] = useCustomReducer(reducer, { count: 0, name: '' });

  const increment = createAction('INCREMENT');
  const decrement = createAction('DECREMENT');
  const setName = createAction('SET_NAME');

  return (
    <div>
      <h1>{state.count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
      <input type="text" value={state.name} onChange={(e) => setName(e.target.value)} />
    </div>
  );
}
```

In this example, we define a `reducer` function that handles the state updates based on different action types. We then use the `useCustomReducer` hook to initialize the state and create the actions.

The `createAction` function is called with the action type, and it returns an action creator function. We can then use these action creator functions to update the state by dispatching the actions.

### Conclusion

By creating a custom `useReducer` hook, we can simplify the syntax and provide a more convenient way to manage state in functional components. With the custom hook, you can easily create actions and update state without the need to write dispatch calls for each state variable.

Creating custom hooks in React allows us to encapsulate complex logic and make it reusable across different components. It's a powerful tool that can enhance code readability and maintainability.

Give the custom `useCustomReducer` hook a try in your next React project and experience the benefits of simpler state management syntax. 

#react #hooks