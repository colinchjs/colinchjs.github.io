---
layout: post
title: "Creating a data table with Chakra UI"
description: " "
date: 2023-09-25
tags: [webdevelopment, chakraui]
comments: true
share: true
---

In this tutorial, we will show you how to create a data table using Chakra UI, a popular React component library. Data tables are commonly used for displaying tabular data in an organized manner. Chakra UI provides a set of powerful components that make it easy to create visually appealing and interactive data tables.

## Installing Chakra UI

Before we start, make sure you have Chakra UI installed in your React project. You can install Chakra UI by running the following command:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating the Data Table Component

First, let's create a new component called `DataTable.js`. Inside this file, import the necessary Chakra UI components:

```javascript
import { Table, Thead, Tbody, Tr, Th, Td } from '@chakra-ui/react';
```

Next, define the `DataTable` component:

```javascript
const DataTable = ({ data }) => {
  return (
    <Table variant="simple">
      <Thead>
        <Tr>
          <Th>Column 1</Th>
          <Th>Column 2</Th>
          <Th>Column 3</Th>
        </Tr>
      </Thead>
      <Tbody>
        {data.map((row) => (
          <Tr key={row.id}>
            <Td>{row.column1}</Td>
            <Td>{row.column2}</Td>
            <Td>{row.column3}</Td>
          </Tr>
        ))}
      </Tbody>
    </Table>
  );
};

export default DataTable;
```

In this example, the `DataTable` component accepts a prop `data`, which is an array of objects representing the rows in the table. Each row object should have properties `column1`, `column2`, and `column3`, representing the values for each column.

Inside the component, we use Chakra UI's `Table`, `Thead`, `Tbody`, `Tr`, `Th`, and `Td` components to structure the table and populate it with data. We map over the `data` array and render a row for each object in the array.

## Using the Data Table Component

To use the `DataTable` component, import it into your desired file and pass the `data` prop:

```javascript
import DataTable from './DataTable';

const MyPage = () => {
  const data = [
    { id: 1, column1: 'Value 1', column2: 'Value 2', column3: 'Value 3' },
    { id: 2, column1: 'Value 4', column2: 'Value 5', column3: 'Value 6' },
    // Add more rows as needed
  ];

  return (
    <div>
      <h1>My Data Table</h1>
      <DataTable data={data} />
    </div>
  );
};
```

In this example, we create a simple page component called `MyPage` and pass the `data` prop to the `DataTable` component. You can customize the data as per your requirements.

## Conclusion

In this tutorial, we have learned how to create a data table using Chakra UI. Chakra UI provides a convenient set of components for building data tables with ease. Feel free to explore the Chakra UI documentation for more styling and customization options.

#webdevelopment #chakraui