---
layout: post
title: "Using global styles in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [developer, storybook]
comments: true
share: true
---

When developing UI components in JavaScript using Storybook, it is essential to have consistent and cohesive styles across different components. One way to achieve this is by using global styles in Storybook. Global styles allow you to define styles that will be applied to all components within your Storybook project.

In this blog post, we'll explore how to set up and use global styles in JavaScript Storybook.

## Setting up Global Styles

To use global styles in Storybook, you'll need to follow these steps:

### Step 1: Create a CSS file for your global styles

Create a new CSS file where you'll define your global styles. For example, you could create a file called `global.css`.

### Step 2: Import the CSS file in your Storybook configuration

In your Storybook configuration file (`.storybook/preview.js`), import the CSS file you created in the previous step. You can use the `addParameters` function to add global styles to your components.

Here's an example of how you can import the CSS file and apply the global styles:

```javascript
import '../path/to/global.css';
import { addParameters } from '@storybook/react';

addParameters({
  options: {
    theme: {
      // define your global styles here
      base: 'dark',
    },
  },
});
```

### Step 3: Apply global styles to your components

Once the global styles are set up, you can apply them to your components by using the `class` attribute in your component's stories.

For example, if you have a `Button` component and you want to apply the global styles, you can add the CSS class in your component's story:

```javascript
import React from 'react';

export default {
  title: 'Button',
  component: Button,
};

export const Default = () => (
  <Button className="global-styles">Default Button</Button>
);
```

In the above example, the `global-styles` CSS class is added to the `Button` component, applying the global styles defined in the `global.css` file.

## Conclusion

Using global styles in JavaScript Storybook allows you to maintain consistent styles across different components in your project. By following the steps outlined in this blog post, you can easily set up and apply global styles to your Storybook project.

With global styles, you can ensure that your components look cohesive and provide a unified user experience. Happy coding!

#developer #storybook #globalstyles