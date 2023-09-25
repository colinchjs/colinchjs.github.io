---
layout: post
title: "Implementing breadcrumbs with Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraUI, breadcrumbs]
comments: true
share: true
---

Breadcrumbs are a useful navigational component that provides users with a trail of links indicating their current location within a website or application. They are typically used in multi-level navigation structures, making it easier for users to navigate back to previous pages or sections.

In this blog post, we'll explore how to implement breadcrumbs using the Chakra UI library in a React application. Chakra UI is a popular component library that provides a set of composable, accessible, and customizable UI components.

Let's get started!

## Setting up Chakra UI

First, we need to set up Chakra UI in our React application. If you haven't already, make sure to install the Chakra UI package by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Next, we need to wrap our application with the `ChakraProvider` component at the root level. This allows us to use Chakra UI components throughout our application. Here's an example of how you can set up the provider:

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

## Creating the Breadcrumbs Component

Now that we have Chakra UI set up, let's proceed with creating the breadcrumbs component. We'll define a functional component called `Breadcrumbs` that accepts an array of breadcrumb items as a prop.

Here's an example implementation of the `Breadcrumbs` component:

```jsx
import { Breadcrumb, BreadcrumbItem, BreadcrumbLink } from "@chakra-ui/react";

function Breadcrumbs({ items }) {
  return (
    <Breadcrumb separator=">" spacing="8px" fontSize="sm">
      {items.map((item, index) => (
        <BreadcrumbItem key={index}>
          {index !== items.length - 1 ? (
            <BreadcrumbLink href={item.url}>{item.label}</BreadcrumbLink>
          ) : (
            <BreadcrumbLink as="span" fontWeight="bold">
              {item.label}
            </BreadcrumbLink>
          )}
        </BreadcrumbItem>
      ))}
    </Breadcrumb>
  );
}

export default Breadcrumbs;
```

In this example, we iterate over the `items` prop using the `map` function to render each breadcrumb item. If the item is not the last one in the array, we render it as a link using the `BreadcrumbLink` component. Otherwise, we render it as a span element with a bold font weight.

## Using the Breadcrumbs Component

To use the `Breadcrumbs` component in your application, you can pass an array of breadcrumb items as a prop. Each item should have a `label` and `url` property.

Here's an example of how you can use the `Breadcrumbs` component:

```jsx
import Breadcrumbs from './Breadcrumbs';

function App() {
  const breadcrumbs = [
    { label: "Home", url: "/" },
    { label: "Products", url: "/products" },
    { label: "Shoes", url: "/products/shoes" },
    { label: "Running Shoes" }
  ];

  return (
    <div>
      <Breadcrumbs items={breadcrumbs} />
      {/* Rest of your application */}
    </div>
  );
}

export default App;
```

In this example, we pass an array of breadcrumb items to the `Breadcrumbs` component. The last item, "Running Shoes", is rendered without a link since it represents the current page/section.

## Conclusion

With the help of Chakra UI, implementing breadcrumbs in your React application is a breeze. The `Breadcrumbs` component allows you to easily create a visual trail for your users, enhancing the overall user experience.

Remember to follow the documentation and guidelines of Chakra UI for further customization and styling options.

#chakraUI #breadcrumbs