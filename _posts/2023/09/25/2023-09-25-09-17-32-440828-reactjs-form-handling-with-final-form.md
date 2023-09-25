---
layout: post
title: "React.js form handling with Final Form"
description: " "
date: 2023-09-25
tags: [React, FormHandling]
comments: true
share: true
---

Managing forms in React.js can be a complex task, especially when it comes to handling form validation, form submission, and managing form state. Final Form is a library that simplifies form handling in React.js by providing a flexible and powerful solution.

In this blog post, we will explore how to use Final Form to handle forms in React.js. We will cover form setup, form validation, form submission, and accessing form values.

## Setting up Final Form

To get started with Final Form, you'll need to install it as a dependency in your React.js project:

```bash
npm install final-form react-final-form
```

Once installed, you can import the necessary components and functions from Final Form in your React.js component:

```javascript
import { Form, Field } from 'react-final-form';
```

## Creating a form

To create a form using Final Form, you can wrap your form components inside the `Form` component provided by Final Form. The `Form` component manages the form state and provides form-wide functions and values.

```jsx
<Form
  onSubmit={handleSubmit}
  initialValues={initialValues}
  validate={validate}
  render={({ handleSubmit }) => (
    <form onSubmit={handleSubmit}>
      <Field name="name" component="input" type="text" placeholder="Name" />
      <Field name="email" component="input" type="email" placeholder="Email" />
      <button type="submit">Submit</button>
    </form>
  )}
/>
```

In the example above, we pass necessary props to the `Form` component such as `onSubmit` for handling form submission, `initialValues` for pre-filling form fields, and `validate` for form validation.

## Form validation

Validating form inputs is an essential part of form handling. Final Form provides a straightforward way to validate form values using the `validate` prop.

```jsx
const validate = (values) => {
  const errors = {};

  if (!values.name) {
    errors.name = 'Please enter your name';
  }

  if (!values.email) {
    errors.email = 'Please enter your email';
  }

  return errors;
};
```

In the `validate` function above, we check if the form fields `name` and `email` have values. If not, we add an error message to the `errors` object.

## Handling form submission

Final Form simplifies form submission by handling the submission logic for you. You can access the form values using the `onSubmit` function provided to the `Form` component.

```jsx
const handleSubmit = (values) => {
  console.log(values); // Output: { name: 'John Doe', email: 'johndoe@example.com' }
  // Handle form submission logic here
};
```

In the `handleSubmit` function above, we simply log the form values to the console. You can replace this log with your custom logic, such as sending a network request or updating your application state.

## Accessing form values

To access form values outside the form submission logic, you can use the `Field` component provided by Final Form. The `Field` component acts as a bridge between form inputs and the form state.

```jsx
<Field name="name" component="input" type="text">
  {({ input }) => (
    <div>
      <input {...input} />
      <button onClick={() => console.log(input.value)}>Log Name</button>
    </div>
  )}
</Field>
```

In the example above, we wrap the `input` component with the `Field` component and pass the `input` prop to retrieve the value. We log the value when the button is clicked.

Final Form provides many other useful features such as field-level validation, asynchronous validation, and field arrays. Make sure to check out the Final Form documentation for more advanced usage.

## Conclusion

Final Form is a powerful library for handling forms in React.js. It simplifies form management, form validation, and form submission, making it easier to build complex forms in React.js applications. With Final Form, you can focus on the logic and functionality of your forms, rather than spending time on form handling boilerplate code.

#React #FormHandling #ReactFinalForm