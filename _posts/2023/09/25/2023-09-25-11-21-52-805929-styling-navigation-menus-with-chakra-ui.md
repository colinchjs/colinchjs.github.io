---
layout: post
title: "Styling navigation menus with Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, react]
comments: true
share: true
---

In this blog post, we'll explore how to style navigation menus using Chakra UI, a popular UI library for React applications. Navigation menus are an essential component of any web application and often play a crucial role in providing a smooth user experience. With Chakra UI, we can easily create stylish and responsive navigation menus that match our application's design.

Chakra UI offers a range of pre-built components, styles, and utilities that make styling navigation menus a breeze. Here are a few steps to get started:

## Step 1: Install Chakra UI

To use Chakra UI in your React application, you will first need to install the library. Open your terminal and run the following command:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Step 2: Import Chakra UI Components

Next, you'll need to import the required Chakra UI components into your file. Depending on your application requirements, you may want to use `chakra` components such as `chakra.div`, `chakra.button`, or `chakra.link`.

Here's an example of importing the `chakra` component:

```jsx
import { chakra } from "@chakra-ui/react";
```

## Step 3: Create the Navigation Menu

Once you have Chakra UI installed and the necessary components imported, you can start creating your navigation menu. Consider using the `Flex` component from Chakra UI to create a responsive container for your menu items.

```jsx
import { Flex, chakra } from "@chakra-ui/react";

const NavigationMenu = () => {
  return (
    <Flex as="nav" align="center" justify="space-between" wrap="wrap" padding="1rem">
      {/* Navigation Menu Items */}
    </Flex>
  );
};

export default NavigationMenu;
```

## Step 4: Style the Menu Items

Now, it's time to style the menu items within the navigation menu. Chakra UI provides a range of built-in style props that allow you to customize the appearance of the components easily. You can use props like `color`, `bg`, `fontSize`, `fontWeight`, and `p` to achieve the desired styling.

Here's an example of styling a menu item using Chakra UI:

```jsx
// Inside the NavigationMenu component

const MenuItem = chakra("a", {
  baseStyle: {
    fontSize: "1.2rem",
    fontWeight: "bold",
    padding: "0.5rem 1rem",
    color: "black",
    transition: "color 0.3s ease",
    _hover: {
      color: "blue.500",
    },
  },
});

// Usage
<MenuItem href="#">Home</MenuItem>
```

## Step 5: Add Responsive Design

With Chakra UI, it's straightforward to make your navigation menu responsive. You can leverage the `Stack` component, which stacks its children vertically and adjusts its layout based on the available space.

```jsx
import { Flex, chakra, Stack } from "@chakra-ui/react";

const NavigationMenu = () => {
  return (
    <Flex as="nav" align="center" justify="space-between" padding="1rem">
      <Stack direction="row" spacing={4}>
        {/* Navigation Menu Items */}
      </Stack>
    </Flex>
  );
};

export default NavigationMenu;
```

By using `Stack` and its `direction` and `spacing` props, you can create responsive navigation menus that adapt to different screen sizes.

## Conclusion

Styling navigation menus with Chakra UI is simple and efficient. By leveraging the pre-built components and styles offered by Chakra UI, you can quickly create stylish and responsive navigation menus for your React applications. Explore the Chakra UI documentation to discover more options and customize your navigation menus to match your design requirements.

#chakraui #react #navigation #menustyling