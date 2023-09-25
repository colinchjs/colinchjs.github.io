---
layout: post
title: "Using the Tabs component in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

Chakra UI is a popular React component library that provides ready-to-use UI components for building modern web applications. One of the essential components it offers is the Tabs component, which allows you to create tabbed navigation effortlessly. In this article, we will explore how to use the Tabs component in Chakra UI to create an interactive tabbed interface.

## Installation

Before we jump into using the Tabs component, let's make sure we have Chakra UI installed in our project. You can install Chakra UI by running the following command in your terminal:

```
npm install @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4
```
or
```
yarn add @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4
```

## Usage

Once you have Chakra UI installed, you can start using the Tabs component in your React application. Follow these steps to use the Tabs component effectively:

1. Import the necessary components from Chakra UI:

```javascript
import { Tabs, TabList, TabPanels, Tab, TabPanel } from "@chakra-ui/react";
```

2. Wrap your tabbed content with the `Tabs` component:

```javascript
<Tabs>
  {/* Tab List */}
  <TabList>
    <Tab>Tab 1</Tab>
    <Tab>Tab 2</Tab>
    <Tab>Tab 3</Tab>
  </TabList>

  {/* Tab Panels */}
  <TabPanels>
    <TabPanel>
      {/* Content of Tab 1 */}
    </TabPanel>
    <TabPanel>
      {/* Content of Tab 2 */}
    </TabPanel>
    <TabPanel>
      {/* Content of Tab 3 */}
    </TabPanel>
  </TabPanels>
</Tabs>
```

3. Customize the appearance of the Tabs component using Chakra UI's theming and component props. For example, you can change the background color of the active tab:

```javascript
<Tabs>
  {/* Tab List */}
  <TabList bg="teal.500">
    {/*...*/}
  </TabList>

  {/* Tab Panels */}
  <TabPanels>
    {/*...*/}
  </TabPanels>
</Tabs>
```

## Conclusion

The Tabs component in Chakra UI makes it easy to create tabbed navigation in your React application. Its simplicity and flexibility allow you to build interactive interfaces without much effort. By following the steps outlined in this article, you can start using the Tabs component in your project and enhance the user experience.

#ChakraUI #React