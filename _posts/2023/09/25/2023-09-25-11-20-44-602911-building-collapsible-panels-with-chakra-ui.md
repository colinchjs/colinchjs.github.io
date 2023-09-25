---
layout: post
title: "Building collapsible panels with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

In this tutorial, we will learn how to create collapsible panels using Chakra UI, a popular React component library. Collapsible panels can be useful for creating accordion menus, collapsible sections, or collapsible content panels in a web application.

## Prerequisites

To follow along with this tutorial, you should have a basic understanding of React and have Chakra UI installed in your project. If you haven't installed Chakra UI yet, you can do so by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating the Collapsible Panel Component

First, let's create a new React component called `CollapsiblePanel` that will be responsible for rendering the collapsible panel. Here's an example code snippet to get started:

```jsx
import { useState } from "react";
import { Box, Button } from "@chakra-ui/react";

function CollapsiblePanel({ title, children }) {
  const [isOpen, setIsOpen] = useState(false);

  const handleToggle = () => {
    setIsOpen(!isOpen);
  };

  return (
    <Box borderWidth="1px" borderRadius="md" p="4">
      <Button onClick={handleToggle}>
        {title} {isOpen ? "-" : "+"}
      </Button>
      {isOpen && (
        <Box mt="2" pl="4">
          {children}
        </Box>
      )}
    </Box>
  );
}

export default CollapsiblePanel;
```

In the above code, we import the necessary components from Chakra UI (`Box` and `Button`) and use the `useState` hook to manage the open/closed state of the panel. The `handleToggle` function toggles the value of `isOpen` when the button is clicked. The panel's title is displayed with a toggle button that shows a "+" or "-" sign based on the state. When the panel is open, the children components passed to `CollapsiblePanel` are rendered.

## Using the CollapsiblePanel Component

Now that we have created the `CollapsiblePanel` component, let's use it in our application. We can pass any content we want to appear inside the collapsible panel as children.

```jsx
import CollapsiblePanel from "./CollapsiblePanel";

function App() {
  return (
    <div>
      <CollapsiblePanel title="Panel 1">
        <p>This is the content of panel 1.</p>
      </CollapsiblePanel>

      <CollapsiblePanel title="Panel 2">
        <p>This is the content of panel 2.</p>
      </CollapsiblePanel>

      <CollapsiblePanel title="Panel 3">
        <p>This is the content of panel 3.</p>
      </CollapsiblePanel>
    </div>
  );
}

export default App;
```

In the above example, we render three collapsible panels with different titles and content. The panels can be collapsed or expanded by clicking on their respective toggle buttons.

## Conclusion

In this tutorial, we have learned how to create collapsible panels using Chakra UI. The `CollapsiblePanel` component allows us to easily create collapsible sections or content panels in our React applications. Feel free to customize the component further to fit your specific needs and styles.

#React #ChakraUI