---
layout: post
title: "Styling textareas with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ReactUI]
comments: true
share: true
---

Textareas are commonly used in web applications to allow users to input longer pieces of text. Chakra UI, a popular React component library, provides a convenient way to style textareas with its built-in components. In this blog post, we will explore how to style textareas using Chakra UI.

## Installation

To get started, make sure you have Chakra UI installed in your project. You can install it via npm or yarn:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```bash
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Usage

Once Chakra UI is installed, you can start using its components to style textareas. Here's an example of how to style a textarea using Chakra UI:

```jsx
import { ChakraProvider, Textarea } from "@chakra-ui/react";

function App() {
  return (
    <ChakraProvider>
      <Textarea
        placeholder="Enter your text here"
        resize="vertical"
        size="lg"
        focusBorderColor="blue.500"
      />
    </ChakraProvider>
  );
}

export default App;
```

In the above example, we import the necessary components from Chakra UI and wrap our `Textarea` component in a `ChakraProvider`. The `Textarea` component accepts various props to customize its styling. Here are some of the important props used in this example:

- `placeholder`: Sets the placeholder text for the textarea.
- `resize`: Specifies whether the textarea should be resizable vertically ("vertical") or not ("none").
- `size`: Sets the size of the textarea ("sm", "md", "lg").
- `focusBorderColor`: Sets the border color when the textarea is in focus.

You can further customize the textarea by adding more props or applying custom CSS styles. Chakra UI provides a wide range of styling options to suit your needs.

## Conclusion

Styling textareas with Chakra UI is a breeze. With its intuitive API and extensive customization options, you can easily create beautiful and responsive textareas in your web applications. Start using Chakra UI in your project today and take advantage of its powerful components.

#ChakraUI #ReactUI