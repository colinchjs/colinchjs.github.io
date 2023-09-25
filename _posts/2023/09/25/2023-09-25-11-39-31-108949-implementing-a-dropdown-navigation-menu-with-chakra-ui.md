---
layout: post
title: "Implementing a dropdown navigation menu with Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakra]
comments: true
share: true
---

One of the essential components of a website is a navigation menu. It allows users to navigate through different pages or sections of a website easily. In this tutorial, I will show you how to implement a dropdown navigation menu using Chakra UI, a popular React component library that provides a set of accessible and customizable UI components.

## What is Chakra UI?

Chakra UI is a simple and flexible component library for building React applications. It provides a wide range of ready-to-use UI components, including buttons, modals, forms, and more. Chakra UI is known for its simplicity and accessibility, making it a popular choice for many developers.

## Prerequisites

To follow along with this tutorial, you need to have basic knowledge of React and have Chakra UI installed in your React project. If you haven't set up Chakra UI, you can install it by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Implementing a Basic Navigation Bar

To start with, create a new React component called `Navbar.js` and import the necessary dependencies:

```javascript
import React from 'react';
import { Box, Flex, Text } from '@chakra-ui/react';
```

In the `Navbar` component, create a `Flex` container that will hold the navigation menu items:

```javascript
const Navbar = () => {
  return (
    <Flex bg="blue.500" p="4" justifyContent="space-between">
      {/* Navigation Items */}
    </Flex>
  );
};

export default Navbar;
```

Next, add the navigation menu items inside the `Flex` container. You can use the `Text` component from Chakra UI to display each menu item:

```javascript
const Navbar = () => {
  return (
    <Flex bg="blue.500" p="4" justifyContent="space-between">
      <Text>Home</Text>
      <Text>About</Text>
      <Text>Services</Text>
      <Text>Contact</Text>
    </Flex>
  );
};
```

The basic navigation bar is now ready. However, we want to convert the menu items into a dropdown when the screen size is reduced. To achieve this, we will use the Chakra UI `Menu` and `MenuItem` components.

## Implementing the Dropdown Menu

First, import the `Menu` and `MenuButton` components from Chakra UI:

```javascript
import { Menu, MenuButton, MenuList, MenuItem } from '@chakra-ui/react';
```

Wrap the navigation items inside the `Menu` component and provide a label for the dropdown button using the `MenuButton` component:

```javascript
const Navbar = () => {
  return (
    <Flex bg="blue.500" p="4" justifyContent="space-between">
      <Menu>
        <MenuButton as={Text}>
          Menu
        </MenuButton>
        <MenuList>
          <MenuItem>Home</MenuItem>
          <MenuItem>About</MenuItem>
          <MenuItem>Services</MenuItem>
          <MenuItem>Contact</MenuItem>
        </MenuList>
      </Menu>
    </Flex>
  );
};
```

When you run your React application, you will see that the navigation menu items are now grouped inside a dropdown menu.

## Styling the Navigation Bar

To make the navigation bar look more appealing, we can style it using Chakra UI's props.

First, import the necessary components and styles:

```javascript
import { Box, Flex, Text } from '@chakra-ui/react';
import { ChevronDownIcon } from '@chakra-ui/icons';
```

Now, update the `MenuButton` component as follows:

```javascript
<MenuButton 
  as={Text} 
  fontSize="lg" 
  fontWeight="bold" 
  color="gray.50" 
  _hover={{ color: 'white' }}
  rightIcon={<ChevronDownIcon />}
>
  Menu
</MenuButton>
```

This code sets the font size, font weight, color, and hover color for the dropdown button. It also adds a chevron down icon on the right side of the button.

You can also style the dropdown menu by updating the `MenuList` and `MenuItem` components:

```javascript
<MenuList bg="gray.800" color="white" borderRadius="md" p="2">
  <MenuItem _hover={{ bg: 'gray.900' }}>Home</MenuItem>
  <MenuItem _hover={{ bg: 'gray.900' }}>About</MenuItem>
  <MenuItem _hover={{ bg: 'gray.900' }}>Services</MenuItem>
  <MenuItem _hover={{ bg: 'gray.900' }}>Contact</MenuItem>
</MenuList>
```

This code sets the background color, text color, and hover color for the dropdown menu items.

And that's it! By following these steps, you have successfully implemented a dropdown navigation menu using Chakra UI. Feel free to customize the styles and add more functionality to suit your project's requirements.

#react #chakra-ui