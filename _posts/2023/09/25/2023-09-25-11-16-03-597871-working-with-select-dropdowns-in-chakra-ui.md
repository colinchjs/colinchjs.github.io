---
layout: post
title: "Working with select dropdowns in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ReactUI]
comments: true
share: true
---

Chakra UI is a popular UI library for React that provides a set of accessible and customizable components out of the box. One of the commonly used components in many web applications is the select dropdown. In this blog post, we will explore how to work with select dropdowns in Chakra UI and some of its features.

## Installation

Before we begin, make sure you have Chakra UI installed in your React project:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating a basic select dropdown

To create a select dropdown in Chakra UI, you can use the `Select` component. Here's an example of a basic select dropdown with different options:

```jsx
import { Select } from "@chakra-ui/react";

function SelectDropdown() {
  return (
    <Select>
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
      <option value="option3">Option 3</option>
    </Select>
  );
}
```

By default, the `Select` component renders a styled dropdown with options. You can pass the desired options as children to the `Select` component using `option` tags. The `value` attribute specifies the value associated with each option.

## Styling the select dropdown

Chakra UI provides various ways to customize the appearance and style of the select dropdown. You can use the `variant` prop to apply different styles. Here's an example:

```jsx
import { Select } from "@chakra-ui/react";

function SelectDropdown() {
  return (
    <Select variant="outline" borderColor="blue.500" borderRadius="md">
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
      <option value="option3">Option 3</option>
    </Select>
  );
}
```

In this example, we have applied the `outline` variant to the select dropdown and set the border color to `blue.500` with a `md` border radius.

## Handling select events

To handle events like option selection or value change, you can use the `onChange` prop with a callback function. Here's an example:

```jsx
import { Select } from "@chakra-ui/react";
import { useState } from "react";

function SelectDropdown() {
  const [selectedOption, setSelectedOption] = useState("");
  
  const handleOptionChange = (event) => {
    setSelectedOption(event.target.value);
    // additional logic here
  };
  
  return (
    <Select value={selectedOption} onChange={handleOptionChange}>
      <option value="option1">Option 1</option>
      <option value="option2">Option 2</option>
      <option value="option3">Option 3</option>
    </Select>
  );
}
```

In this example, we are using the `useState` hook to store the selected option in the component's state. The `handleOptionChange` function is invoked whenever the select option is changed, and it updates the `selectedOption` state value accordingly.

## Conclusion

Select dropdowns are essential components in many web applications, and Chakra UI provides an easy and customizable way to work with them in React. In this blog post, we explored the basics of working with select dropdowns in Chakra UI, including creating a basic select dropdown, styling it, and handling select events.

#ChakraUI #ReactUI