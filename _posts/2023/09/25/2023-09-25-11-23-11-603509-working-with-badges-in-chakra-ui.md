---
layout: post
title: "Working with badges in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraUI]
comments: true
share: true
---

Chakra UI is a popular React component library that provides a powerful set of UI components for building web applications. One of the key features of Chakra UI is its support for badges, which can be used to visually represent important information or indicate the status of an element. In this blog post, we will explore how to work with badges in Chakra UI and demonstrate different use cases.

## Getting Started

To get started with badges in Chakra UI, you first need to install the Chakra UI package into your project. You can install it by running the following command:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once you have Chakra UI installed, you can import the necessary components for working with badges. The `Badge` component is the main component used for rendering badges in Chakra UI. You can import it as follows:

```jsx
import { Badge } from '@chakra-ui/react';
```

## Basic Usage

To use a badge, you can simply wrap it around the element you want to apply the badge to. The badge can be given a text label and an optional color:

```jsx
<Badge colorScheme="green">New</Badge>
```

In the above example, we created a badge with the label "New" and a green color scheme. You can customize the appearance of the badge by using the available props provided by Chakra UI, such as `variant`, `size`, and `borderRadius`.

## Variants

Chakra UI provides different variants for badges, allowing you to visually differentiate them based on their purpose. Here are a few examples of different badge variants:

- **Solid**: A solid colored badge, which can be used to highlight important information.
- **Outline**: An outlined badge, which can be used to provide minimal visual indication.
- **Subtle**: A subtle badge, which can be used to indicate a secondary or less important information.
- **Ghost**: A ghost badge, which can be used to blend with the background and provide a hint of presence.

You can set the variant of a badge by using the `variant` prop as follows:

```jsx
<Badge variant="solid" colorScheme="blue">Solid</Badge>
<Badge variant="outline" colorScheme="orange">Outline</Badge>
<Badge variant="subtle" colorScheme="gray">Subtle</Badge>
<Badge variant="ghost" colorScheme="purple">Ghost</Badge>
```

## Customization

Chakra UI badges can be easily customized to match the design of your application. You can change the color scheme, text color, size, and other styles of a badge by using the available props. For example:

```jsx
<Badge colorScheme="teal" textColor="white" size="sm">Custom</Badge>
```

In the above example, we set the color scheme to teal, text color to white, and size to small. Explore the Chakra UI documentation for a full list of available props and customization options.

## Conclusion

Badges are a useful component for visually indicating important information in your web applications. Chakra UI provides a simple and flexible way to work with badges, allowing you to easily customize their appearance and behavior. With the knowledge gained in this blog post, you can start incorporating badges into your Chakra UI powered projects and enhance the user experience.

#react #chakraUI