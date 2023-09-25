---
layout: post
title: "Building a sticky header with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

In this tutorial, we will learn how to build a sticky header using Chakra UI, a popular UI library for React. A sticky header is a fixed header that remains visible at the top of the page even when the user scrolls down.

## Prerequisites

Before we get started, make sure you have the following installed:

- Node.js and npm (Node Package Manager)
- React and Chakra UI

## Setting up the Project

First, let's create a new React project and install Chakra UI:

```bash
npx create-react-app sticky-header
cd sticky-header
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Next, open the project in your preferred code editor.

## Creating the Sticky Header Component

In the `src` directory, create a new file called `Header.js`. This will be our main component for the sticky header.

```jsx
import { Box } from "@chakra-ui/react";

const Header = () => {
  return (
    <Box
      position="sticky"
      top="0"
      zIndex="10"
      bg="gray.100"
      p="4"
      boxShadow="md"
    >
      {/* Content of the header */}
    </Box>
  );
};

export default Header;
```

In the `Box` component, we have set the `position` to `sticky`, `top` to `0` to keep it fixed at the top of the page, `zIndex` to `10` for stacking order, `bg` (background) to `gray.100`, `p` (padding) to `4`, and `boxShadow` to `md` for a subtle shadow effect.

You can customize the styles according to your needs and add the content of the header within the `Box` component.

## Implementing the Sticky Header

Next, open the `App.js` file and import the `Header` component:

```jsx
import Header from "./Header";

const App = () => {
  return (
    <div>
      <Header />
      {/* Rest of your app */}
    </div>
  );
};

export default App;
```

The `Header` component is now rendered at the top of the app.

## Styling the Sticky Header

To style the content of the `Header` component, you can use the various Chakra UI components such as `Flex`, `Text`, `Button`, etc.

For example, to add a logo and navigation links to the header:

```jsx
import { Box, Flex, Text, Button } from "@chakra-ui/react";

const Header = () => {
  return (
    <Flex
      as="header"
      align="center"
      justify="space-between"
      position="sticky"
      top="0"
      zIndex="10"
      bg="gray.100"
      p="4"
      boxShadow="md"
    >
      <Box>
        <Text fontSize="xl" fontWeight="bold">
          My Logo
        </Text>
      </Box>
      <Flex align="center">
        <Button mx="2">Home</Button>
        <Button mx="2">About</Button>
        <Button mx="2">Contact</Button>
      </Flex>
    </Flex>
  );
};

export default Header;
```

Here, we have used the `Flex` component to create a header container, `Text` component for the logo, and `Button` components for navigation links.

Feel free to customize the styles and add more components to suit your application's requirements.

## Conclusion

With Chakra UI, building a sticky header in React becomes a breeze. Utilizing the `Box` and other components, we can easily create a visually appealing and functional sticky header that enhances the user experience.

Remember to import the necessary dependencies and follow the Chakra UI documentation to explore additional styling options and features.

Happy coding! #React #ChakraUI