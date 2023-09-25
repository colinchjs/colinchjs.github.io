---
layout: post
title: "Building radio buttons with Chakra UI's Radio component"
description: " "
date: 2023-09-25
tags: [chakraui, react]
comments: true
share: true
---

One common UI element that you'll often find in web forms is radio buttons. Radio buttons allow users to select one option out of a given list. In this blog post, we'll explore how to build radio buttons using Chakra UI's Radio component, a powerful and customizable UI library for React.

## What is Chakra UI?

Chakra UI is a simple and modular UI component library for React that focuses on accessibility, customizability, and developer experience. It provides a set of pre-built components that you can easily customize and use in your React applications.

## Getting started with Chakra UI

Before we dive into building radio buttons, let's set up a new React project with Chakra UI. You can use `create-react-app` to generate a new React project by running the following command:

```
npx create-react-app chakra-demo
```

After the project is created, navigate to the project directory and install Chakra UI and its dependencies by running:

```
cd chakra-demo
npm i @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4
```

Once the installation is complete, you can start building your Chakra UI components.

## Building radio buttons with Chakra UI

To build radio buttons using Chakra UI's Radio component, follow these steps:

1. Import the necessary Chakra UI components and hooks:

```
import { Radio, RadioGroup } from "@chakra-ui/react";
```

2. Create a radio button group by wrapping the Radio components in a RadioGroup component:

```jsx
<RadioGroup defaultValue="react">
  <Radio value="react">React</Radio>
  <Radio value="angular">Angular</Radio>
  <Radio value="vue">Vue</Radio>
</RadioGroup>
```

3. Customize the appearance of the radio buttons using Chakra UI's styling props. For example, you can change the color of the selected radio button:

```jsx
<RadioGroup defaultValue="react">
  <Radio value="react" colorScheme="blue">React</Radio>
  <Radio value="angular" colorScheme="red">Angular</Radio>
  <Radio value="vue" colorScheme="green">Vue</Radio>
</RadioGroup>
```

4. Add event handlers to handle the selection of radio buttons. You can use the `onChange` prop to capture the selected value:

```jsx
const handleRadioChange = (value) => {
  console.log(value);
};

<RadioGroup defaultValue="react" onChange={handleRadioChange}>
  <Radio value="react">React</Radio>
  <Radio value="angular">Angular</Radio>
  <Radio value="vue">Vue</Radio>
</RadioGroup>
```

By following these steps, you can easily build radio buttons using Chakra UI's Radio component. Chakra UI provides many other customization options and features, so make sure to explore their documentation for more advanced usage.

# Conclusion

Chakra UI's Radio component makes it easy to build radio buttons in your React applications. By leveraging the power of Chakra UI's customization and accessibility features, you can create interactive and user-friendly forms. So give it a try in your next React project!

#chakraui #react #radiobuttons #webdevelopment