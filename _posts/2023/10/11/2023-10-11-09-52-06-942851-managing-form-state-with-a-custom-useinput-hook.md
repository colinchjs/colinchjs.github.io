---
layout: post
title: "Managing form state with a custom useInput hook"
description: " "
date: 2023-10-11
tags: [React, Forms]
comments: true
share: true
---

When building a form in a React application, managing the state of the input fields can become repetitive and error-prone. To simplify this process, we can create a custom hook called `useInput` that encapsulates the logic for handling form state. This custom hook will make it easier to manage the state of multiple input fields, handle validation, and perform other common form-related tasks.

In this blog post, we will walk through the process of creating and using the `useInput` hook, highlighting its benefits and demonstrating its usage in a practical example.

## Table of Contents
- [Introduction](#introduction)
- [Creating the useInput Hook](#creating-the-useinput-hook)
- [Using the useInput Hook](#using-the-useinput-hook)
- [Handling Validation](#handling-validation)
- [Conclusion](#conclusion)

## Introduction
Managing form state is a common challenge in React applications. As the number of input fields and form complexity increases, the code for updating and validating form data can become cumbersome. The `useInput` hook simplifies this process by abstracting away the complexity and providing a clean API to manage the state of multiple input fields.

## Creating the useInput Hook
Let's start by creating the `useInput` hook. This hook takes an initial value for the input field and returns an object with three properties: `value`, `onChange`, and `reset`.

```jsx
import { useState } from 'react';

const useInput = (initialValue) => {
  const [value, setValue] = useState(initialValue);

  const onChange = (e) => {
    setValue(e.target.value);
  };

  const reset = () => {
    setValue(initialValue);
  };

  return {
    value,
    onChange,
    reset,
  };
};

export default useInput;
```

In the code snippet above, `useState` is used to create a state variable called `value` and a function to update it called `setValue`. The `onChange` function updates the state based on the input value and the `reset` function resets the input field to its initial value.

## Using the useInput Hook
Now that we have created our `useInput` hook, we can use it in our components to manage form state.

```jsx
import React from 'react';
import useInput from './useInput';

const MyForm = () => {
  const nameInput = useInput('');
  const emailInput = useInput('');

  const handleSubmit = (e) => {
    e.preventDefault();
    // Perform form submission logic here
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>Name:</label>
      <input type="text" {...nameInput} />

      <label>Email:</label>
      <input type="email" {...emailInput} />

      <button type="submit">Submit</button>
    </form>
  );
};

export default MyForm;
```

In the code snippet above, the `useInput` hook is used to create state variables `nameInput` and `emailInput`. These variables contain the state value, the `onChange` function, and the `reset` function. Spread syntax (`{...nameInput}`) is used to pass these properties as props to the input fields.

## Handling Validation
The `useInput` hook can easily be extended to handle form validation. We can add a `isValid` property and an `error` message to the hook's return object. Here's an example:

```jsx
const useInput = (initialValue, validate) => {
  const [value, setValue] = useState(initialValue);
  const [isValid, setValid] = useState(true);
  const [error, setError] = useState('');

  const onChange = (e) => {
    const currentValue = e.target.value;
    setValue(currentValue);
    setValid(validate(currentValue));
  };

  const reset = () => {
    setValue(initialValue);
    setValid(true);
    setError('');
  };

  return {
    value,
    onChange,
    reset,
    isValid,
    error,
  };
};
```

In this modified version of `useInput`, we added two more state variables: `isValid` and `error`. The `onChange` function now calls a `validate` function to check the validity of the input value and updates the `isValid` and `error` state variables accordingly.

## Conclusion
Managing form state in React can be simplified and made reusable by creating a custom `useInput` hook. This hook encapsulates the logic for handling form state, making it easier to manage multiple input fields, perform validation, and perform other common form-related tasks. By using the `useInput` hook, we can write cleaner and more maintainable form code in our React applications.

We hope this blog post has been helpful in understanding how to manage form state using a custom hook. Feel free to explore and experiment with the `useInput` hook in your own projects. #React #Forms