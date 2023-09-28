---
layout: post
title: "Working with Redux Toolkit slices"
description: " "
date: 2023-09-29
tags: [ReduxToolkit, ReduxSlices]
comments: true
share: true
---

Redux Toolkit is a powerful toolset that simplifies and enhances Redux application development. One of the key features of Redux Toolkit is the ability to create slices. Slices are small modules that encapsulate a portion of the Redux state and define the actions and reducers for that specific slice.

In this blog post, we will explore how to work with Redux Toolkit slices and leverage their benefits in your application development.

## Creating a slice

To create a slice using Redux Toolkit, you need to use the `createSlice` function provided by the toolkit. Here's an example of creating a slice to manage a todo list:

```javascript
import { createSlice } from '@reduxjs/toolkit';

const todoSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => {
      state.push(action.payload);
    },
    removeTodo: (state, action) => {
      return state.filter(todo => todo.id !== action.payload);
    },
    toggleTodo: (state, action) => {
      const todo = state.find(todo => todo.id === action.payload);
      if (todo) {
        todo.completed = !todo.completed;
      }
    },
  },
});

export const { addTodo, removeTodo, toggleTodo } = todoSlice.actions;
export default todoSlice.reducer;
```

In the above example, we create a slice called `todos` with an initial state of an empty array. We define three reducers: `addTodo`, `removeTodo`, and `toggleTodo`, which modify the state based on the actions dispatched.

## Using the slice in Redux store

Once you have created a slice, you can use it in your Redux store by incorporating it using the `configureStore` function provided by Redux Toolkit. Here's an example of configuring the store with the `todos` slice:

```javascript
import { configureStore } from '@reduxjs/toolkit';
import todoReducer from './todoSlice';

const store = configureStore({
  reducer: {
    todos: todoReducer,
  },
});

export default store;
```

In the above example, we import the `todoReducer` from the `todoSlice` file and include it in the `reducer` object when configuring the store using `configureStore`.

## Accessing slice state and dispatching actions

To access the slice state and dispatch actions in your components, you can use the `useSelector` and `useDispatch` hooks provided by the `react-redux` library.

```javascript
import { useSelector, useDispatch } from 'react-redux';

const TodoList = () => {
  const todos = useSelector(state => state.todos);
  const dispatch = useDispatch();

  // Dispatching addTodo action
  const handleAddTodo = () => {
    dispatch(addTodo({ id: Date.now(), text: 'New Todo', completed: false }));
  };

  return (
    <div>
      <ul>
        {todos.map(todo => (
          <li key={todo.id}>{todo.text}</li>
        ))}
      </ul>
      <button onClick={handleAddTodo}>Add Todo</button>
    </div>
  );
};
```

In the above example, we use `useSelector` to select the `todos` slice from the Redux store and assign it to the `todos` variable. We also use `useDispatch` to get the dispatch function, which allows us to dispatch actions such as `addTodo` with the required payload.

## Conclusion

Working with Redux Toolkit slices simplifies the management of Redux state and reduces boilerplate code. By encapsulating related actions and reducers within a slice, it improves code organization and modularity. With the help of slices, you can efficiently develop and manage your Redux application while leveraging the benefits provided by Redux Toolkit.

#ReduxToolkit #ReduxSlices