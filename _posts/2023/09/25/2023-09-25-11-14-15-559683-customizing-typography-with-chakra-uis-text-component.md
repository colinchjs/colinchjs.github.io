---
layout: post
title: "Customizing typography with Chakra UI's Text component"
description: " "
date: 2023-09-25
tags: [ChakraUI, Typography]
comments: true
share: true
---

If you're looking to customize the typography in your React application using Chakra UI, you're in luck! Chakra UI's `Text` component provides a simple and intuitive way to style and customize your text.

## Getting started

To get started, make sure you have Chakra UI installed and set up in your React project. You can follow the installation instructions in the [Chakra UI documentation](https://chakra-ui.com/docs/getting-started).

## Basic usage

Once you have Chakra UI set up, you can start using the `Text` component. Here's an example of how to use it:

```jsx
import { Text } from "@chakra-ui/react";

function App() {
  return (
    <Text fontSize="xl" fontWeight="bold" color="teal.500">
      Customizing typography with Chakra UI
    </Text>
  );
}
```

In this example, we've set the `fontSize` to `xl`, `fontWeight` to `bold`, and `color` to `teal.500` for our text. You can customize these properties to suit your needs.

## Available props

The `Text` component in Chakra UI provides a wide range of props to customize your text. Here are some commonly used props:

- `fontSize`: Sets the size of the text.
- `fontWeight`: Sets the weight (boldness) of the text.
- `color`: Sets the color of the text.
- `textAlign`: Sets the alignment of the text.
- `textDecoration`: Adds decoration to the text, such as underline or strike-through.
- `textTransform`: Transforms the text to uppercase, lowercase, or capitalize.
- `letterSpacing`: Adjusts the spacing between letters.
- `lineHeight`: Sets the height of each line of text.
- `overflowWrap`: Defines how the text should wrap when it exceeds the container width.
- `whiteSpace`: Specifies how white space within the text should be handled.

These are just a few examples. You can find a complete list of available props in the [Chakra UI Typography documentation](https://chakra-ui.com/docs/typography).

## Theming

Chakra UI also allows you to customize the typography on a global scale using its theming system. You can modify the default values and create your own variants for text styles. Here's an example of how to customize the default font size:

```jsx
import { extendTheme } from "@chakra-ui/react";

const customTheme = extendTheme({
  fonts: {
    body: "Roboto, sans-serif",
    heading: "Montserrat, sans-serif",
  },
  fontSizes: {
    xl: "24px",
    "2xl": "32px",
  },
});

function App() {
  return (
    <ChakraProvider theme={customTheme}>
      <Text fontSize="xl" fontWeight="bold" color="teal.500">
        Customizing typography with Chakra UI
      </Text>
    </ChakraProvider>
  );
}
```

In this example, we've created a custom theme that modifies the `fontSizes` to include custom values for `xl` and `2xl`. We also specified new font families for the `body` and `heading` styles. You can extend the theme to suit your specific typography needs.

## Conclusion

With Chakra UI's `Text` component, customizing typography in your React application becomes a breeze. You can easily customize various attributes of your text, and even modify the typography on a global scale using the theming system. Enjoy creating beautiful and engaging typographic designs with Chakra UI!

## #ChakraUI #Typography