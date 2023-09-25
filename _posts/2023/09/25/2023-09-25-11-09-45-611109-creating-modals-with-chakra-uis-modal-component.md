---
layout: post
title: "Creating modals with Chakra UI's Modal component"
description: " "
date: 2023-09-25
tags: [ChakraUI, ModalComponent]
comments: true
share: true
---

Chakra UI is a simple and accessible UI component library that provides out-of-the-box styling and powerful features to build responsive and user-friendly interfaces. Let's dive into how to create modals using Chakra UI's Modal component.

## Installation

To begin, make sure you have Chakra UI installed in your project. You can install it via npm or yarn by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating a basic modal

To create a basic modal, start by importing the necessary components from Chakra UI:

```jsx
import { Button } from "@chakra-ui/button";
import { Modal, ModalBody, ModalCloseButton, ModalContent, ModalFooter, ModalHeader, ModalOverlay } from "@chakra-ui/modal";
import { useState } from "react";
```

Next, define a state variable to control the visibility of the modal:

```jsx
const [isOpen, setIsOpen] = useState(false);
```

Inside your component, you can now render the modal component:

```jsx
<Button onClick={() => setIsOpen(true)}>Open Modal</Button>

<Modal isOpen={isOpen} onClose={() => setIsOpen(false)}>
  <ModalOverlay />
  <ModalContent>
    <ModalHeader>Create a new post</ModalHeader>
    <ModalCloseButton />
    <ModalBody>
      {/* Your form or additional content goes here */}
    </ModalBody>
    <ModalFooter>
      <Button colorScheme="blue" mr={3} onClick={() => setIsOpen(false)}>
        Save
      </Button>
      <Button onClick={() => setIsOpen(false)}>Cancel</Button>
    </ModalFooter>
  </ModalContent>
</Modal>
```

In the example above, we use the `Button` component as a trigger to open the modal. When clicked, the `isOpen` state variable is set to `true`, making the modal visible. The `onClose` prop is used to handle closing the modal by setting `isOpen` back to `false`.

The `Modal` component contains several subcomponents like `ModalOverlay`, `ModalContent`, `ModalHeader`, `ModalCloseButton`, `ModalBody`, and `ModalFooter` that allow you to structure and customize the modal as needed.

## Customizing the modal

You can further customize the appearance and behavior of your modal by applying styles and adding event handlers. Chakra UI provides default styles, but you can override them using the `modal` object in the `theme` configuration.

For example, to change the background color of the modal content, you can add the following styles:

```jsx
import { extendTheme } from "@chakra-ui/react";

const theme = extendTheme({
  components: {
    Modal: {
      baseStyle: {
        content: {
          bg: "white",
        },
      },
    },
  },
});
```

By applying custom styling, you can ensure that the modals blend seamlessly with the rest of your application's design.

## Conclusion

With Chakra UI's Modal component, you can easily create and customize modals in your React application. Modals provide a clean and organized way to display additional information or capture user input without sacrificing the user experience. Explore Chakra UI's documentation for more advanced features and customization options.

#ChakraUI #ModalComponent