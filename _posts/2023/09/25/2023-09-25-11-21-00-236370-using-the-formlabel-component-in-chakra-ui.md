---
layout: post
title: "Using the FormLabel component in Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, formlabel]
comments: true
share: true
---

Chakra UI is a popular React component library that provides a set of accessible and customizable UI components. One of the components it offers is `FormLabel`, which provides a label for input elements in forms. In this blog post, we will explore how to use the `FormLabel` component in Chakra UI.

## Importing the `FormLabel` component

To start working with the `FormLabel` component, you first need to import it from the Chakra UI library. You can do this by adding the following line at the top of your file:

```jsx
import { FormLabel } from "@chakra-ui/react";
```
Here, we are importing the `FormLabel` component from the `@chakra-ui/react` package.

## Using the `FormLabel` component

Once you have imported the `FormLabel`, you can use it within your React component. You can pass the text you want to display as the label to the `FormLabel` component using the `children` prop.

```jsx
<FormLabel>Username</FormLabel>
```

In the example above, "Username" is the label that will be displayed for the input element. You can customize the appearance of the label using the various props provided by the `FormLabel` component.

## Customizing the appearance of the `FormLabel`

Chakra UI provides several props to customize the appearance of the `FormLabel` component. For example, you can change the font size of the label using the `fontSize` prop, and you can set the color using the `color` prop.

```jsx
<FormLabel fontSize="lg" color="blue.500">Username</FormLabel>
```

In the code snippet above, we are setting the font size of the label to "lg" and the color to "blue.500". You can also apply any other CSS properties to the `FormLabel` component for further customization.

## Conclusion

The `FormLabel` component in Chakra UI allows you to easily add labels to your input elements in forms. With its customizable appearance and accessibility features, it provides a convenient way to enhance the user experience. By using the `FormLabel` component, you can improve the usability and accessibility of your forms in your React applications.

#chakraui #formlabel