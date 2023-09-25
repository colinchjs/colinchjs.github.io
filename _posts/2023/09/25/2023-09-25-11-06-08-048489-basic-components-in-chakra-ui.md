---
layout: post
title: "Basic components in Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, webdevelopment]
comments: true
share: true
---

## Installation

To get started with Chakra UI, you need to first install it as a dependency in your project. You can do this using npm or yarn. Here's an example using npm:

```javascript
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Components

### 1. Box

The `Box` component is the most basic building block in Chakra UI. It acts as a wrapper component and can be used to create layout containers or to style individual elements. It provides a wide range of properties for styling such as `width`, `height`, `background`, `border`, `padding`, and `margin`. Here's an example of using the `Box` component:

```jsx
import { Box } from "@chakra-ui/react";

const App = () => (
  <Box bg="red.200" p="4" rounded="md">
    This is a Box component
  </Box>
);
```

### 2. Button

The `Button` component is used for creating interactive buttons in your application. It supports various styles and sizes, and can be easily customized to match your design system. Here's an example of using the `Button` component:

```jsx
import { Button } from "@chakra-ui/react";

const App = () => (
  <Button colorScheme="blue" size="lg">
    Click me
  </Button>
);
```

### 3. Input

The `Input` component is used for capturing user input, such as text or numbers. It supports various input types like text, email, password, etc. Additionally, it provides validation and error handling capabilities. Here's an example of using the `Input` component:

```jsx
import { Input } from "@chakra-ui/react";

const App = () => (
  <Input type="text" placeholder="Enter your name" />
);
```

## Conclusion

Chakra UI provides a rich set of components that can be used to build beautiful and responsive user interfaces. In this blog post, we explored some of the basic components like `Box`, `Button`, and `Input`. However, Chakra UI offers many more components and utilities that can assist in creating robust web applications.

Start using Chakra UI in your next project and experience the ease and flexibility it brings to your UI development process. #chakraui #webdevelopment