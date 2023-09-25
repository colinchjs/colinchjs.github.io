---
layout: post
title: "Using the Collapse component in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

Chakra UI is a popular React component library that provides a set of accessible and customizable UI components. One of the useful components in Chakra UI is the `Collapse` component, which allows you to create collapsible sections or accordions in your application.

## Installation

To use the `Collapse` component, you need to have Chakra UI installed in your project. You can install it via npm or yarn:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```bash
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Basic Usage

Once you have Chakra UI installed, you can start using the `Collapse` component in your React components. Here's a simple example:

```jsx
import { Collapse } from "@chakra-ui/react";
import { ChevronDownIcon } from "@chakra-ui/icons";

function MyComponent() {
  const [isOpen, setIsOpen] = useState(false);

  return (
    <div>
      <button onClick={() => setIsOpen(!isOpen)}>
        <ChevronDownIcon />
      </button>
      <Collapse in={isOpen}>
        <div>
          // Content that will be collapsed
        </div>
      </Collapse>
    </div>
  );
}
```

In the example above, we first import the `Collapse` component from Chakra UI. We also import the `ChevronDownIcon` from Chakra UI's icon library. Inside the `MyComponent` component, we initialize a state variable `isOpen` to keep track of the collapse state. When the button is clicked, we toggle the value of `isOpen`. The `Collapse` component takes a prop called `in` which determines whether the content inside it should be visible or collapsed.

## Additional Customizations

The `Collapse` component in Chakra UI provides additional customization options. Here are a few examples:

- `animateOpacity`: Allows you to control the opacity transition when the content collapses or expands. Set it to `true` to enable animation.
- `duration`: Sets the duration of the collapse animation. The default value is `200ms`.
- `startCollapsed`: If set to `true`, the content will initially be collapsed.
- `style`: Allows you to add custom styles to the collapsed content.

```jsx
<Collapse in={isOpen} animateOpacity duration={500} startCollapsed style={{ border: "1px solid black" }}>
  <div>
    // Customized collapsed content
  </div>
</Collapse>
```

## Conclusion

The `Collapse` component in Chakra UI is a versatile component that adds collapsible sections to your React application with ease. With its customization options, you can create dynamic and interactive UI elements. Start exploring the possibilities of Chakra UI and enhance the user experience of your application.

#ChakraUI #React