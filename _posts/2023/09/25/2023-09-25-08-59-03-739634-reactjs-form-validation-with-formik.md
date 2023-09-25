---
layout: post
title: "React.js form validation with Formik"
description: " "
date: 2023-09-25
tags: [React, Formik]
comments: true
share: true
---

Form validation is an essential part of building user-friendly and robust web applications. In React.js, Formik is a popular library that simplifies form handling and validation. In this tutorial, we will explore how to implement form validation using Formik in your React.js applications.

## Installing Formik

To start, let's install Formik and its dependencies by running the following command in your project directory:

```shell
npm install formik yup
```

Formik requires Yup for schema validation, so we need to install it as well.

## Setting up the Formik form

To begin, let's define a form using Formik in our React component:

```jsx
import React from 'react';
import { Formik, Form, Field, ErrorMessage } from 'formik';
import * as Yup from 'yup';

const initialValues = {
  name: '',
  email: '',
};

const validationSchema = Yup.object({
  name: Yup.string().required('Name is required'),
  email: Yup.string().email('Invalid email').required('Email is required'),
});

const MyForm = () => {
  const handleSubmit = (values) => {
    // Handle form submission
    console.log(values);
  };

  return (
    <Formik
      initialValues={initialValues}
      validationSchema={validationSchema}
      onSubmit={handleSubmit}
    >
      <Form>
        <div>
          <label htmlFor="name">Name:</label>
          <Field type="text" id="name" name="name" />
          <ErrorMessage name="name" component="div" />
        </div>
        <div>
          <label htmlFor="email">Email:</label>
          <Field type="email" id="email" name="email" />
          <ErrorMessage name="email" component="div" />
        </div>
        <button type="submit">Submit</button>
      </Form>
    </Formik>
  );
};

export default MyForm;
```

In the above example, we import the necessary components from Formik, including `Form`, `Field`, `ErrorMessage`, and `Formik` itself. We define the initial form values and the validation schema using Yup.

Inside the `MyForm` component, we define a `handleSubmit` function to handle form submission. The `<Formik>` component wraps our `<Form>`, and we include the form fields and error messages using `<Field>` and `<ErrorMessage>` components, respectively.

## Handling form submission

When the form is submitted, the `handleSubmit` function is called, which receives an object representing the form values. You can perform any necessary actions, such as making API requests or updating state, based on these form values.

## Conclusion

Form validation is crucial for ensuring data integrity and providing a good user experience. Formik simplifies the process of handling forms in React.js applications, making it easier to implement robust form validation.

By using Formik and Yup together, we can define validation rules, display error messages, and handle form submission with ease. Formik provides a set of powerful components that streamline form handling, allowing developers to focus on building great user interfaces.

Happy coding!

\#React #Formik #Validation