---
layout: post
title: "Creating a custom useRef hook"
description: " "
date: 2023-10-11
tags: [react, hooks]
comments: true
share: true
---

In React, the `useRef` hook is used to create a mutable variable that persists across multiple renders of a component. It is often used to store references to DOM elements or values that need to be accessed within different parts of a component.

Here, we will learn how to create a custom `useRef` hook that includes additional functionality to handle focus management in a more convenient way.

## Table of Contents
- [Basic useRef Hook](#basic-useref-hook)
- [Custom useRef Hook](#custom-useref-hook)
- [Usage](#usage)
- [Conclusion](#conclusion)

## Basic useRef Hook

Before we dive into creating a custom `useRef` hook, let's review the basic usage of `useRef`. 

```javascript
import React, { useRef } from 'react';

function ExampleComponent() {
  const inputRef = useRef();

  const handleClick = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={handleClick}>Focus Input</button>
    </div>
  );
}
```

In the example above, we create a `ref` using the `useRef` hook, and assign it to the `ref` prop of the `input` element. By accessing the `current` property of the `ref`, we can access the DOM element and call its `focus` method to set the focus on it.

## Custom useRef Hook

Now let's create a custom `useFocus` hook that simplifies focus management. This custom hook will handle focus automatically when the component mounts and provide a function to manually focus the element.

```javascript
import { useRef, useEffect } from 'react';

function useFocus() {
  const ref = useRef();

  useEffect(() => {
    if (ref.current) {
      ref.current.focus();
    }
  }, []);

  return ref;
}
```

In the custom `useFocus` hook, we use the `useRef` hook to create a `ref` just like in the basic example. Then, we use the `useEffect` hook with an empty dependency array to execute a callback function only once when the component mounts. Inside the callback, we check if the `ref.current` is defined, and if so, call its `focus` method.

Finally, we return the `ref` from the hook so that it can be used in the component.

## Usage

Now that we have our custom `useFocus` hook, let's see how we can use it in a component.

```javascript
import React from 'react';
import useFocus from './hooks/useFocus';

function ExampleComponent() {
  const inputRef = useFocus();

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
}
```

In the above example, we import our custom `useFocus` hook and use it to create a `ref` named `inputRef`. We then assign this `ref` to the `ref` prop of the `input` element. 

To focus the input element manually, we can simply call the `focus` method on `inputRef.current`.

## Conclusion

Creating a custom `useRef` hook allows us to encapsulate reusable logic for focus management. This can result in cleaner and more organized code, especially when multiple components require similar functionality. By using custom hooks, we can enhance the reusability and maintainability of our React components while keeping our codebase clean and readable.

#react #hooks