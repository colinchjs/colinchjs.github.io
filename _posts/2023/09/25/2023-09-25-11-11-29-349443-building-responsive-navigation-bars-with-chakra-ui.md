---
layout: post
title: "Building responsive navigation bars with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ResponsiveNavigation]
comments: true
share: true
---

In today's world of web development, it is crucial to create websites that are responsive and adaptable to different screen sizes. A key component of any responsive website is the navigation bar, which allows users to easily navigate through the site. In this article, we will explore how to build responsive navigation bars using Chakra UI, a simple and customizable component library for React.

## What is Chakra UI?

Chakra UI is a popular component library that provides a set of accessible and customizable UI components for building React applications. It comes with a variety of pre-styled components, including navigation bars, buttons, forms, and more. Chakra UI allows developers to quickly build responsive and visually appealing web applications.

## Creating a basic navigation bar

To get started, make sure you have Chakra UI installed in your project:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Next, we can create a basic navigation bar using the `Flex` component from Chakra UI. Here's an example of a simple navigation bar:

```jsx
import { Flex, Box, Text, Spacer } from '@chakra-ui/react';

const Navbar = () => {
  return (
    <Flex p={4} align="center" bg="gray.100">
      <Box>
        <Text fontSize="lg" fontWeight="bold">Logo</Text>
      </Box>
      <Spacer />
      <Box>
        <Text>Home</Text>
      </Box>
      <Box pl={4}>
        <Text>About</Text>
      </Box>
      <Box pl={4}>
        <Text>Contact</Text>
      </Box>
    </Flex>
  );
};

export default Navbar;
```

In this example, we are using the `Flex` component from Chakra UI to create a horizontal bar that contains our navigation items. We have used the `Box` component to wrap each navigation item, and the `Text` component to display the text for each item. The `Spacer` component is used to create space between the navigation items.

## Making the navigation bar responsive

To make the navigation bar responsive, we can use Chakra UI's `useBreakpointValue` hook. This hook allows us to define different values for a property based on different breakpoints. Here's an updated version of our navbar code that makes it responsive:

```jsx
import { Flex, Box, Text, Spacer, useBreakpointValue } from '@chakra-ui/react';

const Navbar = () => {
  const fontSize = useBreakpointValue({ base: 'md', md: 'lg' });
  const spacing = useBreakpointValue({ base: 2, md: 4 });

  return (
    <Flex p={4} align="center" bg="gray.100">
      <Box>
        <Text fontSize={fontSize} fontWeight="bold">Logo</Text>
      </Box>
      <Spacer />
      <Box>
        <Text fontSize={fontSize}>Home</Text>
      </Box>
      <Box pl={spacing}>
        <Text fontSize={fontSize}>About</Text>
      </Box>
      <Box pl={spacing}>
        <Text fontSize={fontSize}>Contact</Text>
      </Box>
    </Flex>
  );
};

export default Navbar;
```

In this updated version, we have defined different font sizes and spacing values based on different breakpoints using the `useBreakpointValue` hook. This ensures that the navigation bar adapts to different screen sizes and provides a seamless user experience.

## Conclusion

Building responsive navigation bars is essential for creating user-friendly websites. With Chakra UI, we can easily create responsive navigation bars using its flexible and customizable components. By using Chakra UI's built-in hooks like `useBreakpointValue`, we can make our navigation bars adapt to different screen sizes, ensuring that our websites look great on any device.

Give it a try and start building responsive navigation bars using Chakra UI in your next React project! #ChakraUI #ResponsiveNavigation