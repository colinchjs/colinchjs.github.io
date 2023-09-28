---
layout: post
title: "Implementing pagination with Redux Toolkit"
description: " "
date: 2023-09-29
tags: [redux, pagination]
comments: true
share: true
---

## Why use Redux Toolkit for Pagination?
Redux Toolkit simplifies Redux development with its built-in utilities and recommended best practices. It includes the Redux Toolkit's `createSlice` and `createAsyncThunk`, which make it easy to handle async actions, such as fetching data for pagination.

## Setting up the Redux Store
To get started, let's set up our Redux store using Redux Toolkit. Here's an example of how you can create a slice for pagination:

```javascript
import { createSlice, createAsyncThunk } from '@reduxjs/toolkit';

const pageSize = 10; // The number of items to display per page

export const fetchPage = createAsyncThunk(
  'pagination/fetchPage',
  async (page) => {
    // Fetch data from the backend API based on the current page
    const response = await fetch(`/api/data?page=${page}&pageSize=${pageSize}`);
    const data = await response.json();
    return data;
  }
);

const paginationSlice = createSlice({
  name: 'pagination',
  initialState: {
    currentPage: 1,
    totalPages: 0,
    data: [],
    status: 'idle',
    error: null,
  },
  reducers: {
    setPage: (state, action) => {
      state.currentPage = action.payload;
    },
  },
  extraReducers: (builder) => {
    builder
      .addCase(fetchPage.pending, (state) => {
        state.status = 'loading';
      })
      .addCase(fetchPage.fulfilled, (state, action) => {
        state.status = 'succeeded';
        state.data = action.payload.data;
        state.totalPages = Math.ceil(action.payload.totalCount / pageSize);
      })
      .addCase(fetchPage.rejected, (state, action) => {
        state.status = 'failed';
        state.error = action.error.message;
      });
  },
});

export const { setPage } = paginationSlice.actions;

export default paginationSlice.reducer;
```

In this example, we define an async thunk `fetchPage` that fetches data from an API based on the current page. The `paginationSlice` manages the state for the current page, total pages, fetched data, status, and error.

## Using Pagination in a Component
Now that we have set up our Redux store, let's see how to use pagination in a React component. Here's an example of a simple component that displays paginated data:

```javascript
import React, { useEffect } from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { fetchPage, setPage } from '../redux/paginationSlice';

const PaginationComponent = () => {
  const currentPage = useSelector((state) => state.pagination.currentPage);
  const totalPages = useSelector((state) => state.pagination.totalPages);
  const data = useSelector((state) => state.pagination.data);
  const status = useSelector((state) => state.pagination.status);
  const dispatch = useDispatch();

  useEffect(() => {
    dispatch(fetchPage(currentPage));
  }, [currentPage, dispatch]);

  const handlePageChange = (newPage) => {
    dispatch(setPage(newPage));
  };

  return (
    <div>
      {status === 'loading' ? (
        <p>Loading...</p>
      ) : status === 'failed' ? (
        <p>Error: Failed to fetch data</p>
      ) : (
        <div>
          <ul>
            {data.map((item) => (
              <li key={item.id}>{item.name}</li>
            ))}
          </ul>
          <button
            disabled={currentPage === 1}
            onClick={() => handlePageChange(currentPage - 1)}
          >
            Previous
          </button>
          <button
            disabled={currentPage === totalPages}
            onClick={() => handlePageChange(currentPage + 1)}
          >
            Next
          </button>
        </div>
      )}
    </div>
  );
};

export default PaginationComponent;
```

In this component, we use the `useSelector` hook to access the relevant state values from our Redux store. The `useEffect` hook is used to fetch the data for the current page when the component mounts or when the `currentPage` changes.

The `handlePageChange` function dispatches the `setPage` action to update the current page in the Redux store. This triggers a re-fetch of the data for the new page.

Finally, we render the paginated data along with previous and next buttons that allow the user to navigate through the pages.

## Conclusion
In this blog post, we learned how to implement pagination using Redux Toolkit. Redux Toolkit simplifies the management of state in Redux applications and provides utilities such as `createSlice` and `createAsyncThunk` for handling async actions. By properly setting up your Redux store and using the provided utilities, you can easily implement pagination functionality in your application. Happy coding!

#redux #pagination #redux-toolkit