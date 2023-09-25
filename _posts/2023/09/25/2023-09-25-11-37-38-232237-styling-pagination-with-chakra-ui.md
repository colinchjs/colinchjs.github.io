---
layout: post
title: "Styling pagination with Chakra UI"
description: " "
date: 2023-09-25
tags: []
comments: true
share: true
---

If you're using React and Chakra UI for your project, you can easily style pagination to match your design requirements. Pagination is a common component used to navigate through long lists or data tables. In this blog post, we'll look at how to style pagination using Chakra UI.

## Getting Started

To get started, make sure you have Chakra UI installed in your project. You can install it by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once installed, import the necessary components in your code:

```jsx
import { Box, Button, Stack } from '@chakra-ui/react';
```

## Styling the Pagination Component

Chakra UI provides a rich set of components that can be easily customized to match your design. Here's an example of styling a simple pagination component:

```jsx
const Pagination = () => {
  return (
    <Box mt={4} display="flex" justifyContent="center">
      <Stack direction="row" spacing={2}>
        <Button size="sm" colorScheme="gray" variant="outline">
          Previous
        </Button>
        <Button size="sm" colorScheme="gray">
          1
        </Button>
        <Button size="sm" colorScheme="gray">
          2
        </Button>
        <Button size="sm" colorScheme="gray">
          3
        </Button>
        <Button size="sm" colorScheme="gray">
          Next
        </Button>
      </Stack>
    </Box>
  );
};
```

In the above code snippet, we create a `Pagination` component that renders a box with a set of buttons inside it. We use the `Stack` component to layout and space the buttons evenly. Each button represents a page number, and the "Previous" and "Next" buttons allow the user to navigate through the pages.

You can customize the appearance of the buttons by adding custom CSS styles or using Chakra UI's prop-based styling. For example, you can change the color scheme, size, or variant of the buttons to match your design.

## Conclusion

Styling pagination using Chakra UI is straightforward and customizable. With the help of Chakra UI's components and styling options, you can easily create a pagination component that matches your project's design requirements.