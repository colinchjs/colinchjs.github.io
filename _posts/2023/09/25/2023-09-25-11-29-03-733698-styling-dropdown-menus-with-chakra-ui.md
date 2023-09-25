---
layout: post
title: "Styling dropdown menus with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

Dropdown menus are a common UI element used to provide a list of options or actions for users to choose from. In this blog post, we will explore how to style dropdown menus using Chakra UI, a popular React component library known for its flexible and customizable design system.

Chakra UI provides a Dropdown component that makes it easy to implement dropdown menus in your React applications. Here's how you can style dropdown menus using Chakra UI:

## 1. Install and Import Chakra UI

First, you need to install and import Chakra UI into your React project. You can do this by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once installed, you can import the necessary components from Chakra UI in your React component file:

```jsx
import { Box, Button, Menu, MenuButton, MenuList, MenuItem } from "@chakra-ui/react";
```

## 2. Create Dropdown Menu

Next, you can create a dropdown menu using the Chakra UI components. The `Menu` component wraps the dropdown menu, while the `MenuButton`, `MenuList`, and `MenuItem` components define the trigger button, the list of menu items, and each individual menu item, respectively.

```jsx
<Menu>
  <MenuButton as={Button} variant="solid" colorScheme="teal">
    Dropdown
  </MenuButton>
  <MenuList>
    <MenuItem>Option 1</MenuItem>
    <MenuItem>Option 2</MenuItem>
    <MenuItem>Option 3</MenuItem>
  </MenuList>
</Menu>
```

## 3. Styling the Dropdown Menu

Now, you can style the dropdown menu to match your application's design. Chakra UI provides a wide range of props and styles that you can apply to customize the appearance of the dropdown menu.

For example, you can control the width, background color, and text color of the trigger button using the `buttonProps` prop:

```jsx
<MenuButton as={Button} variant="solid" colorScheme="teal" buttonProps={{ w: "150px", bg: "blue.500", color: "white" }}>
  Dropdown
</MenuButton>
```

You can also apply custom styling to the menu items using the `MenuItem` component's props:

```jsx
<MenuItem _hover={{ bg: "teal.300" }} _focus={{ bg: "teal.300" }}>
  Option 1
</MenuItem>
```

Chakra UI's documentation provides a comprehensive list of available props and styles that you can use to fully customize the dropdown menu.

## Conclusion

Styling dropdown menus with Chakra UI is simple and straightforward. By using the provided components and applying the available props and styles, you can easily create dropdown menus that match your application's design. Whether you need a basic dropdown menu or a highly customized one, Chakra UI's flexibility allows you to achieve the desired look and feel with ease.

#React #ChakraUI