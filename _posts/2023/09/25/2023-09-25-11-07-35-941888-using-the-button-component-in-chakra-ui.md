---
layout: post
title: "Using the Button component in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

Chakra UI is a popular **React component library** that provides ready-to-use components for building modern user interfaces. One of the core components in Chakra UI is the Button component, which makes it easy to create stylish and interactive buttons in your applications.

To start using the Button component in Chakra UI, you first need to install the library using npm or yarn:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once the installation is complete, you can import and use the Button component in your React components:

```javascript
import { Button } from "@chakra-ui/react";

function App() {
  return (
    <Button colorScheme="blue" size="md">
      Click me
    </Button>
  );
}

export default App;
```

In the above example, we import the Button component from the `@chakra-ui/react` package. We then use the Button component with some props to specify the color scheme (`colorScheme="blue"`) and size (`size="md"`). The text inside the button is defined as "Click me".

The `colorScheme` prop allows you to easily set the color scheme of the button. Chakra UI provides several predefined color schemes like "blue", "green", "red", etc. You can also customize the color schemes to match your application's design.

Similarly, the `size` prop allows you to specify the size of the button. Chakra UI provides options like "sm" (small), "md" (medium), and "lg" (large).

The Button component in Chakra UI also supports other props such as `onClick`, `isLoading`, and `disabled` to handle click events, loading states, and disable the button, respectively.

By using the Button component from Chakra UI, you can quickly create visually appealing and responsive buttons in your React applications, saving development time and effort.

#ChakraUI #React