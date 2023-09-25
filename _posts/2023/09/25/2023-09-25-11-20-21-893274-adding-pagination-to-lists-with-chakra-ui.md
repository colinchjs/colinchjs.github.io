---
layout: post
title: "Adding pagination to lists with Chakra UI"
description: " "
date: 2023-09-25
tags: [pagination, chakraUI]
comments: true
share: true
---

In web development, it's common to encounter situations where you have a large list of items to display and you want to make it more user-friendly by adding pagination. Pagination allows users to navigate through the list by displaying a certain number of items per page.

In this blog post, we'll explore how to add pagination to lists using Chakra UI, a popular UI component library for React.

## Installing Chakra UI

To get started, let's install Chakra UI in our React project:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating a Paginated List Component

First, let's create a basic list component that fetches and displays a list of items. We'll use an array of sample data for simplicity. Here's an example of how the component might look:

```jsx
import React from 'react';

const ListComponent = () => {
  const items = ['Item 1', 'Item 2', 'Item 3', 'Item 4', 'Item 5'];

  return (
    <>
      {items.map((item, index) => (
        <div key={index}>{item}</div>
      ))}
    </>
  );
};

export default ListComponent;
```

## Adding Pagination

Next, let's add pagination functionality to our list component using Chakra UI. Chakra UI provides a `Stack` component that we'll use to display our paginated items. We'll also need a state variable to keep track of the current page.

Here's an updated version of our list component with pagination implemented:

```jsx
import React, { useState } from 'react';
import { Stack, Button } from '@chakra-ui/react';

const ListComponent = () => {
  const itemsPerPage = 3;
  const items = ['Item 1', 'Item 2', 'Item 3', 'Item 4', 'Item 5'];
  const [currentPage, setCurrentPage] = useState(1);

  const totalPages = Math.ceil(items.length / itemsPerPage);
  const indexOfLastItem = currentPage * itemsPerPage;
  const indexOfFirstItem = indexOfLastItem - itemsPerPage;
  const currentItems = items.slice(indexOfFirstItem, indexOfLastItem);

  const handlePreviousPage = () => {
    if (currentPage > 1) {
      setCurrentPage(currentPage - 1);
    }
  };

  const handleNextPage = () => {
    if (currentPage < totalPages) {
      setCurrentPage(currentPage + 1);
    }
  };

  return (
    <>
      <Stack spacing={4}>
        {currentItems.map((item, index) => (
          <div key={index}>{item}</div>
        ))}
      </Stack>
      <Button onClick={handlePreviousPage} isDisabled={currentPage === 1}>
        Previous Page
      </Button>
      <Button onClick={handleNextPage} isDisabled={currentPage === totalPages}>
        Next Page
      </Button>
    </>
  );
};

export default ListComponent;
```

## Styling and Customization

Chakra UI provides a variety of styling options and customization capabilities. You can further enhance your paginated list component by applying your own styles, adding animations, or customizing the buttons' appearance.

By implementing pagination using Chakra UI, your website or application will provide a better user experience for navigating through long lists of items.

#pagination #chakraUI