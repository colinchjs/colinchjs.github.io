---
layout: post
title: "Creating a stepper component with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

In this tutorial, we will learn how to create a stepper component using Chakra UI, which is a popular UI library for React applications. This stepper component will allow users to navigate through multiple steps and keep track of the current step. Let's get started!

## Setting up the Project
Before we begin, make sure you have [Chakra UI](https://chakra-ui.com/) installed in your project. You can install it by running the following command:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating the Stepper Component
First, let's import the necessary components from Chakra UI:

```jsx
import { Box, Text, Button } from '@chakra-ui/react';
```

Next, we need to define our stepper component:

```jsx
const Stepper = ({ steps, currentStep, onNext, onPrev }) => {
  // Render the step text and buttons
  return (
    <Box>
      <Text fontSize="xl" fontWeight="bold" mb={4}>
        Step {currentStep + 1} of {steps.length}:
      </Text>
      <Text mb={4}>{steps[currentStep]}</Text>
      <Box>
        <Button
          mr={4}
          variant="outline"
          disabled={currentStep === 0}
          onClick={onPrev}
        >
          Previous
        </Button>
        <Button onClick={onNext}>
          Next
        </Button>
      </Box>
    </Box>
  );
};
```

In the `Stepper` component, we receive the following props:
- `steps`: an array containing the text for each step
- `currentStep`: an integer representing the current step index
- `onNext`: a function to handle the next step button click
- `onPrev`: a function to handle the previous step button click

The main part of the component is the `return` statement, where we render the step text and buttons. We use the Chakra UI `Box`, `Text`, and `Button` components for the layout and styling.

The "Previous" button is disabled when the current step is the first step. The "Next" button triggers the `onNext` function when clicked.

## Integrating the Stepper Component
Now, let's integrate the stepper component into our app. Here's an example of how you can use the `Stepper` component:

```jsx
import { useState } from 'react';
import { ChakraProvider } from '@chakra-ui/react';

const App = () => {
  const steps = ['Step 1', 'Step 2', 'Step 3'];
  const [currentStep, setCurrentStep] = useState(0);

  const handleNext = () => {
    if (currentStep < steps.length - 1) {
      setCurrentStep(currentStep + 1);
    }
  };

  const handlePrev = () => {
    if (currentStep > 0) {
      setCurrentStep(currentStep - 1);
    }
  };

  return (
    <ChakraProvider>
      <Stepper
        steps={steps}
        currentStep={currentStep}
        onNext={handleNext}
        onPrev={handlePrev}
      />
    </ChakraProvider>
  );
};
```

In this example, we use the `useState` hook to manage the current step state. We also define two functions - `handleNext` and `handlePrev` - to handle the next and previous button clicks, respectively.

## Conclusion
By following this tutorial, you have learned how to create a stepper component using Chakra UI. This component allows users to navigate through multiple steps and keeps track of the current step. You can customize the styling and add more functionality to the component based on your specific requirements.

#React #ChakraUI