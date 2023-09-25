---
layout: post
title: "Using the Box component in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraUI]
comments: true
share: true
---

#### Chakra UI is a popular React component library that provides a set of customizable and accessible UI components. One of the key components in Chakra UI is the "Box" component, which is a container that allows you to quickly create layout and styling.

In this tutorial, we will learn how to use the Box component in Chakra UI and explore some of its features.

## Installation

Before we begin, let's make sure we have Chakra UI installed in our project. You can install it by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or if you're using Yarn:

```bash
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Basic Usage

To use the Box component, we need to import it from the `@chakra-ui/react` package. Here's an example of how we can use the Box component to create a simple container:

```jsx
import { Box } from "@chakra-ui/react";

function App() {
  return (
    <Box backgroundColor="blue.500" padding="4" borderRadius="md">
      <p>This is a Box component</p>
    </Box>
  );
}

export default App;
```

In the above example, we import the `Box` component from `@chakra-ui/react`, and then we use it as a normal JSX component. We can pass different props to the Box component to customize its styling and layout. In this case, we set the background color to "blue.500", padding to "4", and borderRadius to "md".

## Custom Styling

The Box component in Chakra UI allows for easy custom styling. We can pass any valid CSS properties as props to the Box component. Additionally, Chakra UI provides a set of utility props to make it even simpler to style the component.

Here's an example that demonstrates using some of the utility props with the Box component:

```jsx
<Box 
  backgroundColor="blue.500"
  padding={4}
  borderRadius="md"
  boxShadow="lg"
  display="flex"
  justifyContent="center"
  alignItems="center"
>
  <p>Custom Styling with Box</p>
</Box>
```

In the above example, we added a boxShadow, set the display to "flex", and aligned the content at the center of the box using the justifyContent and alignItems props.

## Responsiveness

Chakra UI also provides utility props for creating responsive designs. We can use the `@media` syntax to define different styles based on different screen sizes.

Here's an example of how we can make the Box component responsive:

```jsx
<Box
  bg="green.500"
  p={4}
  borderRadius="md"
  _hover={{
    bg: "blue.500",
    transition: "background-color 0.2s"
  }}
  _active={{
    bg: "red.500"
  }}
  _focus={{
    outline: "none"
  }}
  _selected={{
    bg: "purple.500"
  }}
  _disabled={{
    opacity: 0.6,
    cursor: "not-allowed"
  }}
  _first={{
    color: "red.500"
  }}
  _last={{
    color: "blue.500"
  }}
>
  <p>Responsive Box</p>
</Box>
```

In the above example, we use different pseudo-props like `_hover` and `_active` to define different styles for when the box is hovered or clicked. We can also use `_focus`, `_selected`, `_disabled`, `_first`, and `_last` pseudo-props to apply styles based on different states or positions of the element.

## Conclusion

The Box component in Chakra UI is a versatile container that can be used to create layout and styling easily. It provides a wide range of props to customize the appearance and behavior of the component. By using the Box component, you can build beautiful and responsive UIs with less effort.

So, go ahead and give the Box component a try in your next React project using Chakra UI. It will streamline your UI development process and make your life as a developer much easier!

#react #chakraUI