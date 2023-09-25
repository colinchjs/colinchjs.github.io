---
layout: post
title: "Creating a menu component with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

In this tutorial, we'll learn how to create a menu component using Chakra UI, a popular React component library. Menus are a common feature in web applications and can provide a convenient and visually appealing way to access different sections or options.

## Getting Started

To begin, make sure you have Chakra UI installed in your React project. You can install it via npm or yarn by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once installed, import the necessary components from Chakra UI in your desired file:

```javascript
import { Box, Menu, MenuButton, MenuList, MenuItem, MenuDivider } from '@chakra-ui/react';
```

## Creating the Menu Component

Let's start by creating a basic functional component called `MenuComponent` and rendering a simple menu button and menu list:

```javascript
const MenuComponent = () => {
  return (
    <Menu>
      <MenuButton as={Button}>Menu</MenuButton>
      <MenuList>
        <MenuItem>Option 1</MenuItem>
        <MenuItem>Option 2</MenuItem>
        <MenuDivider />
        <MenuItem>Option 3</MenuItem>
      </MenuList>
    </Menu>
  );
}

export default MenuComponent;
```

In the above code, `Menu` acts as the wrapper component for the menu, `MenuButton` renders the button that triggers the menu, and `MenuList` contains the list of menu items. We have also included a `MenuDivider` component to separate the options.

## Styling the Menu Component

Chakra UI provides a convenient way to style components using its `styleProps`. Let's make our menu more visually appealing by customizing its appearance:

```javascript
const MenuComponent = () => {
  return (
    <Menu>
      <MenuButton as={Button} colorScheme="blue" size="md">
        Menu
      </MenuButton>
      <MenuList bg="white" color="black" border="1px solid" borderColor="gray.200" borderRadius="md">
        <MenuItem _hover={{ bg: 'gray.100' }}>Option 1</MenuItem>
        <MenuItem _hover={{ bg: 'gray.100' }}>Option 2</MenuItem>
        <MenuDivider />
        <MenuItem _hover={{ bg: 'gray.100' }}>Option 3</MenuItem>
      </MenuList>
    </Menu>
  );
}

export default MenuComponent;
```

In the above code, we have added some style props to the components. For example, `colorScheme="blue"` sets the button's color to blue, `bg="white"` sets the background color of the menu list to white, and `_hover={{ bg: 'gray.100' }}` changes the background color of menu items on hover to gray.100.

## Conclusion

Creating a menu component with Chakra UI is simple and provides seamless integration into your React project. With Chakra UI's style props, you have full control over the appearance and customization of your menu.

#ChakraUI #React