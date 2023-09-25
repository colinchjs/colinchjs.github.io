---
layout: post
title: "Working with Stepper components in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraui]
comments: true
share: true
---

![Chakra UI Logo](https://chakra-ui.com/logo.png)

Chakra UI is a popular and powerful React component library that provides a set of customizable UI components. One of these components is the Stepper, which allows you to create a multi-step form or wizard-like user interface.

## Getting Started

To get started with using the Stepper component in Chakra UI, you'll need to install Chakra UI in your React project. You can do this by running the following command:

```
npm install @chakra-ui/react
```

Or if you prefer using yarn:

```
yarn add @chakra-ui/react
```

Once you have Chakra UI installed, you can import the Stepper component and start using it in your application.

```jsx
import { Stepper, Step } from "@chakra-ui/react"

function MyStepperComponent() {
  return (
    <Stepper activeStep={0}>
      <Step label="Step 1">Step 1 Content</Step>
      <Step label="Step 2">Step 2 Content</Step>
      <Step label="Step 3">Step 3 Content</Step>
    </Stepper>
  )
}
```

In the example above, we create a basic Stepper component with three steps. Each step is represented by the `Step` component and has a label and content. The `activeStep` prop is used to specify which step is currently active.

## Customizing the Stepper

Chakra UI provides a wide range of customization options for the Stepper component. You can customize the colors, sizes, orientation, and more.

```jsx
<Stepper activeStep={0} size="lg" colorScheme="teal" orientation="vertical">
  <Step label="Step 1">Step 1 Content</Step>
  <Step label="Step 2">Step 2 Content</Step>
  <Step label="Step 3">Step 3 Content</Step>
</Stepper>
```

In the example above, we set the size to `lg`, color scheme to `teal`, and orientation to `vertical`. These are just a few examples of the customization options available in Chakra UI. You can refer to the Chakra UI documentation for a full list of customization options.

## Conclusion

The Stepper component in Chakra UI provides an easy and intuitive way to create multi-step forms or wizard-like interfaces in your React applications. With its extensive customization options, you can tailor the appearance and behavior of the Stepper to fit your specific needs.

#react #chakraui