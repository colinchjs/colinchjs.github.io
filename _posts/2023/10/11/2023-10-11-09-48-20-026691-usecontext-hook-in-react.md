---
layout: post
title: "useContext hook in React"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In React, the `useContext` hook is used to access the value that has been provided by a Parent component to its child components using the `Context` API. It allows components to consume the context without the need of passing props through intermediate components.

## How to Use useContext Hook

1. Create a Context

   First, we need to create a context using the `createContext` function from the `react` package.

   ```jsx
   import React, { createContext } from 'react';

   const MyContext = createContext();
   ```

2. Provide the Context Value

   We need to wrap the parent component or the top-level component with the `MyContext.Provider` component to provide the context value.

   ```jsx
   function App() {
     const contextValue = 'Hello, useContext Hook';

     return (
       <MyContext.Provider value={contextValue}>
         {/* Other child components */}
       </MyContext.Provider>
     );
   }
   ```

3. Consume the Context Value

   Inside the child component where you want to access the context value, use the `useContext` hook to retrieve the value.

   ```jsx
   import React, { useContext } from 'react';

   function ChildComponent() {
     const value = useContext(MyContext);

     return <div>{value}</div>;
   }
   ```

   Here, the `useContext(MyContext)` hook returns the current context value provided by the `MyContext.Provider`. In this case, the `value` variable will contain the string `'Hello, useContext Hook'`.

4. Using Multiple Contexts

   If you have multiple contexts, you can simply nest the `Provider` components and use multiple `useContext` hooks to access the corresponding values.

   ```jsx
   function App() {
     const contextValue1 = "Context 1 value";
     const contextValue2 = "Context 2 value";

     return (
       <Context1.Provider value={contextValue1}>
         <Context2.Provider value={contextValue2}>
           {/* Child components */}
         </Context2.Provider>
       </Context1.Provider>
     );
   }

   function ChildComponent() {
     const value1 = useContext(Context1);
     const value2 = useContext(Context2);

     return (
       <div>
         <span>{value1}</span>
         <span>{value2}</span>
       </div>
     );
   }
   ```

## Conclusion

The `useContext` hook provides a clean and straightforward way to access the context value in React without the need for nested prop drilling. It enhances code readability and maintainability by eliminating the need for passing props through multiple components.

By using the `useContext` hook, you can retrieve the context value directly within your component, making it a powerful tool for building complex React applications.

*Tags: React, useContext, Context API*