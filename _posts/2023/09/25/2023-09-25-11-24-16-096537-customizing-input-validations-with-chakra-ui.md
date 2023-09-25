---
layout: post
title: "Customizing input validations with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, InputValidations]
comments: true
share: true
---

Chakra UI is a popular and highly customizable UI library for React applications. It provides a robust set of components that can be easily customized to fit the design requirements of your application. In this blog post, we will explore how to customize input validations using Chakra UI.

## Why customize input validations?

Input validations are an essential part of any form in a web application. They help ensure that user-provided data is accurate and meets the required format or criteria. Although Chakra UI provides default styles and error messages for input validations, you may want to customize them to align with your application's design system or to provide a better user experience.

## Customizing the validation style

Chakra UI's `FormControl` component is used to wrap input fields and apply validation styles. By default, it provides an error message below the input field when validation fails. To customize the validation styles, you can use the `FormControl`'s `errorBorderColor` prop to change the border color, and the `errorBg` prop to change the background color of the input field.

```jsx
import { FormControl, FormLabel, Input, FormErrorMessage } from "@chakra-ui/react";

function ExampleForm() {
  return (
    <FormControl isInvalid> {/* Add the isInvalid prop to show validation error */}
      <FormLabel htmlFor="name">Name</FormLabel>
      <Input id="name" placeholder="Enter your name" />
      <FormErrorMessage>Invalid name format</FormErrorMessage>
    </FormControl>
  );
}
```

In the example above, the `isInvalid` prop is added to the `FormControl` component to indicate that validation has failed. This triggers the appearance of the error styles. The `FormErrorMessage` component is used to display the error message.

## Customizing the validation message

Chakra UI provides a default error message when using `FormErrorMessage`. However, you may want to customize the message to provide more specific feedback to the user. To do this, you can pass a custom message as a child of the `FormErrorMessage` component.

```jsx
import {
  FormControl,
  FormLabel,
  Input,
  FormErrorMessage,
  Button,
} from "@chakra-ui/react";

function ExampleForm() {
  const [error, setError] = useState("");

  const handleFormSubmit = () => {
    // Perform validation logic here
    if (/* validation fails */) {
      setError("Please enter a valid email address");
    }
  };

  return (
    <form onSubmit={handleFormSubmit}>
      <FormControl isInvalid={!!error}>
        <FormLabel htmlFor="email">Email</FormLabel>
        <Input id="email" placeholder="Enter your email" />
        <FormErrorMessage>{error}</FormErrorMessage>
      </FormControl>
      
      <Button type="submit">Submit</Button>
    </form>
  );
}
```

In the above example, we use the `useState` hook to manage a state variable called `error`. When the form is submitted and the validation fails, we update the `error` state with a custom error message. This message is then displayed using the `FormErrorMessage` component.

## Conclusion

Customizing input validations with Chakra UI allows you to tailor the validation styles and error messages to match your application's design and provide a better user experience. With the flexibility and customization options offered by Chakra UI, you can create visually appealing and user-friendly input validations in your React applications.

#ChakraUI #InputValidations