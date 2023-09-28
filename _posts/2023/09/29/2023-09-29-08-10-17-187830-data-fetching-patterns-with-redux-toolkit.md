---
layout: post
title: "Data fetching patterns with Redux Toolkit"
description: " "
date: 2023-09-29
tags: [redux, datafetching]
comments: true
share: true
---

In a modern web application, it is common to retrieve and display data from an API. Redux Toolkit, the official Redux package, provides a simplified approach to managing state in a React application. In this article, we will explore different data fetching patterns with Redux Toolkit, which can enhance the performance and user experience of your application.

## 1. Basic data fetching using async thunk

Redux Toolkit integrates **async thunks** to handle asynchronous actions. Thunks allow us to write async logic in Redux actions, making it easier to fetch data from an API.

To implement basic data fetching using async thunks, follow these steps:

1. Define a thunk function that dispatches an action to fetch data.

```javascript
import { createAsyncThunk } from '@reduxjs/toolkit';
import api from 'api'; // import your API request library

export const fetchData = createAsyncThunk('data/fetchData', async () => {
  const response = await api.getData(); // Call your API function here
  return response.data;
});
```

2. Create a slice that handles the state and reducers.

```javascript
import { createSlice } from '@reduxjs/toolkit';

const dataSlice = createSlice({
  name: 'data',
  initialState: {
    items: [],
    loading: false,
    error: null,
  },
  reducers: {},
  extraReducers: (builder) => {
    builder
      .addCase(fetchData.pending, (state) => {
        state.loading = true;
      })
      .addCase(fetchData.fulfilled, (state, action) => {
        state.loading = false;
        state.items = action.payload;
      })
      .addCase(fetchData.rejected, (state, action) => {
        state.loading = false;
        state.error = action.error.message;
      });
  },
});

export default dataSlice.reducer;
```

3. Use the `useDispatch` and `useSelector` hooks from the `react-redux` package to dispatch the `fetchData` action and access the fetched data in a component.

```javascript
import { useDispatch, useSelector } from 'react-redux';
import { fetchData } from 'path/to/fetchDataSlice';

const MyComponent = () => {
  const dispatch = useDispatch();
  const data = useSelector((state) => state.data.items);
  const loading = useSelector((state) => state.data.loading);

  useEffect(() => {
    dispatch(fetchData());
  }, [dispatch]);

  if (loading) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      {data.map((item) => (
        <div key={item.id}>{item.name}</div>
      ))}
    </div>
  );
};
```

## 2. Intelligent data fetching with caching

To avoid unnecessary API calls and optimize performance, we can introduce **caching** in data fetching. Redux Toolkit provides a built-in caching mechanism called **RTK Query**.

To implement intelligent data fetching with caching using RTK Query, follow these steps:

1. Set up RTK Query by creating an `api` slice using the `createApi` function.

```javascript
import { createApi, fetchBaseQuery } from '@reduxjs/toolkit/query/react';

const api = createApi({
  baseQuery: fetchBaseQuery({ baseURL: '/api' }), // Configure your base URL
  endpoints: (builder) => ({
    getData: builder.query({
      query: () => 'data', // Customize your API endpoint
    }),
  }),
});

export const { useGetDataQuery } = api;
export default api;
```

2. Use the generated `useGetDataQuery` hook to make the API call and retrieve the data.

```javascript
import { useGetDataQuery } from 'path/to/apiSlice';

const MyComponent = () => {
  const { data, error, isLoading } = useGetDataQuery();

  if (isLoading) {
    return <div>Loading...</div>;
  }

  if (error) {
    return <div>Error: {error.message}</div>;
  }

  return (
    <div>
      {data.map((item) => (
        <div key={item.id}>{item.name}</div>
      ))}
    </div>
  );
};
```

Using intelligent data fetching with caching improves the user experience by minimizing API calls and efficiently managing data in your application.

## Conclusion

Redux Toolkit provides powerful tools to simplify data fetching in a React application. Whether you need to handle basic data fetching using async thunks or implement intelligent data caching with RTK Query, Redux Toolkit has got you covered. By using these patterns, you can enhance the performance and user experience of your application while maintaining a clean and organized codebase.

#redux #datafetching