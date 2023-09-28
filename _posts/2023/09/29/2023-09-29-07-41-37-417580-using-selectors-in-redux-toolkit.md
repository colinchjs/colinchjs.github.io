---
layout: post
title: "Using selectors in Redux Toolkit"
description: " "
date: 2023-09-29
tags: [redux, selectors]
comments: true
share: true
---

To use selectors in Redux Toolkit, you first need to define them using the `createSlice` or `createReducer` functions. Let's look at an example of how to use selectors in a Redux Toolkit setup.

Assume we have a slice of state called `todos` with an array of todo objects, each having a `completed` property. We want to create a selector that returns only the completed todos.

```javascript
import { createSlice } from '@reduxjs/toolkit';

const todosSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => {
      state.push(action.payload);
    },
    markTodoComplete: (state, action) => {
      const { id } = action.payload;
      const todo = state.find(todo => todo.id === id);
      if (todo) {
        todo.completed = true;
      }
    },
  },
});

export const { addTodo, markTodoComplete } = todosSlice.actions;

// Selector to get completed todos
export const selectCompletedTodos = state =>
  state.todos.filter(todo => todo.completed);

export default todosSlice.reducer;
```

In the above example, we define a selector `selectCompletedTodos` that takes in the Redux state and returns an array of completed todos. It filters the `todos` array and returns only the todos where `completed` is `true`.

To use this selector in a React component, you can utilize the `useSelector` hook provided by the `react-redux` library:

```javascript
import { useSelector } from 'react-redux';
import { selectCompletedTodos } from './todosSlice';

const CompletedTodosList = () => {
  const completedTodos = useSelector(selectCompletedTodos);

  return (
    <ul>
      {completedTodos.map(todo => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
};

export default CompletedTodosList;
```

In the example above, we import the `selectCompletedTodos` selector and use it with the `useSelector` hook to retrieve the relevant data from the Redux state. Then, we map over the `completedTodos` array to render a list of completed todos.

With selectors, you can easily compute and retrieve derived data from your Redux state, keeping your code more organized and efficient. They are a valuable tool when working with complex application states and can help improve the performance of your application.

#redux #selectors