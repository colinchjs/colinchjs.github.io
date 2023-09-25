---
layout: post
title: "Building table layouts with Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, react]
comments: true
share: true
---

In web development, tables are a common way to display data in a structured manner. However, building and styling tables can be a tedious task. Thankfully, with the help of Chakra UI, a popular React component library, creating visually appealing and responsive table layouts becomes a breeze.

## Installation

Before we begin, make sure you have Chakra UI installed in your React project. You can install it using npm or yarn:

```bash
npm install @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^5
```
or
```bash
yarn add @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^5
```

## Creating a simple table

Let's start by creating a basic table layout using Chakra UI components. We will create a table with two columns: Name and Email.

```jsx
import { Table, Thead, Tbody, Tr, Th, Td } from '@chakra-ui/react';

const TableLayout = () => {
  return (
    <Table variant="striped" colorScheme="gray">
      <Thead>
        <Tr>
          <Th>Name</Th>
          <Th>Email</Th>
        </Tr>
      </Thead>
      <Tbody>
        <Tr>
          <Td>John Doe</Td>
          <Td>john@example.com</Td>
        </Tr>
        <Tr>
          <Td>Jane Smith</Td>
          <Td>jane@example.com</Td>
        </Tr>
      </Tbody>
    </Table>
  );
};

export default TableLayout;
```

In this code snippet, we import the necessary Chakra UI components for building tables (`Table`, `Thead`, `Tbody`, `Tr`, `Th`, and `Td`). We then structure our table by nesting these components within each other.


## Customizing the table layout

Chakra UI provides various props and styles to customize the table layout according to your needs. For example, you can add additional CSS classes, change the color scheme, or apply styling to specific table elements.

```jsx
<Table variant="striped" colorScheme="teal" size="md">
  <Thead>
    <Tr>
      <Th fontSize="lg">Name</Th>
      <Th>Email</Th>
    </Tr>
  </Thead>
  <Tbody>
    <Tr>
      <Td fontWeight="bold">John Doe</Td>
      <Td fontStyle="italic">john@example.com</Td>
    </Tr>
    {/* ... */}
  </Tbody>
</Table>
```

In this example, we added `size="md"` to set the table size to medium, `colorScheme="teal"` to use the teal color scheme, and applied specific styles to the `Th` and `Td` elements.

## Conclusion

Thanks to Chakra UI, building and styling table layouts in your React project has never been easier. With its intuitive set of components and customization options, you can create visually appealing and responsive tables in no time. So give it a try and streamline your table-building process!

#chakraui #react #webdevelopment