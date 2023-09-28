---
layout: post
title: "Using Redux Toolkit in an isomorphic JavaScript application"
description: " "
date: 2023-09-29
tags: [webdevelopment, redux]
comments: true
share: true
---

Isomorphic JavaScript, also known as Universal JavaScript, allows developers to write JavaScript code that can run both on the client-side and server-side. This enables faster initial page loads and improves SEO.

In this blog post, we will explore how to use Redux Toolkit in an Isomorphic JavaScript application. Redux Toolkit is a powerful library that simplifies the process of managing state in a Redux application.

## What is Redux Toolkit?

Redux Toolkit is an opinionated, batteries-included package that provides developers with a set of tools to write Redux logic more efficiently. It includes utilities for creating Redux store, writing reducers, handling side effects, and more. These tools are designed to streamline the Redux development process and help developers write cleaner and more maintainable code.

## Setting up a Redux Store in an Isomorphic Application

To use Redux Toolkit in an isomorphic JavaScript application, we first need to set up a Redux store that can be used on both the client-side and server-side.

Here's an example of how to set up a Redux store using Redux Toolkit:

```javascript
import { configureStore } from '@reduxjs/toolkit';
import rootReducer from './reducers';

const preloadedState = // Load initial state from the server or any other source

const store = configureStore({
  reducer: rootReducer,
  preloadedState,
});

export default store;
```

In the above code, we import the `configureStore` function from Redux Toolkit and provide it with the root reducer and the preloaded state. The `preloadedState` can be populated with the initial state received from the server.

## Dispatching Actions in an Isomorphic Application

To dispatch actions in an isomorphic application, we need to make sure that the actions are executed on both the client-side and server-side. This is important to maintain the same state across the application.

```javascript
import { createAsyncThunk, createSlice } from '@reduxjs/toolkit';
import axios from 'axios';

export const fetchUsers = createAsyncThunk(
  'users/fetch',
  async () => {
    const response = await axios.get('/api/users');
    return response.data;
  }
);

const usersSlice = createSlice({
  name: 'users',
  initialState: [],
  reducers: {},
  extraReducers: (builder) => {
    builder.addCase(fetchUsers.fulfilled, (state, action) => {
      return action.payload;
    });
  },
});

export default usersSlice.reducer;
```

In the example above, we define an async thunk `fetchUsers` that makes an API call to retrieve a list of users. The response data is then added to the state using the `fulfilled` action.

## Server-side Rendering with Redux Toolkit

Server-side rendering (SSR) is a technique that allows the server to render the initial page view and send it to the client. Redux Toolkit provides tools to handle SSR easily.

```javascript
import { createEpicMiddleware } from 'redux-observable';
import { configureStore } from '@reduxjs/toolkit';
import { createMemoryHistory } from 'history';
import { renderToString } from 'react-dom/server';
import { StaticRouter } from 'react-router-dom';
import { Provider } from 'react-redux';
import { matchRoutes, renderRoutes } from 'react-router-config';
import routes from './routes';
import rootReducer from './reducers';

// Set up Redux middleware for SSR
const epicMiddleware = createEpicMiddleware();

// Create an instance of the Redux store
const store = configureStore({
  reducer: rootReducer,
  middleware: [epicMiddleware],
});

// Render the initial view on the server
const context = {};
const history = createMemoryHistory();
const appMarkup = renderToString(
  <Provider store={store}>
    <StaticRouter context={context} location={req.url}>
      {renderRoutes(routes)}
    </StaticRouter>
  </Provider>
);

// Send the rendered view to the client
res.send(`
  <html>
    <head>
      <title>My Isomorphic App</title>
    </head>
    <body>
      <div id="app">${appMarkup}</div>
      <!-- Include the serialized Redux state -->
      <script>
        window.__PRELOADED_STATE__ = ${JSON.stringify(store.getState())}
      </script>
      <!-- Include the client-side JavaScript -->
      <script src="/bundle.js"></script>
    </body>
  </html>
`);
```

In the above code, we configure the Redux store with middleware for server-side rendering. We use the `renderToString` function from `react-dom/server` to render the initial view. We also serialize the Redux state and send it to the client, allowing the client to pick up where the server left off.

## Conclusion

Using Redux Toolkit in an isomorphic JavaScript application offers a streamlined and efficient way to manage state. With the help of Redux Toolkit, setting up a Redux store, dispatching actions, and handling server-side rendering becomes a much simpler process. By following the steps outlined in this blog post, you can harness the power of Redux Toolkit to create high-performance isomorphic applications.

#webdevelopment #redux