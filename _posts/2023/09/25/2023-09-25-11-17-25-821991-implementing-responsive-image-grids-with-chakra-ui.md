---
layout: post
title: "Implementing responsive image grids with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

Responsive image grids are a common component used in modern web design to showcase a collection of images in an organized and visually appealing manner. Chakra UI is a popular React component library that provides a set of customizable UI components, including a grid system. In this blog post, we will explore how to use Chakra UI to implement responsive image grids in your React application.

## Getting Started with Chakra UI

Before we begin implementing the responsive image grid, it's important to have Chakra UI set up in your React project. Here's a step-by-step guide on how to get started:

1. Install Chakra UI in your React project by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

2. Wrap your application with the `ChakraProvider` component, which provides Chakra UI styles and theme to your components:

```jsx
import { ChakraProvider } from "@chakra-ui/react";

function App() {
  return (
    <ChakraProvider>
      {/* Your components here */}
    </ChakraProvider>
  );
}

export default App;
```

## Creating the Responsive Image Grid

With Chakra UI set up, we can now proceed to create the responsive image grid component. The grid component in Chakra UI is provided by the `SimpleGrid` component. It allows us to define the number of columns and their breakpoints for different screen sizes.

Here's an example of how we can create a responsive image grid with Chakra UI:

```jsx
import { SimpleGrid } from "@chakra-ui/react";

function ImageGrid() {
  return (
    <SimpleGrid columns={[1, 2, 3]} spacing={4}>
      <img src="image1.jpg" alt="Image 1" />
      <img src="image2.jpg" alt="Image 2" />
      <img src="image3.jpg" alt="Image 3" />
      {/* Add more images here */}
    </SimpleGrid>
  );
}

export default ImageGrid;
```

In the above code, we have used the `SimpleGrid` component and set the `columns` prop to an array of values `[1, 2, 3]`. This means that we want the grid to have 1 column on small screens, 2 columns on medium screens, and 3 columns on large screens. The `spacing` prop is used to define the gap between the grid items.

## Making the Image Grid Responsive

To make the image grid truly responsive, we can use CSS to control the size of the images based on the available grid space. We can achieve this by defining a CSS class and applying it to the `img` elements within the grid.

Here's an example CSS class that scales the images proportionally based on the available grid space:

```css
.grid-img {
  width: 100%;
  height: auto;
}
```

To apply this class to the images in the grid, update the `ImageGrid` component as follows:

```jsx
// ...

function ImageGrid() {
  return (
    <SimpleGrid columns={[1, 2, 3]} spacing={4}>
      <img src="image1.jpg" alt="Image 1" className="grid-img" />
      <img src="image2.jpg" alt="Image 2" className="grid-img" />
      <img src="image3.jpg" alt="Image 3" className="grid-img" />
      {/* Add more images here */}
    </SimpleGrid>
  );
}

// ...
```

By setting the `width` of the images to `100%` and the `height` to `auto`, the images will automatically scale within the grid columns, maintaining their aspect ratio.

## Conclusion

In this blog post, we have explored how to implement responsive image grids using the Chakra UI component library in a React application. By utilizing the `SimpleGrid` component and applying CSS to control the size of the images, we can create visually appealing and responsive grids to showcase a collection of images in a user-friendly manner.

Whether you are building a portfolio, a gallery, or any application that requires showcasing images, Chakra UI's responsive image grid can be a useful component to have in your toolbox.

#React #ChakraUI