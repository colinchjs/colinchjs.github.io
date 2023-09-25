---
layout: post
title: "React.js form handling with Formik and Yup"
description: " "
date: 2023-09-25
tags: [React, Formik]
comments: true
share: true
---

Forms are an essential part of any web application. In React.js, handling form validation and submission can be a tedious task. However, with the help of Formik and Yup, the process can be made much more efficient and streamlined.

## What is Formik?

Formik is a popular form library for React.js that simplifies the process of building robust and reusable forms. It provides a set of hooks and utilities that handle form state management, validation, and submission.

## Why use Yup for form validation?

Yup is a powerful schema validation library that works seamlessly with Formik. It can be used to define validation rules for each field in the form, making it easy to ensure the data entered is valid before submitting the form.

## Installation

To get started with Formik and Yup, you need to install them as dependencies in your React.js project. Open your terminal and run the following command:

```bash
npm install formik yup
```

## Set up a basic form using Formik

First, let's create a basic form using Formik. We'll start by importing the necessary dependencies and setting up a simple form component.

```jsx
import React from 'react';
import { Formik, Field, ErrorMessage } from 'formik';

const MyForm = () => (
  <Formik initialValues={{ name: '', email: '', password: '' }}
          onSubmit={(values) => {
            // Handle form submission
          }}
  >
    <form>
      <Field type="text" name="name" placeholder="Name" />
      <ErrorMessage name="name" component="div" />

      <Field type="email" name="email" placeholder="Email" />
      <ErrorMessage name="email" component="div" />

      <Field type="password" name="password" placeholder="Password" />
      <ErrorMessage name="password" component="div" />

      <button type="submit">Submit</button>
    </form>
  </Formik>
);

export default MyForm;
```

In this example, we're using the `Formik` component to wrap our form. We define the initial values of the form fields using the `initialValues` prop, and the `onSubmit` prop to handle form submission.

The `Field` component is used to render each form field, and the `ErrorMessage` component is used to display any validation errors.

## Add validation using Yup

Now let's add validation to our form using Yup. We'll define a validation schema and use it to validate our form data.

```jsx
import * as Yup from 'yup';

const validationSchema = Yup.object().shape({
  name: Yup.string().required('Name is required'),
  email: Yup.string().email('Invalid email').required('Email is required'),
  password: Yup.string().min(6, 'Password must be at least 6 characters').required('Password is required'),
});

```

In this example, we're using the `Yup.object().shape()` method to define a validation schema. Each field in the form is assigned a specific validation rule using Yup's chaining syntax.

Finally, we can pass this validation schema to our `Formik` component using the `validationSchema` prop:

```jsx
<Formik 
  initialValues={{ name: '', email: '', password: '' }}
  validationSchema={validationSchema}
  onSubmit={(values) => {
    // Handle form submission
  }}
>
```

With Yup integrated into Formik, our form now has basic validation that ensures the user enters valid data in each field.

## Conclusion

Using Formik and Yup together in React.js allows for efficient form handling and validation. Formik simplifies the process of managing form state and submission, while Yup provides a powerful and declarative way to define and enforce validation rules. By combining these tools, you can create robust and user-friendly forms in your React.js applications.

#React #Formik #Yup