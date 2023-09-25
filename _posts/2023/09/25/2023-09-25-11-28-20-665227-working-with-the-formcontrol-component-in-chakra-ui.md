---
layout: post
title: "Working with the FormControl component in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraUI]
comments: true
share: true
---

Chakra UI is a popular UI component library for React applications. It provides a set of customizable and accessible components that make building user interfaces a breeze. One of the key components in Chakra UI is `FormControl`, which is used to manage form inputs and handle validation.

## Getting Started

To use `FormControl`, you first need to install Chakra UI in your project. You can do this by running the following command:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or if you are using yarn:

```
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Basic Usage

Here's an example of how to use `FormControl` with an input field:

```jsx
import { FormControl, FormLabel, Input } from "@chakra-ui/react";

function LoginForm() {
  return (
    <FormControl>
      <FormLabel>Email</FormLabel>
      <Input type="email" />
    </FormControl>
  );
}
```

In the example above, we import `FormControl`, `FormLabel`, and `Input` from `@chakra-ui/react`. The `FormLabel` component is used to label the input field. The `Input` component represents the actual input field.

By nesting the `FormLabel` and `Input` components within the `FormControl` component, Chakra UI takes care of styling and accessibility for us. It provides a consistent and visually appealing form field.

## Validation

`FormControl` also provides validation capabilities. You can add validation rules and error messages to your form fields. Here's an example:

```jsx
import { FormControl, FormLabel, Input, FormErrorMessage } from "@chakra-ui/react";
import { useForm } from "react-hook-form";

function LoginForm() {
  const {
    register,
    handleSubmit,
    formState: { errors },
  } = useForm();

  const onSubmit = (data) => {
    // Handle form submission
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <FormControl isInvalid={errors.email}>
        <FormLabel>Email</FormLabel>
        <Input
          type="email"
          {...register("email", { required: "Email is required" })}
        />
        <FormErrorMessage>{errors.email?.message}</FormErrorMessage>
      </FormControl>
    </form>
  );
}
```

In the example above, we use the `useForm` hook from `react-hook-form` to handle form validation. We pass the `register` function to the `Input` component to register the input field with the validation rules. The `isInvalid` prop on `FormControl` is used to conditionally style the form control if there is an error.

The `FormErrorMessage` component is used to display the error message when the form field is invalid. The `errors.email?.message` syntax is used to dynamically display the error message if it exists.

## Conclusion

In this article, we explored how to use the `FormControl` component in Chakra UI for managing form inputs and handling validation. We saw how easy it is to create accessible and visually appealing form fields with Chakra UI. By leveraging the power of Chakra UI and `react-hook-form`, you can build robust and user-friendly forms in your React applications.

#react #chakraUI