---
layout: post
title: "Styling text inputs with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

Chakra UI is a popular React component library that provides a set of customizable and accessible UI components. In this blog post, we will explore how to style text inputs using Chakra UI.

## Getting started with Chakra UI

First, let's set up a new React project and install Chakra UI:

```bash
npx create-react-app chakra-ui-demo
cd chakra-ui-demo
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Now, you can import and use Chakra UI components in your React application. Let's move on to styling text inputs.

## Styling text inputs

Chakra UI provides a `Input` component that can be used for text inputs. To style the text inputs, you can use the `Input` component and customize its appearance using Chakra UI's styling props.

Here's an example of how to style a basic text input using Chakra UI:

```jsx
import { Input } from "@chakra-ui/react";

function MyForm() {
  return (
    <Input
      placeholder="Enter your name"
      _focus={{ borderColor: "blue.500", boxShadow: "outline" }}
    />
  );
}
```

In the example above, we import the `Input` component from Chakra UI and use it inside a `MyForm` component. We pass the `placeholder` prop to the `Input` component to provide a hint to the user. We also use the `_focus` prop to define the styles when the input is focused. In this case, we set the border color to blue and add an outline box shadow.

You can further customize the text input by applying different props provided by Chakra UI. For example, you can use the `size` prop to adjust the size of the input, or the `variant` prop to choose different styles for the text input.

## Conclusion

Styling text inputs with Chakra UI is straightforward and allows for easy customization. By using the `Input` component and Chakra UI's styling props, you can create visually appealing and accessible text inputs for your React applications.

Give Chakra UI a try in your next project and see how easy it is to style text inputs and other UI components!

#React #ChakraUI