---
layout: post
title: "Creating accordions in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

Accordions are a common UI element used to display collapsible content in a structured manner. They are widely used in websites and applications to provide an organized and compact way of presenting large amounts of information.

In this tutorial, we will explore how to create accordions using Chakra UI, a popular React component library that provides a set of customizable and accessible UI components.

## Getting Started

Let's start by creating a new React project and installing the necessary dependencies. Open your terminal and run the following commands:

```bash
npx create-react-app chakra-accordion
cd chakra-accordion
```

Once the project is created, install Chakra UI by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating the Accordion Component

In Chakra UI, accordions can be easily created using the `Collapse` and `Accordion` components. Create a new file called `Accordion.js` inside the `src` folder and add the following code:

```jsx
import { Box, Accordion, AccordionItem, AccordionButton, AccordionPanel, AccordionIcon } from "@chakra-ui/react";

const AccordionComponent = () => {
    return (
        <Accordion defaultIndex={[0]} allowMultiple>
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
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed ac dui tellus.
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
                    Proin blandit odio at dictum consequat. Sed maximus tempus enim id cursus.
                </AccordionPanel>
            </AccordionItem>
        </Accordion>
    );
};

export default AccordionComponent;
```

In the above code, we import the required components from Chakra UI and define the `AccordionComponent` function. Inside this function, we use the `Accordion`, `AccordionItem`, `AccordionButton`, `AccordionPanel`, and `AccordionIcon` components to create the accordion structure.

Each `AccordionItem` represents a section in the accordion, and the content of each section is defined within the `AccordionPanel`. The `AccordionButton` is used to trigger the collapse and expand behavior of the sections, and the `AccordionIcon` displays an arrow that indicates the expand or collapse state.

## Using the Accordion Component

To use the `AccordionComponent`, open the `src/App.js` file and replace its contents with the following code:

```jsx
import AccordionComponent from "./Accordion";

function App() {
  return (
    <div className="App">
      <AccordionComponent />
    </div>
  );
}

export default App;
```

Save the file and start the development server by running the command `npm start`. You should now see the accordion with two sections labeled "Section 1" and "Section 2". Clicking on the section headers will expand or collapse the corresponding section content.

## Customizing the Accordion

Chakra UI provides a wide range of customization options for the accordion components. You can change the colors, sizes, icons, and other styles to match your application's design. Refer to the [Chakra UI documentation](https://chakra-ui.com/docs/component/accordion) for more details on how to customize accordions.

## Conclusion

In this tutorial, we have learned how to create accordions using Chakra UI. Accordions are a handy UI component for organizing and displaying content in a collapsible manner. With Chakra UI, creating and customizing accordions becomes straightforward, thanks to its rich set of accessible components.

#ChakraUI #React