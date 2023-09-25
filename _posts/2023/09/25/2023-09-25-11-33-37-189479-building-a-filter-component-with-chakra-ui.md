---
layout: post
title: "Building a filter component with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ReactUI]
comments: true
share: true
---

In this tutorial, we will learn how to build a filter component using the Chakra UI library. The filter component will allow users to narrow down a list of items based on certain criteria. We will utilize the power and flexibility of Chakra UI to create a visually appealing and interactive filter experience.

## Prerequisites
- Basic understanding of React
- Familiarity with Chakra UI

## Setting up the Project
To begin, let's create a new React project and install Chakra UI.

```shell
npx create-react-app filter-component
cd filter-component
npm install @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4
```

Next, open the project in your favorite code editor.

## Creating the Filter Component
In the `src` directory, create a new folder called `components`. Inside the `components` folder, create a new file called `Filter.js`. 

First, import the necessary dependencies from Chakra UI and React.

```javascript
import { Box, Checkbox, Stack, Text } from '@chakra-ui/react';
import { useState } from 'react';
```

Next, create the `Filter` component.

```javascript
const Filter = () => {
  const [filterOptions, setFilterOptions] = useState([]);

  const handleCheckboxChange = (event) => {
    const optionName = event.target.name;
    const isChecked = event.target.checked;

    if (isChecked) {
      setFilterOptions([...filterOptions, optionName]);
    } else {
      setFilterOptions(filterOptions.filter((option) => option !== optionName));
    }
  };

  return (
    <Box>
      <Text fontWeight="bold">Filters</Text>
      <Stack spacing={2} mt={2}>
        <Checkbox name="option1" onChange={handleCheckboxChange}>Option 1</Checkbox>
        <Checkbox name="option2" onChange={handleCheckboxChange}>Option 2</Checkbox>
        <Checkbox name="option3" onChange={handleCheckboxChange}>Option 3</Checkbox>
      </Stack>
    </Box>
  );
};

export default Filter;
```

In the `Filter` component, we are using the `useState` hook to keep track of the selected filter options. The `handleCheckboxChange` function handles the checkbox change event and updates the `filterOptions` state accordingly.

The component renders a `Box` from Chakra UI and displays the filter options as checkboxes inside a `Stack`. Whenever a checkbox is checked or unchecked, the corresponding `handleCheckboxChange` function is called.

## Implementing the Filter Component
Now that we have created the `Filter` component, let's use in our main `App` component.

In the `App.js` file, import the `Filter` component.

```javascript
import Filter from './components/Filter';
```

Next, add the `Filter` component to the `App` component.

```javascript
const App = () => {
  return (
    <div>
      <Filter />
      {/* Rest of your application */}
    </div>
  );
};

export default App;
```

## Conclusion
In this tutorial, we have learned how to create a filter component using Chakra UI. We explored how to handle checkbox change events and update the filter options. With Chakra UI, it's easy to create visually appealing filter components to enhance the user experience of your application.

Remember to **#ChakraUI** and **#ReactUI** in your social media posts when sharing your filter component implementation. Happy coding!