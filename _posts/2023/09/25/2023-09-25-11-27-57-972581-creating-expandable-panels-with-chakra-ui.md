---
layout: post
title: "Creating expandable panels with Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraui]
comments: true
share: true
---

In this tutorial, we will learn how to create expandable panels using Chakra UI - a flexible and easy-to-use UI component library for React applications. Expandable panels are a great way to organize and display content within a collapsible container, allowing users to show or hide sections of information as needed.

## Getting started
First, let's make sure we have Chakra UI installed in our project. If you haven't done so already, you can install it by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once Chakra UI is installed, we can start building our expandable panels.

## Step 1: Set up basic structure
To begin, let's create a new file called `ExpandablePanel.js` and import the necessary components from Chakra UI:

```jsx
import { Box, Button } from "@chakra-ui/react";
import { ChevronDownIcon, ChevronUpIcon } from "@chakra-ui/icons";
import { useState } from "react";

const ExpandablePanel = ({ title, content }) => {
  const [isOpen, setIsOpen] = useState(false);

  const handleToggle = () => {
    setIsOpen(!isOpen);
  };

  return (
    <Box borderWidth="1px" borderRadius="md" overflow="hidden">
      <Button
        width="100%"
        onClick={handleToggle}
        justifyContent="flex-start"
        fontWeight="bold"
        px={4}
        py={2}
      >
        {isOpen ? (
          <>
            <ChevronUpIcon /> <span>{title}</span>
          </>
        ) : (
          <>
            <ChevronDownIcon /> <span>{title}</span>
          </>
        )}
      </Button>
      {isOpen && <Box px={4} py={2}>{content}</Box>}
    </Box>
  );
};

export default ExpandablePanel;
```

Now, we have a basic structure for our expandable panel component with a toggle button and the ability to show and hide the content.

## Step 2: Use the ExpandablePanel component
To use our newly created `ExpandablePanel` component, let's create a sample usage within a React component:

```jsx
import { Stack } from "@chakra-ui/react";
import ExpandablePanel from "./ExpandablePanel";

const App = () => {
  return (
    <Stack spacing={4}>
      <ExpandablePanel title="Panel 1" content="Content of panel 1" />
      <ExpandablePanel title="Panel 2" content="Content of panel 2" />
      <ExpandablePanel title="Panel 3" content="Content of panel 3" />
    </Stack>
  );
};

export default App;
```

Here, we have used the `ExpandablePanel` component by passing the title and content props. Each panel will have its own toggle button and content section.

## Step 3: Styling and customization
Chakra UI provides a wide range of styling options and customization for its components. You can further enhance the appearance and behavior of the expandable panels by exploring the Chakra UI documentation and applying different styles to suit your project's requirements.

## Conclusion
In this tutorial, we have learned how to create expandable panels using Chakra UI. Expandable panels enhance the user experience by providing the ability to collapse and expand sections of information. With Chakra UI's powerful and intuitive components, it becomes easier to create interactive and visually appealing expandable panels in your React applications.

#react #chakraui