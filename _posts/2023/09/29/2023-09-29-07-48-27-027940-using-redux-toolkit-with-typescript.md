---
layout: post
title: "Using Redux Toolkit with TypeScript"
description: " "
date: 2023-09-29
tags: [redux, typescript]
comments: true
share: true
---

## Introduction

In this blog post, we will explore how to use Redux Toolkit with TypeScript to simplify state management in your React applications. Redux Toolkit is the official recommended way to write Redux logic, and with TypeScript, you can achieve compile-time type safety and enhanced developer experience.

## Prerequisites

Before we begin, make sure you have the following:

1. Basic knowledge of Redux and TypeScript.
2. A React application set up with TypeScript and Redux.

If you're new to Redux or need help setting up a React app with TypeScript and Redux, refer to the Redux documentation and TypeScript documentation respectively.

## Install Redux Toolkit

To start using Redux Toolkit with TypeScript, you need to install the required packages. Open your terminal and navigate to your project directory. Run the following command:

```bash
npm install @reduxjs/toolkit react-redux
```

This will install both Redux Toolkit and React Redux packages.

## Creating a Redux Store

Let's start by creating a Redux store with TypeScript. In a typical Redux setup, you need to define the store, reducers, and actions separately. However, Redux Toolkit simplifies this process.

Create a new file `store.ts` and add the following code:

```typescript
import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export type RootState = ReturnType<typeof store.getState>;

export default store;
```

Here, we are using the `configureStore` function from Redux Toolkit to create our store. We also imported a `counterReducer` from `counterSlice` file which we will create next.

## Creating a Slice

In Redux Toolkit, a **slice** is a single file that contains all the reducer logic, action creators, and action types. It helps in organizing and managing your Redux code.

Create a new file `counterSlice.ts` and add the following code:

```typescript
import { createSlice, PayloadAction } from '@reduxjs/toolkit';

interface CounterState {
  value: number;
}

const initialState: CounterState = {
  value: 0,
};

const counterSlice = createSlice({
  name: 'counter',
  initialState,
  reducers: {
    increment: (state) => {
      state.value++;
    },
    decrement: (state) => {
      state.value--;
    },
    incrementByAmount: (state, action: PayloadAction<number>) => {
      state.value += action.payload;
    },
  },
});

export const { increment, decrement, incrementByAmount } = counterSlice.actions;

export default counterSlice.reducer;
```

In this example, we define the initial state of the counter and create three reducers: `increment`, `decrement`, and `incrementByAmount`. Each reducer handles the state mutation based on the dispatched action.

## Using the Redux Store in a Component

Now that we have set up our Redux store and created a slice, let's use them in a React component.

```tsx
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { RootState, increment, decrement, incrementByAmount } from './store';

const Counter = () => {
  const counter = useSelector((state: RootState) => state.counter.value);
  const dispatch = useDispatch();

  const handleIncrement = () => {
    dispatch(increment());
  };

  const handleDecrement = () => {
    dispatch(decrement());
  };

  const handleIncrementByAmount = () => {
    dispatch(incrementByAmount(5));
  };

  return (
    <div>
      <h2>Counter: {counter}</h2>
      <button onClick={handleIncrement}>Increment</button>
      <button onClick={handleDecrement}>Decrement</button>
      <button onClick={handleIncrementByAmount}>Increment by 5</button>
    </div>
  );
};

export default Counter;
```

In this example, we use the `useSelector` hook to access the counter value from the store, and the `useDispatch` hook to dispatch actions. We then define handlers for each button click, which dispatch the corresponding action.

## Conclusion

In this blog post, we have learned how to use Redux Toolkit with TypeScript to simplify state management in React apps. By using Redux Toolkit's `configureStore` function and creating a slice, we can streamline our Redux code and achieve better type safety with TypeScript.

By following the steps outlined in this post, you should now have a good understanding of how to set up and use Redux Toolkit with TypeScript in your own projects.

#redux #typescript #react #redux-toolkit