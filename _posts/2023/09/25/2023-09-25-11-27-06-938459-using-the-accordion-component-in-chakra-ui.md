---
layout: post
title: "Using the Accordion component in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

In this blog post, we will explore how to use the Accordion component in Chakra UI to create collapsible sections in your web application.

## What is the Accordion Component?

The Accordion component allows you to group related content into collapsible sections. Each section consists of a title and a content area that can be expanded or collapsed with a click. This is a great way to organize and present information in a clean and user-friendly manner.

## Installation

To use the Accordion component in your React project, you need to install the Chakra UI library first. You can do this by running the following command:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Getting Started

Once Chakra UI is installed, you can start using the Accordion component. First, you need to import the required components from Chakra UI:

```jsx
import { Accordion, AccordionItem, AccordionButton, AccordionPanel, AccordionIcon } from "@chakra-ui/react";
```

## Example Usage

Now, let's see how to use the Accordion component in a simple example:

```jsx
<Accordion allowToggle>
  <AccordionItem>
    <h2>
      <AccordionButton>
        <Box flex="1" textAlign="left">
          Section 1
        </Box>
        <AccordionIcon />
      </AccordionButton>
    </h2>
    <AccordionPanel pb={4}>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed eu feugiat mi.
    </AccordionPanel>
  </AccordionItem>
  <AccordionItem>
    <h2>
      <AccordionButton>
        <Box flex="1" textAlign="left">
          Section 2
        </Box>
        <AccordionIcon />
      </AccordionButton>
    </h2>
    <AccordionPanel pb={4}>
      Ut pretium turpis quis lectus tristique, a dictum dolor iaculis.
    </AccordionPanel>
  </AccordionItem>
</Accordion>
```

In this example, we have created two accordion sections. Each section is wrapped in an `AccordionItem` component and has a title defined within the `AccordionButton` component. The content of each section is wrapped in an `AccordionPanel` component.

The `allowToggle` prop on the `Accordion` component allows multiple sections to be expanded simultaneously. If you want to allow only one section to be expanded at a time, remove this prop.

## Customization

Chakra UI provides various props to customize the appearance of the Accordion component. You can customize the styling of the sections, icons, and other elements according to your needs. Refer to the [Chakra UI documentation](https://chakra-ui.com/docs/data-display/accordion) for more details.

## Conclusion

The Accordion component in Chakra UI simplifies the process of creating collapsible sections in your web application. It allows you to organize and present information in an intuitive and user-friendly manner. By using Chakra UI's styling capabilities, you can customize the appearance of the accordion to fit your project's design.

#ChakraUI #React