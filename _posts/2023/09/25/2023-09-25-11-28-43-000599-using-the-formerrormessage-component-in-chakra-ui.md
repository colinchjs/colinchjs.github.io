---
layout: post
title: "Using the FormErrorMessage component in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraui]
comments: true
share: true
---

Creating forms in web applications often involves validating user input. Chakra UI, a popular component library for React, provides the `FormErrorMessage` component to conveniently display error messages associated with form fields. In this blog post, we will explore how to use the `FormErrorMessage` component effectively in your Chakra UI forms.

## Installing Chakra UI

Before we start, make sure you have Chakra UI installed in your React project. You can install Chakra UI by running the following command:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once installed, make sure to wrap your application's root component with the `ChakraProvider`.

## Using the FormErrorMessage component

To use the `FormErrorMessage` component, follow these steps:

1. Import the necessary components from Chakra UI:

```javascript
import { FormControl, FormLabel, FormErrorMessage, Input } from "@chakra-ui/react";
```

2. Include the `FormErrorMessage` component within a `FormControl` component:

```javascript
<FormControl isInvalid={error}>
  <FormLabel>Email address</FormLabel>
  <Input type="email" />
  <FormErrorMessage>{errorMessage}</FormErrorMessage>
 </FormControl>
```

The `isInvalid` prop on `FormControl` determines whether to display the error message. Set it to `true` when an error is present. The `FormErrorMessage` component displays the error message passed as its child.

3. Handling form validation and errors:

To control the error message display, you need to handle form validation and track any errors. Here's an example of how you can handle form validation using the `useState` hook:

```javascript
import { useState } from "react";

function MyForm() {
  const [email, setEmail] = useState("");
  const [error, setError] = useState(false);

  const handleSubmit = (event) => {
    event.preventDefault();
  
    if (!email) {
      setError(true);
      return;
    }
    
    // Submit the form
  };

  return (
    <form onSubmit={handleSubmit}>
      <FormControl isInvalid={error}>
        <FormLabel>Email address</FormLabel>
        <Input
          type="email"
          value={email}
          onChange={(event) => {
            setEmail(event.target.value);
            setError(false);
          }}
        />
        <FormErrorMessage>
          {!email && "Please enter your email address"}
        </FormErrorMessage>
      </FormControl>
      
      <Button type="submit">Submit</Button>
    </form>
  );
}
```

In the example above, we track the email input value and the error state using the `useState` hook. When the form is submitted, we check if the email is empty and set the error state to `true` if it is. The error message will be displayed by the `FormErrorMessage` component.

## Conclusion

Using the `FormErrorMessage` component in Chakra UI makes it easy to display error messages for form validation. By following the steps outlined in this blog post, you can enhance the user experience of your web forms by providing clear error feedback. 

Remember to install Chakra UI, import the necessary components, and handle form validation to make the most of the `FormErrorMessage` component. Happy coding!

#react #chakraui