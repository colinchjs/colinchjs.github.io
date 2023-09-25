---
layout: post
title: "Using the Input component in Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

Chakra UI is a popular React UI library that provides a set of accessible and customizable UI components. One of the commonly used components in Chakra UI is the `Input` component, which allows users to input text or other data.

## Getting Started

To use the `Input` component in Chakra UI, you need to install the Chakra UI package:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```shell
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once installed, you can import the `Input` component in your React component:

```jsx
import { Input } from "@chakra-ui/react";

function MyForm() {
  return (
    <Input placeholder="Enter your name" />
  );
}
```

## Customizing the Input Component

Chakra UI provides a wide range of props that you can use to customize the `Input` component according to your needs. Here are a few examples:

- **Size**: You can adjust the size of the input field by setting the `size` prop to either "sm" (small), "md" (medium), or "lg" (large).

```jsx
<Input size="sm" placeholder="Small input" />
<Input size="md" placeholder="Medium input" />
<Input size="lg" placeholder="Large input" />
```

- **Variant**: Chakra UI offers multiple variants for the `Input` component, such as "outline", "filled", "flushed", and "unstyled".

```jsx
<Input variant="outline" placeholder="Outlined input" />
<Input variant="filled" placeholder="Filled input" />
<Input variant="flushed" placeholder="Flushed input" />
<Input variant="unstyled" placeholder="Unstyled input" />
```

- **Disabled**: You can disable the input field by setting the `isDisabled` prop to `true`.

```jsx
<Input isDisabled placeholder="Disabled input" />
```

- **Error Handling**: Chakra UI provides an `isInvalid` prop that allows you to indicate an error state in the input field.

```jsx
<Input isInvalid placeholder="Invalid input" />
```

## Conclusion

The `Input` component in Chakra UI is a versatile and customizable input field that facilitates user input in your React applications. It offers a wide range of props to customize its appearance and behavior based on your specific requirements.

Using Chakra UI's `Input` component can streamline the development process and enhance the accessibility and usability of your web forms. So, give it a try in your next React project!

#React #ChakraUI