---
layout: post
title: "Setting up Redux Toolkit in a JavaScript project"
description: " "
date: 2023-09-29
tags: [redux, reduxtoolkit]
comments: true
share: true
---

In JavaScript projects, Redux is a commonly used state management library. However, setting up Redux and managing its boilerplate code can be cumbersome and time-consuming. That's where **Redux Toolkit** comes in handy. 

## What is Redux Toolkit?

**Redux Toolkit** is the official recommended way to write Redux logic. It is a set of opinionated tools and utilities that simplifies the process of creating, configuring, and managing Redux stores. It helps reduce boilerplate code and makes Redux development more efficient.

## Step-by-step guide for setting up Redux Toolkit

### Step 1: Install Redux Toolkit

Start by installing Redux Toolkit into your project. You can do this using npm or yarn:

```shell
npm install @reduxjs/toolkit
```

or

```shell
yarn add @reduxjs/toolkit
```

### Step 2: Create a Redux Slice

A Redux slice represents a specific part of your Redux state and contains the actions and reducers associated with that part. Create a new file called `counterSlice.js` and define your first Redux slice.

```javascript
// counterSlice.js

import { createSlice } from '@reduxjs/toolkit';

const counterSlice = createSlice({
  name: 'counter',
  initialState: 0,
  reducers: {
    increment: (state) => state + 1,
    decrement: (state) => state - 1,
  },
});

export const { increment, decrement } = counterSlice.actions;
export default counterSlice.reducer;
```

### Step 3: Create a Redux Store

Create a Redux store using the `configureStore` function provided by Redux Toolkit. Import the created reducer from the slice file and pass it as an argument to `configureStore`.

```javascript
// store.js

import { configureStore } from '@reduxjs/toolkit';
import counterReducer from './counterSlice';

const store = configureStore({
  reducer: {
    counter: counterReducer,
  },
});

export default store;
```

### Step 4: Connect Redux Store to the App

To use the Redux store in your application, wrap your root component with the `Provider` component from the `react-redux` library. Import the store and wrap your app.

```javascript
// index.js

import React from 'react';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

That's it! You have successfully set up Redux Toolkit in your JavaScript project. Now, you can start using the `increment` and `decrement` actions provided by your counter slice to manage the state.

Remember to import the necessary functions, components, and files as shown in the code examples.

#redux #reduxtoolkit