---
layout: post
title: "React.js routing using React Router"
description: " "
date: 2023-09-25
tags: [ReactRouter, ReactJS]
comments: true
share: true
---

React Router is a popular library in the React.js ecosystem that allows you to handle routing in your web applications. It provides a declarative way to define routes and navigate between different views in your application.

## Installation

To start using React Router in your React.js project, you need to install the `react-router-dom` package. You can do this by running the following command in your project directory:

```shell
npm install react-router-dom
```

## Basic Usage

To use React Router, you need to wrap your application with the `BrowserRouter` component. This component provides the necessary context for routing to work correctly. Here's an example of how to set up basic routing in your React.js application:

```javascript
import React from 'react';
import { BrowserRouter as Router, Switch, Route } from 'react-router-dom';

import Home from './pages/Home';
import About from './pages/About';
import NotFound from './pages/NotFound';

function App() {
  return (
    <Router>
      <Switch>
        <Route exact path="/" component={Home} />
        <Route path="/about" component={About} />
        <Route component={NotFound} />
      </Switch>
    </Router>
  );
}

export default App;
```

In the above example, we import the necessary components from `react-router-dom` and define the routes using the `Route` component. The `exact` prop is used to match the exact URL, and the `component` prop specifies the component to render for that route. The `Switch` component ensures that only the first matching route is rendered.

You can define as many routes as needed, and each route can have its own component. The `<Route component={NotFound} />` acts as a fallback route that renders when no other routes match.

## Navigating Between Routes

React Router provides a `<Link>` component that allows you to easily create links between different routes in your application. Here's an example of how to use it:

```javascript
import React from 'react';
import { Link } from 'react-router-dom';

function Navbar() {
  return (
    <nav>
      <ul>
        <li>
          <Link to="/">Home</Link>
        </li>
        <li>
          <Link to="/about">About</Link>
        </li>
      </ul>
    </nav>
  );
}

export default Navbar;
```

In the above example, we import the `Link` component from `react-router-dom` and use it to create navigation links. The `to` prop specifies the destination URL for the link.

## Summary

React Router is a powerful tool for handling routing in React.js applications. By using the `react-router-dom` package and defining routes with the `Route` component, you can easily navigate between different views in your application. The `Link` component can be used to create navigation links. Make sure to wrap your application with the `BrowserRouter` component to enable routing functionality. #ReactRouter #ReactJS