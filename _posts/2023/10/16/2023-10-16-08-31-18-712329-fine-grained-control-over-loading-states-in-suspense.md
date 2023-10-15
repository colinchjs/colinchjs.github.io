---
layout: post
title: "Fine-grained control over loading states in suspense"
description: " "
date: 2023-10-16
tags: [reactsuspense, reactlazy]
comments: true
share: true
---

In React, the Suspense component offers a built-in way to handle asynchronous operations and provide loading states for your app. However, sometimes you may need more fine-grained control over the loading states to customize the user experience. In this blog post, we will explore how to achieve this level of control with Suspense.

## Understanding Suspense

Before diving into advanced loading states, let's recap how Suspense works. The Suspense component allows you to wrap your async components and specify a fallback component to render while the async content is loading.

```javascript
import React, { Suspense } from 'react';

const MyComponent = React.lazy(() => import('./MyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <MyComponent />
    </Suspense>
  );
}

export default App;
```

In the above example, the `MyComponent` is loaded asynchronously, and while it's loading, the fallback component will be rendered. Once the async component is loaded, it will be rendered in place of the fallback.

## Customizing loading states

To have more control over loading states, you can implement your own loading indicator component and conditionally render it based on loading conditions. Here's an example:

```javascript
import React, { Suspense, useState } from 'react';

const MyComponent = React.lazy(() => import('./MyComponent'));

const CustomLoader = () => {
  const [isLoading, setIsLoading] = useState(true);

  setTimeout(() => {
    setIsLoading(false);
  }, 3000); // Simulating loading delay of 3 seconds

  return isLoading ? <div>Loading custom content...</div> : null;
};

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <CustomLoader />
      <MyComponent />
    </Suspense>
  );
}

export default App;
```

In this example, we create a `CustomLoader` component that controls the loading state with the help of the `useState` hook. We simulate a loading delay of 3 seconds with `setTimeout` and set the loading state to `false` once the delay is over.

By rendering the `CustomLoader` before the async component, you can display your own loading indicator component and customize the loading experience for your users.

## Conclusion

React's Suspense component provides a convenient way to handle loading states in asynchronous rendering. By customizing the loading states, you can create a more tailored loading experience for your users. Fine-grained control over loading states allows you to display custom loading indicators and give your app a polished look. Embrace the power of Suspense to enhance the user experience in your React applications.

References:
- [React Suspense documentation](https://reactjs.org/docs/react-api.html#reactsuspense)
- [React.lazy() documentation](https://reactjs.org/docs/react-api.html#reactlazy)
- [React useState() hook documentation](https://reactjs.org/docs/hooks-state.html)