---
layout: post
title: "Using the RadioGroup component in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraui]
comments: true
share: true
---

Radio buttons are a common form element used to allow users to select one option from a list. The RadioGroup component in Chakra UI provides an easy way to manage groups of radio buttons in React applications.

## Installation

Before we can use the RadioGroup component, we need to install Chakra UI in our project. You can install it via npm or yarn:

```bash
npm install @chakra-ui/react
```

or

```bash
yarn add @chakra-ui/react
```

## Usage

To use the RadioGroup component, we first import it from the `@chakra-ui/react` package:

```jsx
import { RadioGroup } from "@chakra-ui/react";
```

Next, we define the list of options for our radio buttons. We can create an array of objects, where each object represents an option:

```jsx
const options = [
  {
    value: "option1",
    label: "Option 1",
  },
  {
    value: "option2",
    label: "Option 2",
  },
  {
    value: "option3",
    label: "Option 3",
  },
];
```

Then, we render the RadioGroup component and pass in the options as children:

```jsx
<RadioGroup>
  {options.map((option) => (
    <Radio key={option.value} value={option.value}>
      {option.label}
    </Radio>
  ))}
</RadioGroup>
```

The `Radio` component is automatically provided by the RadioGroup component and represents each individual radio button. We use the `value` prop to assign a value to each option, and the `label` prop to display the label for each option.

## Handling the selected option

To handle the selected option, we can use the `onChange` event provided by the RadioGroup component. We can define a function that will be called whenever the selected option changes:

```jsx
function handleOptionChange(value) {
  console.log("Selected option:", value);
}
```

We pass this function as a prop to the RadioGroup component:

```jsx
<RadioGroup onChange={handleOptionChange}>
  {options.map((option) => (
    <Radio key={option.value} value={option.value}>
      {option.label}
    </Radio>
  ))}
</RadioGroup>
```

Now, whenever the user selects an option, the `handleOptionChange` function will be called with the value of the selected option.

## Styling

You can customize the appearance and styling of the RadioGroup component by using the `styleProps` provided by Chakra UI. You can add inline styles or use CSS-in-JS libraries like `emotion` or `styled-components` to define custom styles.

## Conclusion

Using the RadioGroup component in Chakra UI makes it easy to manage groups of radio buttons in your React applications. It provides a simple and intuitive API for creating and handling radio buttons, allowing you to focus on building great user experiences.

Give it a try in your project and make your forms more interactive and user-friendly!

#react #chakraui