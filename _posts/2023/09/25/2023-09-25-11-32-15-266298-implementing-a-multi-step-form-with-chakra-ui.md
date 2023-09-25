---
layout: post
title: "Implementing a multi-step form with Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, react]
comments: true
share: true
---

Chakra UI is a popular React UI library that provides a set of customizable and accessible UI components. In this tutorial, we will explore how to create a multi-step form using Chakra UI.

## Step 1: Setting up the project

Before we start implementing the multi-step form, let's set up our React project with Chakra UI. Make sure you have Node.js and npm installed.

1. Create a new directory for your project and navigate into it:

```bash
mkdir multi-step-form
cd multi-step-form
```

2. Initialize a new React project:

```bash
npx create-react-app .
```

3. Install Chakra UI and its required dependencies:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

4. Start the development server:

```bash
npm start
```

## Step 2: Creating the form component

Now that our project is set up, let's create a new component for our multi-step form. Create a new file named `MultiStepForm.js` in the `src` folder.

```jsx
import React, { useState } from 'react';
import { Button, Container, Stack } from '@chakra-ui/react';

const MultiStepForm = () => {
  const [step, setStep] = useState(1);

  const handleNextStep = () => {
    setStep((prevStep) => prevStep + 1);
  };

  const handlePrevStep = () => {
    setStep((prevStep) => prevStep - 1);
  };

  const handleSubmit = () => {
    // Handle form submission logic
  };

  return (
    <Container maxWidth="md">
      <Stack spacing={6}>
        {/* Form steps */}
        {step === 1 && <Step1 />}
        {step === 2 && <Step2 />}
        {step === 3 && <Step3 />}

        {/* Navigation buttons */}
        {step !== 1 && (
          <Button onClick={handlePrevStep} colorScheme="gray">
            Previous
          </Button>
        )}
        {step !== 3 ? (
          <Button onClick={handleNextStep} colorScheme="teal">
            Next
          </Button>
        ) : (
          <Button onClick={handleSubmit} colorScheme="teal">
            Submit
          </Button>
        )}
      </Stack>
    </Container>
  );
};

export default MultiStepForm;
```

In this code snippet, we defined a `MultiStepForm` component that utilizes the `useState` hook to manage the current step of the form. The component renders different steps based on the current step state. The navigation buttons allow users to move between steps and submit the form at the last step.

## Step 3: Implementing form steps

Now that we have our form component, let's create the individual steps of our multi-step form. We will create three separate components: `Step1`, `Step2`, and `Step3`.

```jsx
// Step1.js
import React from 'react';
import { FormControl, FormLabel, Input } from '@chakra-ui/react';

const Step1 = () => {
  return (
    <FormControl>
      <FormLabel>Name</FormLabel>
      <Input placeholder="Enter your name" />
      {/* Add fields for other form inputs */}
    </FormControl>
  );
};

export default Step1;
```

```jsx
// Step2.js
import React from 'react';
import { FormControl, FormLabel, Input } from '@chakra-ui/react';

const Step2 = () => {
  return (
    <FormControl>
      <FormLabel>Email</FormLabel>
      <Input type="email" placeholder="Enter your email address" />
      {/* Add fields for other form inputs */}
    </FormControl>
  );
};

export default Step2;
```

```jsx
// Step3.js
import React from 'react';
import { FormControl, FormLabel, Input } from '@chakra-ui/react';

const Step3 = () => {
  return (
    <FormControl>
      <FormLabel>Message</FormLabel>
      <Input as="textarea" placeholder="Enter your message" />
      {/* Add fields for other form inputs */}
    </FormControl>
  );
};

export default Step3;
```

In each step component, we use Chakra UI's `FormControl`, `FormLabel`, and `Input` components to create form input fields.

## Step 4: Implementing form validation and submission logic

To validate and submit the form, you can add your logic to the `handleSubmit` function in the `MultiStepForm` component. You can use form libraries like Formik or React Hook Form for form validation.

## Conclusion

In this tutorial, we learned how to implement a multi-step form using Chakra UI. Chakra UI provides a convenient set of UI components that make it easy to create beautiful and accessible forms. Feel free to customize and extend the multi-step form according to your requirements. Happy coding!

#chakraui #react