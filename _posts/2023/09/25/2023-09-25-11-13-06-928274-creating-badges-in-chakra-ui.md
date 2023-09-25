---
layout: post
title: "Creating badges in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, Badges]
comments: true
share: true
---

Badges are a great way to visually highlight important information or provide additional context to your UI. With Chakra UI, a popular React component library, it's super easy to create stylish and customizable badges. In this blog post, we'll explore how to create badges in Chakra UI and showcase some examples.

## Setting Up Chakra UI

Before we dive into creating badges, make sure you have Chakra UI installed in your React project. If you haven't done this already, you can install it using npm or yarn.

```javascript
// Using npm
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion

// Using yarn
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Next, you need to wrap your application with the ChakraProvider in your root component.

```jsx
import { ChakraProvider } from "@chakra-ui/react";

function App() {
  return (
    <ChakraProvider>
      {/* Your application code */}
    </ChakraProvider>
  );
}

export default App;
```

## Creating a Basic Badge

To create a basic badge in Chakra UI, you can use the `Badge` component. The `Badge` component accepts various props to customize its appearance.

```jsx
import { Badge } from "@chakra-ui/react";

function MyComponent() {
  return (
    <Badge colorScheme="purple" variant="solid">
      New
    </Badge>
  );
}
```

In the above example, we've set the `colorScheme` prop to "purple" to give the badge a purple background color. The `variant` prop is set to "solid" to make the badge have a solid fill. You can experiment with different color schemes and variants based on your UI requirements.

## Adding Text to Badges

You can easily add text or icons to badges to provide more context. You can either wrap the content inside the `Badge` component or use the `BadgeLabel` component.

```jsx
import { Badge, BadgeLabel } from "@chakra-ui/react";

function MyComponent() {
  return (
    <Badge colorScheme="blue" variant="subtle">
      {/* Wrap content directly */}
      New

      {/* Or use BadgeLabel component */}
      <BadgeLabel>Alert!</BadgeLabel>
    </Badge>
  );
}
```

The above example demonstrates two ways to add content to badges. You can choose the method that suits your needs and preferences.

## Customizing Badge Appearance

Chakra UI provides a wide range of props for customizing badge appearance. Here are some of the commonly used props:

- `colorScheme`: Specifies the color scheme of the badge.
- `variant`: Sets the badge variant, such as "subtle", "solid", or "outline".
- `size`: Adjusts the size of the badge.
- `fontSize`: Sets the font size of the badge text.
- `borderRadius`: Specifies the border radius of the badge.
- `p`: Sets the padding of the badge.

Feel free to experiment with these props and discover the possibilities of creating unique badge styles.

## Conclusion

In this blog post, we explored how to create badges using Chakra UI. We covered the basics of setting up Chakra UI in a React project and showcased examples of creating badges with different styles and customizations. With Chakra UI's flexible and versatile components, you can easily create visually appealing badges to enhance your UI. Start incorporating badges in your projects today and make your UI elements stand out!

#ChakraUI #Badges