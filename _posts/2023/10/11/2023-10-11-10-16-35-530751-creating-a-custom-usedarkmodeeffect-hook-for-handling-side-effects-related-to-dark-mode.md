---
layout: post
title: "Creating a custom useDarkModeEffect hook for handling side effects related to dark mode"
description: " "
date: 2023-10-11
tags: [react, react]
comments: true
share: true
---

Dark mode has become increasingly popular in recent years, allowing users to change the color scheme of an application or website to a darker theme. Implementing dark mode functionality often involves adding specific styling and handling side effects based on the current mode.

In this blog post, we will walk through the process of creating a custom React hook, `useDarkModeEffect`, that will simplify handling side effects related to dark mode. This hook will allow developers to easily execute additional code when the dark mode state changes.

## Table of Contents

- [Introduction](#introduction)
- [Setup](#setup)
- [Creating the `useDarkModeEffect` Hook](#creating-the-usedarkmodeeffect-hook)
- [Using the `useDarkModeEffect` Hook](#using-the-usedarkmodeeffect-hook)
- [Conclusion](#conclusion)

## Introduction

Dark mode has become a sought-after feature in many applications, providing an alternative color scheme that is easier on the eyes and can conserve battery life on certain devices. However, implementing all the necessary changes within an application can be challenging. By creating a custom hook to handle the side effects of dark mode, we can simplify the process and improve code reusability.

## Setup

Before we begin, let's make sure we have a basic setup with React and any necessary dependencies.

```javascript
import React, { useState, useEffect } from 'react';

const App = () => {
  // Our dark mode state
  const [darkMode, setDarkMode] = useState(false);

  // Our useDarkModeEffect hook

  return (
    // Render our application content
  );
};

export default App;
```

## Creating the `useDarkModeEffect` Hook

Let's start by creating our `useDarkModeEffect` hook.

```javascript
const useDarkModeEffect = (darkMode, callback) => {
  useEffect(() => {
    // Execute the callback when dark mode changes
    callback(darkMode);
  }, [darkMode, callback]);
};
```

In this hook, we use the built-in `useEffect` hook to execute the callback function whenever the `darkMode` state changes. This ensures that any side effects related to dark mode will be triggered only when necessary.

## Using the `useDarkModeEffect` Hook

Now, let's see how we can use our custom hook in our application.

```javascript
const App = () => {
  const [darkMode, setDarkMode] = useState(false);

  useDarkModeEffect(darkMode, (isDarkMode) => {
    // Handle side effects related to dark mode, e.g., updating CSS classes
    if (isDarkMode) {
      // Apply dark mode styling
    } else {
      // Apply light mode styling
    }
  });

  return (
    // Render our application content
  );
};
```

In this example, we pass the `darkMode` state and a callback function to our `useDarkModeEffect` hook. Inside the callback function, we can handle any necessary side effects, such as updating CSS classes or applying different styles depending on the current mode.

## Conclusion

By creating a custom `useDarkModeEffect` hook, we can simplify the process of handling side effects related to dark mode in our React applications. This hook allows us to execute additional code whenever the dark mode state changes, making it easier to implement and maintain dark mode functionality.

Remember to consider using this hook in your projects to improve code reusability and make managing dark mode a breeze.

[#react](#react) [#darkmode](#darkmode)