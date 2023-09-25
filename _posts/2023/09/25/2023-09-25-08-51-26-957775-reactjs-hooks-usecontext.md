---
layout: post
title: "React.js hooks: useContext"
description: " "
date: 2023-09-25
tags: [ReactJS, useContext]
comments: true
share: true
---

The `useContext` hook allows us to consume values from the React context within a functional component. Context is a way to share data between components without passing props manually at every level. It eliminates the need to pass props down through intermediate components that don't need the data.

To use the `useContext` hook, we first need to create a context using the `createContext` method. Let's create a simple example where we have a context for the user's language preference:

```javascript
import React, { useContext, createContext } from 'react';

// Create a context
const LanguageContext = createContext();

// Create a component that will provide the context value
const LanguageProvider = ({ children }) => {
  const userLanguage = 'en'; // In a real application, this could come from an API or user settings

  return (
    <LanguageContext.Provider value={userLanguage}>
      {children}
    </LanguageContext.Provider>
  );
};

// Create a functional component that consumes the context
const MyComponent = () => {
  const language = useContext(LanguageContext);

  return <div>Current language: {language}</div>;
};
```

In the example above, we created a `LanguageContext` using `createContext` method. We then created a `LanguageProvider` component that wraps all the components that need access to the language context. The `LanguageProvider` component sets the value of the context to the user's language preference.

In the `MyComponent` component, we use the `useContext` hook to consume the value from the `LanguageContext`. It returns the current language preference and renders it in a `div` element.

To make the context available to our components, we need to render the `LanguageProvider` component at the top level of our application:

```javascript
function App() {
  return (
    <LanguageProvider>
      <MyComponent />
    </LanguageProvider>
  );
}
```

By doing this, all the components wrapped inside the `LanguageProvider` will have access to the language context.

Using the `useContext` hook, we can easily consume values from a context and keep our components concise and focused. It simplifies the process of accessing shared data and improves the overall maintainability of our React applications.

Give it a try in your projects and experience the power of `useContext` in React.js!

\#ReactJS #useContext