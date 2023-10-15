---
layout: post
title: "Using suspense with code splitting in React"
description: " "
date: 2023-10-16
tags: [reactlazy]
comments: true
share: true
---

React's Suspense component and code splitting are two powerful features that can greatly improve the performance and user experience of your React applications. Suspense allows you to display a fallback UI while waiting for asynchronous data to load, and code splitting allows you to split your bundle into smaller chunks that can be loaded on-demand.

In this blog post, we will explore how to effectively combine Suspense with code splitting in React to achieve optimal performance. We will use React.lazy, a built-in React feature, to lazily load components and Suspense to handle the loading state.

## Why Use Code Splitting?

Code splitting is essential for optimizing large React applications. By splitting your code into smaller chunks, you can reduce the initial bundle size and improve loading times. This is especially important for modern web applications where users expect fast and responsive experiences.

## How to Use React.lazy

React.lazy is a function that enables you to lazily load components. It allows you to dynamically import a component when it is needed instead of including it in the initial bundle. This can significantly reduce the overall bundle size, as only the necessary components will be loaded.

Here's an example of how to use React.lazy:

```jsx
import React, { lazy, Suspense } from 'react';

const LazyComponent = lazy(() => import('./LazyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LazyComponent />
    </Suspense>
  );
}

export default App;
```

In the above example, we import React.lazy and Suspense from the 'react' package. We then use React.lazy to dynamically import the LazyComponent. The Suspense component wraps the LazyComponent and defines the fallback UI that will be displayed while the component is being loaded.

## Combining Suspense with Code Splitting

To combine Suspense with code splitting, we can wrap the Suspense component around multiple lazy-loaded components. This allows us to handle the loading state for all the dynamically imported components together.

```jsx
import React, { lazy, Suspense } from 'react';

const LazyComponent1 = lazy(() => import('./LazyComponent1'));
const LazyComponent2 = lazy(() => import('./LazyComponent2'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <div>
        <LazyComponent1 />
        <LazyComponent2 />
      </div>
    </Suspense>
  );
}

export default App;
```

In the above example, LazyComponent1 and LazyComponent2 are imported lazily and wrapped within the Suspense component. If any of the components are not yet loaded, the fallback UI (in this case, the string "Loading...") will be displayed.

## Conclusion

Using Suspense with code splitting in React can significantly improve the performance of your applications. By lazily loading components and providing a fallback UI with Suspense, you can achieve faster loading times and a better user experience.

Remember to use React.lazy to lazily import components, and wrap them in a Suspense component to handle the loading state. Experiment with code splitting and Suspense in your React projects to optimize your applications and create faster and more responsive experiences for your users.

# References
- [React.lazy - React Documentation](https://reactjs.org/docs/code-splitting.html#reactlazy)
- [React Suspense - React Documentation](https://reactjs.org/docs/concurrent-mode-suspense.html)
- [Code Splitting in React - Kent C. Dodds](https://kentcdodds.com/blog/code-splitting-with-react-and-react-router)