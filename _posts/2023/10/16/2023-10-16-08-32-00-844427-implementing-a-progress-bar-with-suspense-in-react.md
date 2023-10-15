---
layout: post
title: "Implementing a progress bar with suspense in React"
description: " "
date: 2023-10-16
tags: [reactsuspense]
comments: true
share: true
---

In a React application, it is common to have components that fetch data asynchronously. While waiting for the data to be loaded, we can use suspense to render a fallback UI, such as a progress bar, to provide feedback to the user.

To implement a progress bar with suspense in React, follow these steps:

## Step 1: Install the necessary packages

First, make sure you have the necessary packages installed. We will be using the `react-dom` and `react-router-dom` packages for this example. Install them by running the following command:

```bash
npm install react-dom react-router-dom
```

## Step 2: Create a progress bar component

Create a new file called `ProgressBar.js` and add the following code:

```jsx
import React from 'react';

const ProgressBar = () => {
  return (
    <div>
      <h3>Loading...</h3>
      <progress max="100" />
    </div>
  );
};

export default ProgressBar;
```

This component renders a simple progress bar with the text "Loading..." and an HTML `progress` element.

## Step 3: Update your main component

In your main component where you fetch the data, import the `lazy` and `Suspense` components from React and the `ProgressBar` component. Wrap the component that fetches the data inside a `Suspense` component and provide the `fallback` prop with the `ProgressBar` component.

```jsx
import React, { lazy, Suspense } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';
import ProgressBar from './ProgressBar';

const MyComponent = lazy(() => import('./MyComponent'));

const App = () => {
  return (
    <Router>
      <Suspense fallback={<ProgressBar />}>
        <Switch>
          <Route path="/" component={MyComponent} />
        </Switch>
      </Suspense>
    </Router>
  );
};

export default App;
```

In this example, we are using the `lazy` function to import the component that fetches the data asynchronously. The `fallback` prop of the `Suspense` component is set to the `ProgressBar` component, which will be rendered while the data is being fetched.

## Step 4: Test the progress bar

Run your application and navigate to the route where the component that fetches the data is rendered. You should see the progress bar being shown while the data is being loaded. Once the data is loaded, the component will be rendered.

## Conclusion

By using suspense in React, we can provide a better user experience by showing a progress bar or any other type of fallback UI while waiting for data to be loaded asynchronously. This helps to communicate to the user that something is happening and reduces the perceived loading time.

# References

- [React documentation on Suspense](https://reactjs.org/docs/react-api.html#reactsuspense)
- [React Router documentation](https://reactrouter.com/)