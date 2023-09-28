---
layout: post
title: "Using Redux Toolkit with React"
description: " "
date: 2023-09-29
tags: [Redux, React]
comments: true
share: true
---

Redux Toolkit is a powerful library that simplifies the usage of Redux in React applications. It provides a set of tools and conventions that eliminate many common pain points when working with Redux.

## Getting Started

To get started with Redux Toolkit, first, make sure you have a React application set up. If not, you can create one using `create-react-app`. Then, follow these steps:

1. Install Redux Toolkit and its dependencies by running the following command:

```bash
npm install @reduxjs/toolkit react-redux
```

2. Create a new file called `store.js` in your project's directory. This file will contain the store configuration and all your Redux logic.

3. Open `store.js` and import the necessary dependencies:

```javascript
import { configureStore } from "@reduxjs/toolkit";
```

4. Define your initial state and create a reducer function using the `createSlice` function provided by Redux Toolkit:

```javascript
const initialState = {
  counter: 0,
};

const counterSlice = createSlice({
  name: "counter",
  initialState,
  reducers: {
    increment(state) {
      state.counter++;
    },
    decrement(state) {
      state.counter--;
    },
  },
});
```

5. Create the Redux store by calling the `configureStore` function and passing in your reducer:

```javascript
const store = configureStore({
  reducer: counterSlice.reducer,
});
```

6. Wrap your app component with the `Provider` component from `react-redux` and pass it the `store` as a prop:

```javascript
import { Provider } from "react-redux";

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById("root")
);
```

7. Now you can access the Redux store in your components. To use the store, import the `useDispatch` and `useSelector` hooks provided by the `react-redux` library:

```javascript
import { useDispatch, useSelector } from "react-redux";
```

8. To dispatch actions, use the `useDispatch` hook and call your action creator functions defined in your slice:

```javascript
const dispatch = useDispatch();

const handleIncrement = () => {
  dispatch(counterSlice.actions.increment());
};

const handleDecrement = () => {
  dispatch(counterSlice.actions.decrement());
};
```

9. To access the state from the store, use the `useSelector` hook and pass in the appropriate selector function:

```javascript
const counter = useSelector((state) => state.counter);
```

## Conclusion

Redux Toolkit simplifies the process of using Redux with React by providing a set of opinionated tools and conventions. It helps eliminate boilerplate code and makes state management more straightforward and efficient. By following the steps above, you can easily integrate Redux Toolkit into your React application and leverage its benefits. Start using Redux Toolkit today and enhance your React app's state management capabilities!

## #Redux #React