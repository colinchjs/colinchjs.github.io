---
layout: post
title: "Styling components in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ReactUI]
comments: true
share: true
---

Chakra UI is a popular React component library that provides a set of customizable, accessible, and composable UI components. It allows developers to easily create beautiful UIs with minimal effort. In this blog post, we will explore how to style components in Chakra UI.

## Getting Started with Chakra UI

To start using Chakra UI in your React project, you need to install it first. Run the following command in your terminal:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Next, you need to wrap your application with the `ChakraProvider` to make Chakra UI components available to your application. In your `App.js` or equivalent file, import and wrap your component tree like this:

```jsx
import { ChakraProvider } from "@chakra-ui/react";

function App() {
  return (
    <ChakraProvider>
      {/* Your component tree */}
    </ChakraProvider>
  );
}

export default App;
```

Now that you have Chakra UI set up in your project, let's see how you can style components using Chakra UI's styling system.

## Styling Components Using Style Props

Chakra UI provides an intuitive way to style components using style props. These style props allow you to customize various aspects of the component's appearance, such as color, typography, spacing, and more.

For example, to set the background color of a `Button` component to blue, you can use the `bg` prop:

```jsx
import { Button } from "@chakra-ui/react";

function MyComponent() {
  return (
    <Button bg="blue.500" color="white">
      Click me
    </Button>
  );
}
```

In the above code, the `bg` prop sets the background color to `blue.500`, and the `color` prop sets the text color to `white`.

Chakra UI's style props follow a consistent naming convention. For example, to set the margin of an element, you can use the `m` prop, and to set the padding, you can use the `p` prop.

## Extending Component Styles

Chakra UI allows you to extend the styles of its components using the `chakra` function. The `chakra` function returns a new component with extended styles that you can use in your application.

For example, let's say you want to create a custom `CustomButton` component that extends the `Button` component from Chakra UI:

```jsx
import { Button, chakra } from "@chakra-ui/react";

const CustomButton = chakra(Button, {
  baseStyle: {
    borderRadius: "md",
    fontWeight: "bold",
  },
});

function MyComponent() {
  return <CustomButton colorScheme="pink">Click me</CustomButton>;
}
```

In the above code, the `chakra` function extends the styles of the `Button` component and applies the specified `baseStyle` to the `CustomButton`. You can then use the `CustomButton` component as you would use the regular `Button` component, but with the additional extended styles.

## Conclusion

Styling components in Chakra UI is simple and intuitive. With the help of style props and the ability to extend component styles, you can easily customize the appearance of Chakra UI components to match your design requirements. By using Chakra UI, you can save time and effort in styling your React UI and focus more on building your application.

## #ChakraUI #ReactUI #ComponentStyling