---
layout: post
title: "Building a notification component with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ReactJS]
comments: true
share: true
---

Notifications are an essential part of any web application or website, as they allow us to provide important information or updates to our users. In this tutorial, we'll explore how to build a notification component using Chakra UI, a simple and accessible component library for React.

## Getting Started

Before we begin, make sure you have a basic understanding of React and have Chakra UI installed in your project. If not, you can install it by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once Chakra UI is installed, we can start building our notification component.

## Setting up the Component

First, let's create a new file called `Notification.js` and import the necessary components and hooks from Chakra UI:

```jsx
import { Box, CloseButton, Flex, Text } from "@chakra-ui/react";
import { useState } from "react";
```

Next, we define our `Notification` component, which will be a functional component that takes the notification message and type as props:

```jsx
const Notification = ({ message, type }) => {
  const [isOpen, setIsOpen] = useState(true);

  const handleClose = () => {
    setIsOpen(false);
  };

  return (
    <Box
      bg={type === "success" ? "green.500" : "red.500"}
      color="white"
      p={4}
      borderRadius="md"
      mb={4}
      display={isOpen ? "flex" : "none"}
    >
      <Flex flex={1} align="center">
        <Text fontSize="sm" fontWeight="bold">
          {message}
        </Text>
      </Flex>
      <CloseButton size="sm" onClick={handleClose} />
    </Box>
  );
};

export default Notification;
```

In the code above, we use the `useState` hook to manage the state of the notification. We set the initial state as `true` to show the notification by default. The `handleClose` function sets the state to `false` when the close button is clicked.

The `Notification` component renders a `Box` component from Chakra UI, which serves as the notification container. The background color and text color are determined based on the `type` prop passed to the component. The notification message is rendered inside a `Text` component, and a `CloseButton` is added to allow users to dismiss the notification.

## Using the Notification Component

To use our newly created `Notification` component, import it into your desired component:

```jsx
import { Button } from "@chakra-ui/react";
import Notification from "./Notification";

const App = () => {
  const handleNotification = () => {
    // Some event or action that triggers the notification
  };

  return (
    <div>
      <Button onClick={handleNotification}>Show Notification</Button>
      <Notification message="Notification message here" type="success" />
    </div>
  );
};

export default App;
```

In the example above, we import and render the `Button` component from Chakra UI. On clicking the button, it triggers the `handleNotification` function, which could be linked to some event or action in your application. We also include the `Notification` component with a `message` prop and a `type` prop, which determines the style and color of the notification.

## Conclusion

By using Chakra UI, we can easily create a reusable and customizable notification component for our React applications. The flexibility offered by the Chakra UI library allows for easy customization and styling, making it a great choice for building user interfaces.

#ChakraUI #ReactJS