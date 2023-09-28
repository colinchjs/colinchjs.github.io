---
layout: post
title: "Building a CRUD application with Redux Toolkit"
description: " "
date: 2023-09-29
tags: [redux, react]
comments: true
share: true
---

In this tutorial, we will walk through the process of building a CRUD (Create, Read, Update, Delete) application using Redux Toolkit. Redux Toolkit is a powerful toolset that simplifies the management of state in React applications.

## Prerequisites

To follow along with this tutorial, you should have basic knowledge of React and Redux. It is also helpful to have a working development environment with Node.js and npm (or yarn) installed.

## Setting up the Project

To start, let's create a new React project using [Create React App](https://create-react-app.dev/):

```bash
npx create-react-app redux-crud-app
cd redux-crud-app
```

Next, install the necessary dependencies:

```bash
npm install redux react-redux @reduxjs/toolkit
```

## Creating Redux Actions and Reducers

We will begin by defining our actions and reducers. Create a new directory called `features` inside the `src` folder. Inside the `features` directory, create a new file called `todosSlice.js`. In this file, let's define our actions and reducers for managing todos.

```javascript
// src/features/todosSlice.js

import { createSlice } from '@reduxjs/toolkit';

const todosSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => {
      state.push(action.payload);
    },
    removeTodo: (state, action) => {
      const index = state.findIndex(todo => todo.id === action.payload);
      state.splice(index, 1);
    },
    updateTodo: (state, action) => {
      const { id, text } = action.payload;
      const todo = state.find(todo => todo.id === id);
      if (todo) {
        todo.text = text;
      }
    },
  },
});

export const { addTodo, removeTodo, updateTodo } = todosSlice.actions;

export default todosSlice.reducer;
```

In this code snippet, we create a slice using `createSlice` from Redux Toolkit. The slice contains the name of the slice (`todos`), the initial state, and the reducer functions for adding, removing, and updating todos.

## Setting up the Redux Store

Now that we have our actions and reducers defined, let's set up the Redux store. Create a new file called `store.js` in the `src` directory and add the following code:

```javascript
// src/store.js

import { configureStore } from '@reduxjs/toolkit';
import todosReducer from './features/todosSlice';

const store = configureStore({
  reducer: {
    todos: todosReducer,
  },
});

export default store;
```

The code above creates a Redux store using `configureStore` from Redux Toolkit. We provide our `todosReducer` as the reducer for the `todos` slice.

## Integrating Redux with React

To integrate Redux with our React application, we need to wrap our App component with the Redux Provider. Open the `src/index.js` file and modify it as follows:

```javascript
// src/index.js

import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import App from './App';
import store from './store';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

## Using Redux State in Components

Now, we can start using the Redux state in our components. In a new file called `TodoList.js` inside the `src` directory, add the following code:

```javascript
// src/TodoList.js

import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { removeTodo, updateTodo } from './features/todosSlice';

const TodoList = () => {
  const todos = useSelector(state => state.todos);
  const dispatch = useDispatch();

  const handleDelete = id => {
    dispatch(removeTodo(id));
  };

  const handleUpdate = (id, newText) => {
    dispatch(updateTodo({ id, text: newText }));
  };

  return (
    <div>
      {todos.map(todo => (
        <div key={todo.id}>
          <span>{todo.text}</span>
          <button onClick={() => handleDelete(todo.id)}>Delete</button>
          <input
            type="text"
            value={todo.text}
            onChange={e => handleUpdate(todo.id, e.target.value)}
          />
        </div>
      ))}
    </div>
  );
};

export default TodoList;
```

In this code snippet, we use the `useSelector` and `useDispatch` hooks from `react-redux` to access the todos from the Redux state and dispatch actions to modify the state.

## Conclusion

Congratulations! You have successfully built a CRUD application using Redux Toolkit. Redux Toolkit provides a simplified and efficient way to manage state in your React applications. With this foundation, you can now expand and enhance your application's functionality.

Make sure to check out the official documentation for [Redux Toolkit](https://redux-toolkit.js.org/) for more advanced usage and features.

#redux #react-redux