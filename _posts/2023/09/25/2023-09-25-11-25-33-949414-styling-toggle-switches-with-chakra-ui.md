---
layout: post
title: "Styling toggle switches with Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraui]
comments: true
share: true
---

Toggle switches are a common UI element used to enable or disable a certain setting or feature in an application. When styling toggle switches, it's important to ensure that they are clear and intuitive for users to interact with.

In this tutorial, we'll explore how to style toggle switches using Chakra UI, a popular UI component library for React applications.

## Setting up Chakra UI

Before we begin, make sure you have Chakra UI installed and set up in your React project. You can follow the official documentation for installation instructions.

## Creating the Toggle Switch

To create a toggle switch with Chakra UI, we can use the `Switch` component provided by the library. Here's an example of how to use it:

```jsx
import { Switch } from "@chakra-ui/react";

const ToggleSwitch = () => {
  const [isChecked, setIsChecked] = useState(false);

  const handleToggle = () => {
    setIsChecked(!isChecked);
  };

  return (
    <Switch
      size="lg"
      onChange={handleToggle}
      isChecked={isChecked}
      colorScheme="teal"
    />
  );
};

export default ToggleSwitch;
```

In the above code, we import the `Switch` component from Chakra UI and use it in our `ToggleSwitch` component. We also use the `useState` hook to manage the state of the switch.

The `size` prop configures the size of the toggle switch, while the `colorScheme` prop sets the color theme for the switch. The `isChecked` prop determines whether the switch is initially on or off.

When the switch is toggled, we update the state using the `handleToggle` function. This toggles the `isChecked` state between `true` and `false`.

## Customizing the Toggle Switch

Chakra UI provides a range of props to customize the appearance of the toggle switch according to your design needs. Here are a few examples:

```jsx
<Switch
  size="md"
  colorScheme="blue"
  isDisabled={true}
  defaultIsChecked={true}
  id="my-switch"
/>
```

In the above code, we've adjusted the `size` prop to "md", the `colorScheme` prop to "blue", and added the `isDisabled` prop to make the switch unclickable. We've also set the `defaultIsChecked` prop to `true` to make the switch initially on.

## Conclusion

Styling toggle switches using Chakra UI is a straightforward process with its `Switch` component. By leveraging the various prop options provided by Chakra UI, you can easily customize the appearance and behavior of the toggle switch to match your application's design.

With Chakra UI's extensive documentation and flexible component library, you have all the tools at your disposal to create beautiful and user-friendly toggle switches for your React projects.

#react #chakraui