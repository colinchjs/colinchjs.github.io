---
layout: post
title: "Preloading data with suspense in React"
description: " "
date: 2023-10-16
tags: [react, datafetching]
comments: true
share: true
---

When building a React application, it's common to have components that need to load data from an external source, such as an API. Traditional approaches involve showing loading spinners or placeholders while waiting for the data to be fetched.

React suspense provides a more streamlined way to handle data fetching and rendering. It allows you to specify that a component should suspend rendering until the data is loaded, and shows a fallback UI in the meantime.

## Suspense for data fetching

To preload data with suspense in React, we can use the `React.lazy` function combined with `React.Suspense`. Here's an example:

```jsx
import React, { Suspense } from 'react';

const fetchData = () => {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('Data loaded!');
    }, 2000);
  });
}

const MyComponent = () => {
  const data = fetchData();

  return (
    <Suspense fallback={<div>Loading...</div>}>
      {data}
    </Suspense>
  );
}

export default MyComponent;
```

In this example, the `fetchData` function returns a promise that resolves with the data after a 2-second delay. The `MyComponent` component uses `React.Suspense` with a fallback UI (a simple "Loading..." message in this case) to handle the suspense state.

When rendering the `MyComponent`, React will automatically trigger the suspense state and show the fallback UI while waiting for the `fetchData` promise to resolve. Once the data is loaded, it will be rendered in place of the fallback UI.

## Error handling with suspense

If the data fetching encounters an error, React suspense also allows us to handle and display the error. We can use the `ErrorBoundary` component from React to catch and display the error message. Here's an updated example:

```jsx
import React, { Suspense } from 'react';

const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject('Error occurred!');
    }, 2000);
  });
}

const ErrorBoundary = ({ children }) => {
  return (
    <ErrorBoundary fallback={<div>Error occurred!</div>}>
      {children}
    </ErrorBoundary>
  );
}

const MyComponent = () => {
  const data = fetchData();

  return (
    <ErrorBoundary>
      <Suspense fallback={<div>Loading...</div>}>
        {data}
      </Suspense>
    </ErrorBoundary>
  );
}

export default MyComponent;
```

In this updated example, the `fetchData` function intentionally rejects the promise after a 2-second delay to simulate an error. The `ErrorBoundary` component handles the error and displays the fallback UI provided.

By wrapping the `Suspense` component with `ErrorBoundary`, React will catch any error thrown during the data fetching process and display the fallback UI with the error message.

## Conclusion

Using suspense for data fetching in React allows us to handle loading states and errors in a more declarative and streamlined way. By combining `React.lazy`, `React.Suspense`, and `ErrorBoundary`, we can create components that automatically handle data fetching, rendering, and error display.

Preloading data with suspense can result in a better user experience, as it reduces the need for custom loading spinners and error handling logic. It's a powerful feature that simplifies the data fetching process in React applications. #react #datafetching