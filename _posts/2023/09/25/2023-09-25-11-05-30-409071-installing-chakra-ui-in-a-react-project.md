---
layout: post
title: "Installing Chakra UI in a React project"
description: " "
date: 2023-09-25
tags: [react, chakra]
comments: true
share: true
---

Chakra UI is a popular UI component library that provides a set of customizable and accessible components for building React applications. In this tutorial, we will walk you through the process of installing Chakra UI in your React project.

## Step 1: Create a new React project

Before we can install Chakra UI, we need to have a React project set up. If you already have an existing project, you can skip this step.

To create a new React project, open your terminal and run the following command:

```bash
npx create-react-app my-app
```

This will create a new directory called `my-app` and set up a basic React project inside it.

## Step 2: Install Chakra UI dependencies

Once you have your React project set up, navigate to the project directory by running:

```bash
cd my-app
```

Then, install the Chakra UI dependencies by running the following command:

```bash
npm install @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4
```

This command installs the necessary packages to use Chakra UI in your React project.

## Step 3: Import Chakra UI components

Now that we have Chakra UI installed, we can start using its components in our project.

To import Chakra UI components, open the `src/App.js` file and modify it as follows:

```javascript
import { ChakraProvider } from "@chakra-ui/react";
import { Button } from "@chakra-ui/react";

function App() {
  return (
    <ChakraProvider>
      <Button colorScheme="teal" size="md">
        Hello Chakra UI!
      </Button>
    </ChakraProvider>
  );
}

export default App;
```

In this example, we import the `ChakraProvider` component from `@chakra-ui/react` which allows us to use Chakra UI components in our application. We also import the `Button` component for demonstration purposes.

## Step 4: Start the React development server

To start your React development server, run the following command in your terminal:

```bash
npm start
```

This will launch your React application in the browser and you should see the Chakra UI button rendered.

Congratulations! You have successfully installed Chakra UI in your React project and imported a Chakra UI component.

## Conclusion

Chakra UI provides a comprehensive set of UI components that can greatly accelerate your React application development. By following the steps outlined in this tutorial, you should now have Chakra UI up and running in your React project.

#react #chakra-ui