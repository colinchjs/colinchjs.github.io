---
layout: post
title: "Building stepper forms with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

Stepper forms are a great way to guide users through a multi-step process, ensuring that they provide all the necessary information before proceeding to the next step. Chakra UI, a popular React component library, makes it easy to implement stepper forms with its flexible and customizable components.

In this tutorial, we will walk through the process of building a stepper form using Chakra UI. We'll assume some familiarity with React and Chakra UI, so make sure you have those dependencies installed before getting started.

## Setting up the project

1. Start by creating a new React project using Create React App:

   ```shell
   npx create-react-app my-stepper-form
   ```

2. Install Chakra UI and its required dependencies:

   ```shell
   npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
   ```

3. Import the necessary Chakra UI components in your main `App.js` file:

   ```jsx
   import { ChakraProvider } from "@chakra-ui/react";
   ```

## Creating the stepper component

Next, let's create a new component called `Stepper` that will handle the logic for our stepper form.

1. In the `src` folder, create a new file called `Stepper.js` and add the following code:

   ```jsx
   import React, { useState } from "react";
   import { Box, Button, Text } from "@chakra-ui/react";

   const Stepper = () => {
     const [step, setStep] = useState(1);

     const handleNextStep = () => {
       setStep((prevStep) => prevStep + 1);
     };

     const handlePreviousStep = () => {
       setStep((prevStep) => prevStep - 1);
     };

     return (
       <Box>
         {step === 1 && <Text>Step 1 - Enter Basic Information</Text>}
         {step === 2 && <Text>Step 2 - Add Additional Details</Text>}
         {step === 3 && <Text>Step 3 - Review and Submit</Text>}

         <Button
           onClick={handleNextStep}
           disabled={step === 3}
           mt={4}
           ml={2}
         >
           Next
         </Button>

         <Button
           onClick={handlePreviousStep}
           disabled={step === 1}
           mt={4}
           ml={2}
         >
           Previous
         </Button>
       </Box>
     );
   };

   export default Stepper;
   ```

   This component handles the state of the current step and provides buttons to navigate between steps.

2. In your `App.js` file, import and render the `Stepper` component:

   ```jsx
   import React from "react";
   import { ChakraProvider } from "@chakra-ui/react";
   import Stepper from "./Stepper";

   const App = () => {
     return (
       <ChakraProvider>
         <Stepper />
       </ChakraProvider>
     );
   };

   export default App;
   ```

   Save the file and start the development server:

   ```shell
   npm start
   ```

   You should see the initial step displayed, with "Next" and "Previous" buttons. Clicking the buttons should switch between steps accordingly.

## Styling the stepper

With Chakra UI, styling the stepper is a breeze using its comprehensive set of utility classes and component props.

1. Update the `Stepper` component to display the steps as a dot indicator:

   ```jsx
   const Stepper = () => {
     // ...

     return (
       <Box>
         <Box
           display="flex"
           justifyContent="center"
           mt={8}
           mb={4}
           spacing={4}
         >
           <Box
             w={6}
             h={6}
             borderRadius="full"
             bg={step >= 1 ? "blue.500" : "gray.300"}
           />
           <Box
             w={6}
             h={6}
             borderRadius="full"
             bg={step >= 2 ? "blue.500" : "gray.300"}
           />
           <Box
             w={6}
             h={6}
             borderRadius="full"
             bg={step >= 3 ? "blue.500" : "gray.300"}
           />
         </Box>

         {/* ... */}
       </Box>
     );
   };
   ```

   This code adds a dot indicator for each step, where a filled blue dot indicates the current step, and a gray dot indicates the remaining steps.

2. Add some spacing and styling to the buttons:

   ```jsx
   return (
     <Box>
       {/* ... */}

       <Button
         onClick={handleNextStep}
         disabled={step === 3}
         mt={4}
         ml={2}
         colorScheme="blue"
       >
         Next
       </Button>

       <Button
         onClick={handlePreviousStep}
         disabled={step === 1}
         mt={4}
         ml={2}
         colorScheme="gray"
         variant="outline"
       >
         Previous
       </Button>
     </Box>
   );
   ```

   The buttons are now styled according to the Chakra UI color scheme.

## Conclusion

With Chakra UI, building stepper forms becomes a straightforward task. Its customizable components and utility classes make it easy to create a user-friendly and visually appealing multi-step form experience. Give it a try in your next project and see how Chakra UI can simplify your development process.

#ChakraUI #React