---
layout: post
title: "Implementing breadcrumbs with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, breadcrumbs]
comments: true
share: true
---

Breadcrumbs are a useful navigation component that allows users to track their location within a website or application. With the Chakra UI library, you can easily implement breadcrumbs in your React project.

## Installation

First, make sure you have Chakra UI installed in your project. You can install it using npm or yarn:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```bash
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Usage

To implement breadcrumbs, you'll need a way to store the navigation hierarchy and render the breadcrumbs component. Here's an example of how you can achieve this with Chakra UI:

1. Create a Breadcrumbs component to render the breadcrumb navigation:

```jsx
import { Breadcrumb, BreadcrumbItem, BreadcrumbLink } from "@chakra-ui/react";

const Breadcrumbs = ({ items }) => {
  return (
    <Breadcrumb separator=">" spacing="8px">
      {items.map((item, index) => (
        <BreadcrumbItem key={index}>
          {index !== items.length - 1 ? (
            <BreadcrumbLink href={item.href}>{item.label}</BreadcrumbLink>
          ) : (
            <BreadcrumbLink>{item.label}</BreadcrumbLink>
          )}
        </BreadcrumbItem>
      ))}
    </Breadcrumb>
  );
};

export default Breadcrumbs;
```

2. In your component where you want to display the breadcrumbs, create an array of objects representing each breadcrumb item:

```jsx
import { Box } from "@chakra-ui/react";
import Breadcrumbs from "./Breadcrumbs";

const MyComponent = () => {
  const breadcrumbs = [
    { label: "Home", href: "/" },
    { label: "Category", href: "/category" },
    { label: "Subcategory", href: "/category/subcategory" },
    { label: "Current Page" },
  ];

  return (
    <Box>
      <Breadcrumbs items={breadcrumbs} />
      {/* Rest of your component */}
    </Box>
  );
};

export default MyComponent;
```

In the above example, we pass the `items` array to the `Breadcrumbs` component which renders the breadcrumbs based on the provided hierarchy. The last breadcrumb item does not require a `href` as it represents the current page.

## Styling

You can customize the styling of the breadcrumbs using Chakra UI's `Breadcrumb` component and its props. For example, you can change the separator character by setting the `separator` prop.

```jsx
<Breadcrumb separator="-" spacing="8px">
  {/* Breadcrumb items */}
</Breadcrumb>
```

You can also apply your own custom styles using CSS-in-JS or Chakra UI's `style` prop.

## Conclusion

With Chakra UI, implementing breadcrumbs in your React project is a breeze. The `Breadcrumb` component and its related components make it easy to render and style breadcrumbs according to your requirements. Enhance your website or application's navigation by adding breadcrumbs to provide a clear and intuitive user experience.

```hashtags
#ChakraUI #breadcrumbs
```