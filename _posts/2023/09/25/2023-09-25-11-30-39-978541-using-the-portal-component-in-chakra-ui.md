---
layout: post
title: "Using the Portal component in Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, react]
comments: true
share: true
---

Chakra UI is a popular UI library for React that provides a set of accessible and customizable components. One of the useful components it offers is the "Portal" component, which allows you to render a component's children outside of its parent DOM hierarchy. This can be particularly useful when you want to render a component at the top level of the application, such as modals, tooltips, or dropdown menus.

## Why use the Portal component?

The Portal component in Chakra UI offers several benefits:

1. **Accessibility**: It ensures that the portal content is still accessible to screen readers and other assistive technologies.

2. **Prevents CSS Clashing**: By rendering content outside of the parent DOM hierarchy, it prevents CSS clashes that may occur when applying styles to parent and child components.

3. **Z-Index Management**: When rendering content at the top level, you can easily manage the z-index to control the stacking order of elements.

## How to use the Portal component in Chakra UI

Using the Portal component in Chakra UI is straightforward. Here's an example of how to use it:

```jsx
import { Portal } from "@chakra-ui/react";

function App() {
  return (
    <div>
      <h1>My App</h1>
      <Portal>
        <div>Rendered outside the parent div</div>
      </Portal>
    </div>
  );
}
```

In the example above, we import the Portal component from the `@chakra-ui/react` package and wrap the content we want to render outside of the parent div with the Portal component. The content will be rendered as a sibling of the root div where the ChakraProvider is rendered.

It's important to note that the Portal component does not accept a parent prop. Instead, it detects the nearest ChakraProvider component as the parent.

## Conclusion

The Portal component in Chakra UI is a powerful tool for rendering components outside of the parent DOM hierarchy. It provides accessibility, prevents CSS clashes, and makes z-index management easier. By using the Portal component, you can create more flexible and interactive UI components in your React applications.

#chakraui #react