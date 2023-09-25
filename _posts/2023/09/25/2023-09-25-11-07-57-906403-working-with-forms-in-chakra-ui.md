---
layout: post
title: "Working with forms in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakra]
comments: true
share: true
---

Chakra UI is a popular and powerful component library that helps developers build user interfaces in React applications. It provides a wide range of pre-built components, including form components, which make it easier to work with and validate user input.

In this tutorial, we will explore how to work with forms in Chakra UI and leverage its form components to create a user-friendly form.

## Installation

To get started, make sure you have Chakra UI installed in your React project. If you haven't already installed it, run the following command:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating a Basic Form

Let's start by creating a basic form using Chakra UI components. First, import the necessary components from Chakra UI:

```jsx
import { Input, Button, FormControl, FormLabel, FormErrorMessage } from '@chakra-ui/react';
```

Now, you can use these components to build your form:

```jsx
const MyForm = () => {
  return (
    <form>
      <FormControl id="name" isRequired>
        <FormLabel>Name</FormLabel>
        <Input type="text" />
        {/* Form error message */}
        <FormErrorMessage>This field is required</FormErrorMessage>
      </FormControl>

      <FormControl id="email" isRequired>
        <FormLabel>Email</FormLabel>
        <Input type="email" />
        {/* Form error message */}
        <FormErrorMessage>This field is required</FormErrorMessage>
      </FormControl>

      <Button type="submit">Submit</Button>
    </form>
  );
};
```

In the example above, we have used the `FormControl`, `FormLabel`, `Input`, `FormErrorMessage`, and `Button` components from Chakra UI. The `FormControl` component provides the base to wrap form inputs, and we can include a `FormLabel` and `FormErrorMessage` to give more context and validation feedback to the user.

You can add additional form inputs and validations as needed.

## Styling the Form

Chakra UI provides a theming system that allows you to customize the look and feel of your form components. You can leverage the `ChakraProvider` component and provide a custom theme object to modify the styles. For example:

```jsx
import { ChakraProvider, extendTheme } from "@chakra-ui/react";

const theme = extendTheme({
  components: {
    Input: {
      baseStyle: {
        borderColor: "blue.500",
      },
    },
    Button: {
      baseStyle: {
        bgColor: "blue.500",
        color: "white",
      },
    },
  },
});

function App() {
  return (
    <ChakraProvider theme={theme}>
      {/* Your app content and form */}
    </ChakraProvider>
  );
}
```

In the above example, we have modified the base styles of the `Input` and `Button` components to use a custom color scheme.

## Conclusion

Working with forms in Chakra UI is straightforward and provides a streamlined way to handle user input and validation. By leveraging the pre-built form components and theming system, you can create user-friendly forms in your React applications with ease.

#react #chakra-ui