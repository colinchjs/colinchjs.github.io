---
layout: post
title: "Implementing a skeleton loading screen with suspense in React"
description: " "
date: 2023-10-16
tags: []
comments: true
share: true
---

In a React application, it's important to provide good user experience by showing loading indicators while waiting for data to be fetched. One popular approach is to use skeleton loading screens, which display a simplified version of the content layout while the data is being loaded. In this blog post, we will learn how to implement a skeleton loading screen using React and the new suspense feature.

## Table of Contents
- [What is a skeleton loading screen?](#what-is-a-skeleton-loading-screen)
- [Setting up a React project](#setting-up-a-react-project)
- [Creating a skeleton component](#creating-a-skeleton-component)
- [Using suspense to show skeleton loading screen](#using-suspense-to-show-skeleton-loading-screen)
- [Conclusion](#conclusion)

## What is a skeleton loading screen?
A skeleton loading screen is a placeholder UI that mimics the appearance of the content to be loaded. It typically consists of simple shapes and placeholders for images or text. This gives the user a visual indication that something is loading and prevents the UI from appearing empty.

## Setting up a React project
Before we can start implementing the skeleton loading screen, let's set up a new React project. You can create a new React project using Create React App by running the following command in your terminal:

```bash
npx create-react-app skeleton-loading-screen
```

Once the project is created, navigate to the project directory and start the development server:

```bash
cd skeleton-loading-screen
npm start
```

## Creating a skeleton component
To create the skeleton loading screen, we will first create a new component called `Skeleton`. This component will be responsible for rendering the skeleton UI.

```jsx
import React from 'react';
import './Skeleton.css';

const Skeleton = () => {
  return (
    <div className="skeleton">
      {/* skeleton UI elements */}
    </div>
  );
};

export default Skeleton;
```

In the above code, we have defined a basic `Skeleton` component which returns a `div` element with the CSS class of `skeleton`. The actual skeleton UI elements like lines or shapes would be defined inside this `div`.

## Using suspense to show skeleton loading screen
With the introduction of React suspense, we can easily implement the skeleton loading screen pattern. Suspense allows us to suspend components while they are loading, showing a fallback UI in the meantime.

To use suspense, we first need to enable it in our project. Open the `index.js` file and modify it as follows:

```jsx
import React, { Suspense } from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import reportWebVitals from './reportWebVitals';
import './index.css';

ReactDOM.render(
  <React.StrictMode>
    <Suspense fallback={<Skeleton />}>
      <App />
    </Suspense>
  </React.StrictMode>,
  document.getElementById('root')
);

reportWebVitals();
```

In the above code, we have wrapped our `App` component with the `Suspense` component. We have also provided a `fallback` prop which specifies the skeleton loading screen component to be shown while the `App` component is loading.

With this setup, whenever there is a suspense boundary (such as when fetching data from an API), the `fallback` component will be rendered until the actual data is available.

## Conclusion
In this blog post, we have learned how to implement a skeleton loading screen using React and suspense. By implementing a skeleton loading screen, we can provide a better user experience by showing loading indicators while waiting for data to be fetched.