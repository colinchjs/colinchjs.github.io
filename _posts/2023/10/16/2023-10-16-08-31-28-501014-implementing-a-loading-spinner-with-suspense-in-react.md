---
layout: post
title: "Implementing a loading spinner with suspense in React"
description: " "
date: 2023-10-16
tags: [3498db, reactsuspense]
comments: true
share: true
---

In modern web applications, it's important to provide a good user experience by displaying a loading spinner while data or components are being loaded. React's `Suspense` component, introduced in React 16.6, makes it easy to handle asynchronous loading and display a loading spinner until the data is ready.

## Using React Suspense

To implement a loading spinner with `Suspense`, follow these steps:

1. Wrap your asynchronous components or data fetching calls with a `Suspense` component in your parent component.

Example: 

```jsx
import React, { Suspense } from 'react';

const MyComponent = () => {
  return (
    <div>
      <Suspense fallback={<Spinner />}>
        <AsyncComponent />
      </Suspense>
    </div>
  );
}
```

2. Create a `fallback` component that will be displayed while the asynchronous component is loading.

```jsx
const Spinner = () => {
  return (
    <div className="spinner">
      <div className="spinner__circle"></div>
    </div>
  );
}
```

3. Implement your asynchronous component using React's lazy loading with `import()`.

```jsx
const AsyncComponent = React.lazy(() => import('./AsyncComponent'));
```

4. In your `AsyncComponent`, handle the loading of data or any async operations. You can also wrap the data fetching call with `Suspense` to display the loading spinner during data fetching.

Example:

```jsx
import React, { Suspense } from 'react';

const AsyncComponent = () => {
  const data = fetchData();
  
  return (
    <div>
      <Suspense fallback={<Spinner />}>
        {data}
      </Suspense>
    </div>
  );
}
```

## Customizing the loading spinner

To customize the loading spinner, you can modify the `Spinner` component's CSS class and add your own styling.

Example CSS:

```css
.spinner {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.spinner__circle {
  width: 50px;
  height: 50px;
  border: 3px solid #f3f3f3;
  border-top: 3px solid #3498db;
  border-radius: 50%;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(360deg);
  }
}
```

With this implementation, the loading spinner will be displayed until the `AsyncComponent` and its associated data are fully loaded. This provides a seamless user experience and keeps your application responsive.

# References
- [React Suspense documentation](https://reactjs.org/docs/react-api.html#reactsuspense)
- [React.lazy() documentation](https://reactjs.org/docs/code-splitting.html#reactlazy)
- [Create React App documentation on lazy loading](https://create-react-app.dev/docs/code-splitting/#webpack)

## #React #LoadingSpinner