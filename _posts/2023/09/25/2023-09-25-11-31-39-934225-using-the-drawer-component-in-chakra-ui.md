---
layout: post
title: "Using the Drawer component in Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, webdevelopment]
comments: true
share: true
---

The Drawer component in Chakra UI is a versatile component that allows you to display content in a collapsible panel, similar to a sidebar or modal. It is commonly used to reveal additional information or perform actions without taking up too much screen space.

To use the Drawer component in your Chakra UI project, follow these steps:

1. Install Chakra UI in your project:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

2. Import the required components in your file:

```jsx
import { Drawer, DrawerBody, DrawerOverlay, DrawerContent, DrawerHeader, DrawerFooter, DrawerCloseButton } from "@chakra-ui/react";
```

3. Set up the state to control the open and close behavior of the drawer:

```jsx
import { useState } from "react";

function MyComponent() {
  const [isOpen, setIsOpen] = useState(false);

  const onClose = () => {
    setIsOpen(false);
  };

  const onOpen = () => {
    setIsOpen(true);
  };

  return (
    <>
      <button onClick={onOpen}>Open Drawer</button>

      <Drawer isOpen={isOpen} onClose={onClose} size="md">
        <DrawerOverlay />
        <DrawerContent>
          <DrawerCloseButton />
          <DrawerHeader>Drawer Header</DrawerHeader>

          <DrawerBody>
            <p>Drawer Content</p>
          </DrawerBody>

          <DrawerFooter>
            <button onClick={onClose}>Close Drawer</button>
          </DrawerFooter>
        </DrawerContent>
      </Drawer>
    </>
  );
}
```

4. Customize the appearance and behavior of the Drawer component using the available props. For example, you can set the size using the `size` prop, which accepts values like `xs`, `sm`, `md`, `lg`, and `xl`.

```jsx
<Drawer isOpen={isOpen} onClose={onClose} size="md">
  {/* Drawer content */}
</Drawer>
```

And that's it! You have successfully used the Drawer component from Chakra UI in your project. Explore the Chakra UI documentation for more customization options and advanced usage.

#chakraui #webdevelopment