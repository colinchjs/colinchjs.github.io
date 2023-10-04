---
layout: post
title: "Basics of JavaScript Redux"
description: " "
date: 2023-09-29
tags: [redux]
comments: true
share: true
---

JavaScript Redux is a popular library that helps manage the state of web applications. It is a predictable state container that ensures the consistency of data throughout the application. In this blog post, we will cover the basics of JavaScript Redux and how to get started with it.

## Installation

To use Redux in your JavaScript project, you need to install it first. You can install Redux using npm by running the following command:

```
npm install redux
```

Once installed, you can import Redux into your project using the `require` or `import` statements.

## Store

The **store** is at the heart of Redux. It is an object that holds the application state. You can create a store by calling the `createStore` function from the Redux library. For example:

```javascript
const { createStore } = require('redux');

const initialState = {
  counter: 0,
};

const reducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { counter: state.counter + 1 };
    case 'DECREMENT':
      return { counter: state.counter - 1 };
    default:
      return state;
  }
};

const store = createStore(reducer);
```

In the code snippet above, we first define the *initial state* of our application. Then, we create a *reducer* function that specifies how the state should change in response to different *actions*. The reducer takes in the current state and an action object, and returns a new state based on the action type.

We pass the reducer function as an argument to the `createStore` function to create the store. The store holds the state of the application and provides methods to interact with it.

## Actions

**Actions** are payloads of information that send data from the application to the store. An action is a plain JavaScript object that must have a `type` property indicating the type of action being performed. For example:

```javascript
const increment = () => {
  return {
    type: 'INCREMENT',
  };
};

const decrement = () => {
  return {
    type: 'DECREMENT',
  };
};
```

In the code snippet above, we have defined two action creators `increment` and `decrement`. These functions return action objects with the appropriate type.

## Dispatching Actions

To update the state in the store, we need to **dispatch** actions. Dispatching an action is done by calling the `dispatch` method provided by the store. For example:

```javascript
store.dispatch(increment());
store.dispatch(decrement());
```

In the code snippet above, we dispatch the `increment` and `decrement` actions to update the state in the store.

## Subscribing to Store Updates

Redux provides a method called `subscribe` that allows us to listen for changes to the store. You can call `subscribe` and pass a callback function that will be called whenever the state changes. For example:

```javascript
const unsubscribe = store.subscribe(() => {
  console.log(store.getState());
});
```

In the code snippet above, we subscribe to store updates by providing a callback function that logs the current state to the console. The `subscribe` method returns a function that can be called to unsubscribe from further store updates.

## Conclusion

In this blog post, we covered the basics of JavaScript Redux. We learned how to create a store, define actions, dispatch them, and subscribe to store updates. Understanding these fundamental concepts will help you build scalable and maintainable web applications using Redux.

#javascript #redux