---
layout: post
title: "Adding icons to Chakra UI components"
description: " "
date: 2023-09-25
tags: [ChakraUI, Icons]
comments: true
share: true
---

Chakra UI is a popular library for building user interfaces with React. One of its key features is the ability to easily integrate icons into your UI components. In this tutorial, we will explore how to add icons to Chakra UI components using the `@chakra-ui/icons` package.

## Prerequisites

Before we begin, make sure you have already set up a Chakra UI project. If you haven't, you can follow the official documentation to install Chakra UI in your React project.

## Installing @chakra-ui/icons

To use icons with Chakra UI, we need to install the `@chakra-ui/icons` package. Open your terminal and run the following command:

```shell
npm install @chakra-ui/icons
```

## Importing Icons

To import icons, we need to use the `Icon` component from `@chakra-ui/icons`. You can import individual icons or import the entire icon library. 

For example, to import the `ChevronRightIcon`:

```javascript
import { ChevronRightIcon } from '@chakra-ui/icons';
```

To import the entire icon library:

```javascript
import * as Icons from '@chakra-ui/icons';
```

## Using Icons in Chakra UI Components

Once you have imported the icons, you can use them in your Chakra UI components. The `Icon` component can be placed inside any Chakra UI component and accepts various props.

Here's an example of adding an icon to a button component:

```javascript
import { Button } from '@chakra-ui/react';
import { ChevronRightIcon } from '@chakra-ui/icons'; 

const MyButton = () => {
  return (
    <Button
      colorScheme="teal"
      rightIcon={<ChevronRightIcon />}
    >
      See More
    </Button>
  );
};
```

In this example, we imported the `Button` component from `@chakra-ui/react` and the `ChevronRightIcon` from `@chakra-ui/icons`. We then added the `ChevronRightIcon` as the `rightIcon` prop of the `Button` component.

## Conclusion

Adding icons to your Chakra UI components is made easy with the `@chakra-ui/icons` package. By importing and placing the `Icon` component within any Chakra UI component, you can enhance your UI with visually appealing icons. Start exploring the available icons and see how they can improve the user experience of your Chakra UI application.

## #ChakraUI #Icons