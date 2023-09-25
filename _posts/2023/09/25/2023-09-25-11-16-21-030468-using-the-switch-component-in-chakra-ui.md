---
layout: post
title: "Using the Switch component in Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

One of the most commonly used components in web development is a switch, which allows users to toggle between two states. In Chakra UI, a popular React component library, you can easily implement a switch using the `Switch` component.

## Installation

Before we can start using the `Switch` component, we need to install Chakra UI and its dependencies. You can do this by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```
Make sure you have npm installed on your machine to run this command. 

## Usage

Once you have Chakra UI installed in your React project, you can import the `Switch` component and use it in your code. Here's an example:

```jsx
import { Switch } from '@chakra-ui/react';

function App() {
  const [isChecked, setIsChecked] = React.useState(false);

  const handleChange = () => {
    setIsChecked(!isChecked);
  };

  return (
    <div>
      <Switch isChecked={isChecked} onChange={handleChange} colorScheme="teal" size="lg" />
    </div>
  );
}
```

In this example, we first import the `Switch` component from Chakra UI. We then create a state variable `isChecked` using the `useState` hook to keep track of the switch's state.

Next, we define a `handleChange` function that toggles the value of `isChecked` whenever the switch is clicked. This function is passed as the `onChange` prop to the `Switch` component.

Finally, we render the `Switch` component, passing the `isChecked` state and the `handleChange` function as props. We also set the `colorScheme` to "teal" and the size to "lg" for visual customization.

## Customization

Chakra UI provides a wide range of prop options for customizing the appearance of the `Switch` component. You can refer to the Chakra UI documentation for a complete list of available props and their descriptions.

## Conclusion

The `Switch` component in Chakra UI offers a simple and user-friendly way to implement a switch in your React applications. Its versatility and customization options make it a powerful tool for building intuitive user interfaces.

#React #ChakraUI