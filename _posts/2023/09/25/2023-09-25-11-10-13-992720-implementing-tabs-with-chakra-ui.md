---
layout: post
title: "Implementing tabs with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

In this blog post, we will explore how to implement tabs using Chakra UI, a popular UI library for React applications. Tabs are a common UI component used to display multiple sections of content in a compact and organized manner.

## Getting Started

Before we begin, make sure you have a basic understanding of React and have a React project set up with Chakra UI installed. You can install Chakra UI by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating the Tab Component

To get started with implementing tabs, we first need to create a component to render the tabs and handle the state. Let's create a `Tabs` component:

```jsx
import { useState } from 'react';
import { Tab, TabList, TabPanel, TabPanels } from "@chakra-ui/react";

const Tabs = ({ defaultTab, tabs }) => {
  const [selectedTab, setSelectedTab] = useState(defaultTab);

  return (
    <Tab>
      <TabList>
        {tabs.map((tab, index) => (
          <Tab
            key={index}
            onClick={() => setSelectedTab(index)}
            isSelected={selectedTab === index}
          >
            {tab.title}
          </Tab>
        ))}
      </TabList>

      <TabPanels>
        {tabs.map((tab, index) => (
          <TabPanel
            key={index}
            display={selectedTab === index ? "block" : "none"}
          >
            {tab.content}
          </TabPanel>
        ))}
      </TabPanels>
    </Tab>
  );
};

export default Tabs;
```

In this component, we are using the `Tab`, `TabList`, `TabPanel`, and `TabPanels` components from Chakra UI to create the tabbed interface. We are also using the `useState` hook to manage the selected tab state.

## Using the Tabs Component

Now that we have our `Tabs` component, we can use it to create tabbed content. Here's an example of how to use it:

```jsx
import { ChakraProvider, Stack } from "@chakra-ui/react";
import Tabs from "./Tabs";

const App = () => {
  const tabs = [
    {
      title: "Tab 1",
      content: "Content for Tab 1",
    },
    {
      title: "Tab 2",
      content: "Content for Tab 2",
    },
    {
      title: "Tab 3",
      content: "Content for Tab 3",
    },
  ];

  return (
    <ChakraProvider>
      <Stack spacing={4}>
        <Tabs defaultTab={0} tabs={tabs} />
      </Stack>
    </ChakraProvider>
  );
};

export default App;
```

In this example, we have an array of tabs with their corresponding titles and contents. We pass this array as props to the `Tabs` component, along with the `defaultTab` index to specify which tab should be selected by default.

## Customizing the Styles

Chakra UI provides a set of default styles for the Tab components. You can customize these styles using the `theme` object from Chakra UI or by using the `CSS` prop on individual components.

For example, to change the background color of the selected tab, you can do:

```jsx
<Tab isSelected={selectedTab === index} _selected={{ bg: "blue.500", color: "white" }}>
  {tab.title}
</Tab>
```

This will set the background color to blue when the tab is selected.

## Conclusion

In this blog post, we've learned how to implement tabs using Chakra UI in a React application. We've created a `Tabs` component that handles the tab state and renders the tabbed interface. We've also seen how to customize the styles of the tabs. Tabs are a great way to organize and present content in an intuitive and user-friendly manner, and Chakra UI makes it easy to implement them in React applications.

#React #ChakraUI