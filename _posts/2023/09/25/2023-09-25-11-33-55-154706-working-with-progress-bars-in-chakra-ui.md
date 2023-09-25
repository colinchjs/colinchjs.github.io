---
layout: post
title: "Working with progress bars in Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, ProgressBar]
comments: true
share: true
---

Progress bars are a common UI component used to display the progress of a task, such as file uploads, form submissions, or loading data. Chakra UI, a popular React component library, provides an easy and customizable way to work with progress bars in your applications.

## Installing Chakra UI

To get started, you'll need to install Chakra UI in your React project. Run the following command in your terminal:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating a basic progress bar

Chakra UI provides a `Progress` component that can be used to create a basic progress bar. Here's an example of how to use it:

```jsx
import { Progress } from "@chakra-ui/react";

function App() {
  return (
    <Progress value={60} size="md" colorScheme="teal" />
  );
}

export default App;
```

In the example above, we import the `Progress` component from Chakra UI and render it with a `value` prop set to `60`. This will display a progress bar that is 60% complete. We also specify the `size` and `colorScheme` props to customize the appearance of the progress bar.

## Customizing the progress bar

Chakra UI provides several props that allow you to customize the appearance and behavior of the progress bar. Here are a few examples:

### Changing the color

You can change the color of the progress bar by setting the `colorScheme` prop to a valid color scheme from the Chakra UI theme. For example:

```jsx
<Progress value={75} colorScheme="blue" />
```

### Adjusting the size

You can adjust the size of the progress bar by setting the `size` prop to one of the available sizes: `sm`, `md`, or `lg`. For example:

```jsx
<Progress value={50} size="lg" />
```

### Adding a label

You can add a label to the progress bar by setting the `hasStripe` prop to `true`. This will display the progress percentage as a text label on the progress bar. For example:

```jsx
<Progress value={80} hasStripe />
```

## Conclusion

Chakra UI makes it easy to work with progress bars in your React applications. By using the `Progress` component and customizing its props, you can create visually appealing and functional progress bars to enhance the user experience. So go ahead, give it a try, and make your applications more informative and engaging with progress bars!

\#ChakraUI #ProgressBar