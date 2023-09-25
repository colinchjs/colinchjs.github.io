---
layout: post
title: "Creating dropdown menus with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI]
comments: true
share: true
---

Dropdown menus are a common component in many user interfaces, as they provide a convenient way to display a list of options for users to choose from. In this tutorial, we will learn how to create dropdown menus using Chakra UI, a popular UI component library for React.

## Installation

To get started, make sure you have Chakra UI installed in your project. You can install it via npm or yarn using the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```bash
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Usage

Once installed, you can import the necessary components from Chakra UI and start using the Dropdown component. Here's an example of how to create a basic dropdown menu:

```jsx
import { Menu, MenuButton, MenuList, MenuItem } from "@chakra-ui/react";

function DropdownMenu() {
  return (
    <Menu>
      <MenuButton>
        Open Menu
      </MenuButton>
      <MenuList>
        <MenuItem>Option 1</MenuItem>
        <MenuItem>Option 2</MenuItem>
        <MenuItem>Option 3</MenuItem>
      </MenuList>
    </Menu>
  );
}

export default DropdownMenu;
```

In this example, we import the necessary components from Chakra UI (`Menu`, `MenuButton`, `MenuList`, and `MenuItem`) and wrap them in a `Menu` component. The `MenuButton` is used as the trigger to open the dropdown menu, and the `MenuList` contains the list of options (`MenuItem`). 

## Customizing Dropdown Menu

Chakra UI provides a wide range of props to customize the appearance and behavior of the dropdown menu. You can customize the styling, add icons, handle events, and more. Here's an example of how to customize a dropdown menu:

```jsx
import { Menu, MenuButton, MenuList, MenuItem, IconButton } from "@chakra-ui/react";
import { MdArrowDropDown } from "react-icons/md";

function CustomDropdown() {
  return (
    <Menu>
      <MenuButton as={IconButton} icon={<MdArrowDropDown />} variant="outline" colorScheme="teal">
        Open Menu
      </MenuButton>
      <MenuList>
        <MenuItem icon={<IconBox />} onSelect={() => console.log("Option selected!")}>
          Option 1
        </MenuItem>
        <MenuItem icon={<IconBox />} onSelect={() => console.log("Option selected!")}>
          Option 2
        </MenuItem>
        <MenuItem icon={<IconBox />} onSelect={() => console.log("Option selected!")}>
          Option 3
        </MenuItem>
      </MenuList>
    </Menu>
  );
}

export default CustomDropdown;
```

In this example, we customize the `MenuButton` by using the `as` prop to render it as an `IconButton` component from Chakra UI. We also add the `icon` prop to display an arrow icon (`MdArrowDropDown`) and set the `variant` and `colorScheme` to customize the button's appearance. 

We can also add icons to the menu options by using the `icon` prop in each `MenuItem`. Additionally, we handle the `onSelect` event to log a message when an option is selected.

## Conclusion

Dropdown menus are a valuable component for enhancing user interfaces and providing a user-friendly way to present options. Using Chakra UI, creating and customizing dropdown menus becomes straightforward and flexible. With its extensive documentation and powerful set of components, Chakra UI makes it easier than ever to build modern and visually appealing UIs.

#UI #ChakraUI