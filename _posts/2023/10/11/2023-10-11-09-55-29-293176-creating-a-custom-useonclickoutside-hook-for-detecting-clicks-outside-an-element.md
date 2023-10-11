---
layout: post
title: "Creating a custom useOnClickOutside hook for detecting clicks outside an element"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In this blog post, we will be creating a custom React hook called `useOnClickOutside`. This hook will allow us to easily detect when a user clicks outside of a specific element on the page. This can be useful for implementing dropdowns, modals, or any other component that needs to close when the user clicks outside of it.

### What is a custom hook?

A custom hook is a reusable function that contains some logic and can be used in multiple components. Custom hooks are a powerful feature in React that allows us to encapsulate complex behavior and share it across different parts of our application.

### Implementing the `useOnClickOutside` hook

To start, let's create a new JavaScript file called `useOnClickOutside.js` and define our custom hook:

```javascript
import { useEffect } from "react";

const useOnClickOutside = (ref, handler) => {
  useEffect(() => {
    const handleClickOutside = (event) => {
      if (ref.current && !ref.current.contains(event.target)) {
        handler();
      }
    };
    
    document.addEventListener("mousedown", handleClickOutside);
    return () => {
      document.removeEventListener("mousedown", handleClickOutside);
    };
  }, [ref, handler]);
};

export default useOnClickOutside;
```

Let's break down the code:

1. We import the `useEffect` hook from React, which will allow us to perform side effects in our custom hook.
2. We define our custom hook `useOnClickOutside` with two parameters: `ref` and `handler`. `ref` is a reference to the element we want to detect clicks outside of, and `handler` is a function that will be called when a click outside the element occurs.
3. Inside the `useEffect` hook, we define a callback function `handleClickOutside` that will check if the clicked element is outside of the referenced element. If it is, we call the `handler` function.
4. We attach the `handleClickOutside` function to the `mousedown` event on the document using `document.addEventListener`.
5. Finally, we clean up the event listener by removing it in the cleanup function returned by `useEffect` using `document.removeEventListener`.

### Using the `useOnClickOutside` hook

Now that we have our custom hook, let's see how we can use it in a React component:

```javascript
import React, { useRef } from "react";
import useOnClickOutside from "./useOnClickOutside";

const Dropdown = () => {
  const dropdownRef = useRef();

  const closeDropdown = () => {
    // Logic to close the dropdown
  };

  useOnClickOutside(dropdownRef, closeDropdown);

  return (
    <div ref={dropdownRef}>
      {/* Dropdown content */}
    </div>
  );
};

export default Dropdown;
```

In this example, we create a `Dropdown` component that uses the `useOnClickOutside` hook to close the dropdown when the user clicks outside of it. We create a `ref` using the `useRef` hook and pass it to the `useOnClickOutside` hook along with a `closeDropdown` function that contains the logic to close the dropdown.

### Conclusion

Creating a custom `useOnClickOutside` hook allows us to easily detect clicks outside of an element and trigger actions accordingly. This can be a powerful tool for enhancing user experience and improving the usability of our React applications.

Remember to check out the official React Hooks documentation for more information on creating and using custom hooks.