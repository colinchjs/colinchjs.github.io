---
layout: post
title: "Implementing toast notifications using Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ToastNotifications]
comments: true
share: true
---

To enhance the user experience of your web application, implementing toast notifications can be a great way to provide important updates or messages in a non-intrusive way. In this tutorial, we will explore how to implement toast notifications using Chakra UI, a popular React component library.

## Prerequisites

Before getting started, ensure that you have the following prerequisites installed:

- Node.js and npm
- React.js

## Setting Up

First, let's create a new React project by running the following command in your terminal:

```bash
npx create-react-app toast-notifications
cd toast-notifications
```

Next, install the required dependencies:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating a Toast Component

In this step, we will create a reusable Toast component using Chakra UI.

Create a new file named `Toast.js` in the `src/components` directory and add the following code:

```jsx
import { useEffect } from 'react';
import { useToast } from '@chakra-ui/react';

const Toast = ({ title, description, status }) => {
  const toast = useToast();

  useEffect(() => {
    toast({
      title,
      description,
      status,
      duration: 5000,
      isClosable: true,
    });
  }, [title, description, status, toast]);

  return null;
};

export default Toast;
```

In the above code, we import the necessary modules from Chakra UI. We use the `useToast` hook to access the toast functionality. Inside the `useEffect` hook, we call the `toast` function with the provided `title`, `description`, `status`, and additional options like `duration` and `isClosable`.

## Using the Toast Component

Now, let's integrate the `Toast` component and display a toast notification when a specific event occurs.

Open the `src/App.js` file and add the following code:

```jsx
import React from 'react';
import Toast from './components/Toast';

const App = () => {
  const handleClick = () => {
    <Toast title="Success" description="Toast notification example" status="success" />;
  };

  return (
    <div>
      <button onClick={handleClick}>Show Toast</button>
    </div>
  );
};

export default App;
```

In the above code, we import and use the `Toast` component in the `handleClick` function. When the button is clicked, it triggers the `handleClick` function, which will render the toast notification with the specified title, description, and status.

## Styling the Toast Notifications

Chakra UI provides extensive styling capabilities, allowing you to customize the appearance of your toast notifications. You can customize these styles by modifying the Chakra UI theme or by directly applying additional styles to the components.

## Conclusion

In this tutorial, we learned how to implement toast notifications using Chakra UI in a React application. Toast notifications provide a user-friendly way to display important updates or messages without interrupting the user's workflow. By using Chakra UI's built-in toast functionality, we can easily incorporate these notifications into our web application.

Implement toast notifications in your application today and enhance the user experience! #ChakraUI #ToastNotifications