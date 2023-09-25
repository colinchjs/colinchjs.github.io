---
layout: post
title: "Using the Tag component in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

The Tag component in Chakra UI is a versatile component that allows you to display tags or labels in your application. Tags are commonly used to categorize or label items for easy identification. In this blog post, we will explore how to use the Tag component in Chakra UI to create and style tags in your application.

## Installation

To use the Tag component, you first need to install Chakra UI in your project. You can install Chakra UI using npm or yarn. Here is an example of how to install Chakra UI using npm:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Usage

Once Chakra UI is installed, you can start using the Tag component in your application. Import the `Tag` component from Chakra UI and use it as follows:

```jsx
import { Tag } from "@chakra-ui/react";

function App() {
  return (
    <Tag size="md" variant="solid" colorScheme="blue">
      Chakra UI
    </Tag>
  );
}
```

In the example above, we import the `Tag` component from Chakra UI and render it with the desired props. The `size` prop determines the size of the tag (e.g., "sm" for small, "md" for medium, "lg" for large). The `variant` prop determines the visual style of the tag (e.g., "solid" for filled, "subtle" for outlined). The `colorScheme` prop sets the color scheme for the tag (e.g., "blue", "green", "red").

## Custom Styling

Chakra UI provides a set of default styles for the Tag component, but you can also customize the styles to suit your application's design. You can use the `styleProps` object to override the default styles. Here is an example:

```jsx
import { Tag } from "@chakra-ui/react";

function App() {
  return (
    <Tag
      size="md"
      variant="solid"
      colorScheme="blue"
      bg="teal.400"
      color="white"
      borderRadius="md"
      _hover={{ bg: "teal.500" }}
    >
      Custom Tag
    </Tag>
  );
}
```

In the example above, we override the default styles of the Tag component by setting the `bg` (background color), `color` (text color), `borderRadius` (border radius), and `_hover` (styles on hover) props.

## Conclusion

The Tag component in Chakra UI is a powerful tool for displaying tags or labels in your application. With its easy-to-use APIs and customizable styles, you can create visually appealing tags that enhance the user experience. Give it a try in your next Chakra UI project!

#ChakraUI #React