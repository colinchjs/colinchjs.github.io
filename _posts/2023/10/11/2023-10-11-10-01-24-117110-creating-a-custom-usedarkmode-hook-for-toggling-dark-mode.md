---
layout: post
title: "Creating a custom useDarkMode hook for toggling dark mode"
description: " "
date: 2023-10-11
tags: [React, DarkMode]
comments: true
share: true
---

Dark mode has become increasingly popular in recent years, as it provides a sleek and more comfortable browsing experience for users. In this blog post, we will explore how to create a custom `useDarkMode` hook using React, enabling users to toggle between light and dark modes effortlessly.

## Table of Contents
- [Introduction](#introduction)
- [Setting Up the Project](#setting-up-the-project)
- [Implementing the useDarkMode Hook](#implementing-the-usedarkmode-hook)
- [Toggling Dark Mode](#toggling-dark-mode)
- [Summary](#summary)

## Introduction
Dark mode is a feature that allows the user to switch the user interface (UI) to a darker color scheme. It is especially useful in low-light environments, as it reduces eye strain and improves readability. By creating this custom `useDarkMode` hook, we can easily integrate dark mode into our React applications.

## Setting Up the Project
Before we start implementing the hook, let's set up a basic React project if you haven't already:
```bash
npx create-react-app use-dark-mode-tutorial
cd use-dark-mode-tutorial
```

## Implementing the `useDarkMode` Hook
To begin, let's create a new file called `useDarkMode.js` and define our custom hook:
```javascript
import { useEffect, useState } from 'react';

const useDarkMode = () => {
  const [isDarkMode, setIsDarkMode] = useState(false);

  useEffect(() => {
    // Logic to check the user's preference for dark mode
    const preferDarkMode = window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches;
    setIsDarkMode(preferDarkMode);
  }, []);

  useEffect(() => {
    // Logic to update dark mode state in local storage
    localStorage.setItem('darkMode', JSON.stringify(isDarkMode));
    // Update the UI based on the dark mode state
    document.body.classList.toggle('dark-mode', isDarkMode);
  }, [isDarkMode]);

  return [isDarkMode, setIsDarkMode];
};

export default useDarkMode;
```

In this hook, we use the React `useState` and `useEffect` hooks to manage the dark mode state. The first `useEffect` checks the user's system preference for dark mode and sets the initial state accordingly. The second `useEffect` updates the dark mode state in local storage and applies the appropriate CSS class to the `body` element.

## Toggling Dark Mode
Now that we have our `useDarkMode` hook implemented, we can integrate it into our React components. Here's an example of how we can use this hook in a functional component:

```javascript
import React from 'react';
import useDarkMode from './useDarkMode';

const App = () => {
  const [isDarkMode, setIsDarkMode] = useDarkMode();

  const toggleDarkMode = () => {
    setIsDarkMode(!isDarkMode);
  };

  return (
    <div>
      <h1>My App</h1>
      <button onClick={toggleDarkMode}>
        Toggle Dark Mode
      </button>
      <p>
        Dark mode is {isDarkMode ? 'enabled' : 'disabled'}.
      </p>
    </div>
  );
};

export default App;
```

In this example, we create a simple component that renders a button to toggle dark mode. We use the `useDarkMode` hook to retrieve the current dark mode state and the `setIsDarkMode` function to update it when the button is clicked.

## Summary
In this tutorial, we walked through the process of creating a custom `useDarkMode` hook for toggling dark mode in a React application. By leveraging the power of React hooks, we were able to seamlessly integrate this functionality into our components. Implementing dark mode not only enhances the user experience but also showcases the flexibility of React's functional programming paradigm.

Feel free to experiment with styling your components differently based on the `isDarkMode` value, and let your creativity guide you towards achieving a visually appealing and accessible dark mode interface.

Thanks for reading!

# The two important hashtags: 
`#React` `#DarkMode`