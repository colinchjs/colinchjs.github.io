---
layout: post
title: "Adding scrollbars to Chakra UI components"
description: " "
date: 2023-09-25
tags: [chakraui, scrollbars]
comments: true
share: true
---

Chakra UI is a popular library that provides a set of accessible and customizable UI components for building React applications. While Chakra UI offers a wide range of components with various functionalities, it doesn't include built-in scrollbars. However, you can easily add scrollbars to Chakra UI components by leveraging CSS properties.

In this blog post, we will walk through the process of adding scrollbars to Chakra UI components using custom CSS. Let's get started!

## Step 1: Import Chakra UI Components

First, make sure you have Chakra UI installed and imported into your project. You can install it via npm or yarn:

```javascript
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

```javascript
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Then, import the required Chakra UI components into your file:

```javascript
import { Box, Flex } from "@chakra-ui/react";
```

## Step 2: Create a Custom CSS Class

To add scrollbars to your Chakra UI components, you need to create a custom CSS class with the desired scrollbar styles. In this example, we'll create a class called `scrollable`:

```css
.scrollable {
  overflow: auto;
  scrollbar-width: thin;
  scrollbar-color: gray lightgray;
}
```

Make sure to adjust the scrollbar colors to match your application's style.

## Step 3: Apply the Custom CSS Class

Now that you have your custom CSS class defined, you can apply it to any Chakra UI component where you want to enable scrolling. For example, if you want to add scrollbars to a `Box` component, you can add the `scrollable` class to it:

```javascript
<Box className="scrollable">
  {/* Content */}
</Box>
```

Alternatively, you can apply the class directly to the component using the `className` prop. The same applies to other Chakra UI components such as `Flex`, `Grid`, or `Text`.

## Step 4: Adjust Component Dimensions

In some cases, you might need to adjust the dimensions of your Chakra UI component to enable scrolling properly. You can do this by setting a fixed height or width and applying appropriate CSS styles.

For instance, if you want to add vertical scrolling to a `Box` component, make sure it has a defined height:

```javascript
<Box className="scrollable" h="300px">
  {/* Content */}
</Box>
```

Remember to adapt the height value according to your requirements.

## Conclusion

By following the steps outlined in this blog post, you can easily add scrollbars to Chakra UI components using custom CSS. This allows you to enhance the user experience of your application by handling content overflow gracefully.

Remember that you can further customize the scrollbar appearance and behavior by adjusting the CSS properties. Experiment with different styles to align with your application's design language.

#chakraui #scrollbars #css