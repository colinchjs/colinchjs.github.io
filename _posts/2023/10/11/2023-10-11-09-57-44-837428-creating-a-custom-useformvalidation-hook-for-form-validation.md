---
layout: post
title: "Creating a custom useFormValidation hook for form validation"
description: " "
date: 2023-10-11
tags: [React, FormValidation]
comments: true
share: true
---

Form validation is an essential part of web development to ensure data correctness and prevent errors. In this blog post, we will guide you through the process of creating a custom `useFormValidation` hook in React to simplify and centralize form validation logic in your applications.

## Table of Contents
- [Introduction](#introduction)
- [Setting Up the Project](#setting-up-the-project)
- [Creating the `useFormValidation` Hook](#creating-the-useformvalidation-hook)
- [Using the `useFormValidation` Hook](#using-the-useformvalidation-hook)
- [Conclusion](#conclusion)

## Introduction

Validating form inputs can be a repetitive and error-prone task if we manage the validation logic in each form component individually. By creating a custom hook, we can encapsulate the validation logic and reuse it across multiple forms, improving code reusability and maintainability.

## Setting Up the Project

Before we dive into the implementation, let's set up a basic React project using Create React App:

```bash
npx create-react-app form-validation-app
cd form-validation-app
npm start
```

## Creating the `useFormValidation` Hook

Create a new file named `useFormValidation.js` in the `src` folder. In this file, we will define our custom hook:

```jsx
import { useState } from 'react';

const useFormValidation = (initialState, validationRules, onSubmit) => {
  const [values, setValues] = useState(initialState);
  const [errors, setErrors] = useState({});

  const handleChange = (e) => {
    const { name, value } = e.target;
    setValues({ ...values, [name]: value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    
    const validationErrors = {};

    Object.keys(validationRules).forEach((name) => {
      const value = values[name];
      const validationError = validationRules[name](value);

      if (validationError) {
        validationErrors[name] = validationError;
      }
    });

    if (Object.keys(validationErrors).length === 0) {
      onSubmit(values);
      setValues(initialState);
    } else {
      setErrors(validationErrors);
    }
  };

  return { values, errors, handleChange, handleSubmit };
};

export default useFormValidation;
```

In this hook, we utilize the `useState` hook to manage form values and validation errors. The `handleChange` function updates the form values whenever an input changes, while the `handleSubmit` function validates the form inputs against the provided validation rules and triggers the `onSubmit` callback if the form is valid.

## Using the `useFormValidation` Hook

Now, let's use our `useFormValidation` hook in a form component:

```jsx
import useFormValidation from './useFormValidation';

const SignUpForm = () => {
  const { values, errors, handleChange, handleSubmit } = useFormValidation(
    { name: '', email: '', password: '' },
    {
      name: (value) => !value && 'Name is required',
      email: (value) => !value && 'Email is required',
      password: (value) => value.length < 6 && 'Password should be at least 6 characters',
    },
    (values) => {
      // Handle form submission
      console.log('Form submitted:', values);
    }
  );

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" name="name" value={values.name} onChange={handleChange} />
        {errors.name && <span>{errors.name}</span>}
      </label>
      
      <label>
        Email:
        <input type="email" name="email" value={values.email} onChange={handleChange} />
        {errors.email && <span>{errors.email}</span>}
      </label>
      
      <label>
        Password:
        <input type="password" name="password" value={values.password} onChange={handleChange} />
        {errors.password && <span>{errors.password}</span>}
      </label>
      
      <button type="submit">Submit</button>
    </form>
  );
};

export default SignUpForm;
```

In the `SignUpForm` component, we destructure the values, errors, handleChange, and handleSubmit properties from the `useFormValidation` hook. We pass the initial form values, validation rules for each input field, and the form submission handler to the hook.

Now, the form inputs are automatically validated on each change, and error messages are rendered if any validation errors occur. When the form is submitted and no validation errors are present, the provided `onSubmit` function is called with the form values.

## Conclusion

In this blog post, we have demonstrated how to create a custom `useFormValidation` hook in React. By isolating the form validation logic into a reusable hook, we can improve the readability, reusability, and maintainability of our form components. By utilizing this custom hook, you can easily implement form validation in your React applications. Happy coding!

## Tags
#React #FormValidation