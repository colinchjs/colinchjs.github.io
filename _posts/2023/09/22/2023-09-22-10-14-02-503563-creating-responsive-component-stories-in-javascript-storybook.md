---
layout: post
title: "Creating responsive component stories in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [storybook, javascript]
comments: true
share: true
---

Storybook is a popular tool for developing and testing UI components in isolation. One of the key benefits of Storybook is the ability to create stories, which are individual units of a component's behavior or appearance. However, sometimes we need to test and showcase how our components respond to different screen sizes. In this blog post, we will explore how to create responsive component stories in JavaScript Storybook.

## Setting Up Storybook

Before we dive into creating responsive component stories, make sure you have Storybook set up in your project. If you haven't done that yet, you can follow the official [Storybook documentation](https://storybook.js.org/docs/react/get-started/introduction) to set it up. Once you have a basic Storybook setup, we can move forward.

## Creating Responsive Stories

To create responsive component stories, we can leverage the power of addons provided by Storybook. The addon that we will be using is called [Viewport](https://www.npmjs.com/package/@storybook/addon-viewport). This addon lets us test our components at different viewport sizes.

### Installing and Configuring the Viewport Addon

To install the Viewport addon, run the following command in your project directory:

```
npm install --save-dev @storybook/addon-viewport
```

Next, we need to configure the addon to be used by Storybook. In your `.storybook/main.js` or `.storybook/webpack.config.js`, add the following code:

```js
module.exports = {
  addons: ['@storybook/addon-viewport'],
};
```

### Creating Responsive Stories

Now that the Viewport addon is installed and configured, we can create responsive component stories. To do this, we can use the `parameters` option provided by Storybook's API.

Let's say we have a `Button` component that we want to test at different screen sizes. We can create a file named `Button.stories.js` and write our responsive stories like this:

```jsx
import React from 'react';
import Button from '../Button';

export default {
  title: 'Components/Button',
  component: Button,
  parameters: {
    viewport: {
      defaultViewport: 'desktop',
      viewports: {
        desktop: {
          name: 'Desktop',
          styles: {
            width: '1024px',
            height: '768px',
          },
        },
        tablet: {
          name: 'Tablet',
          styles: {
            width: '768px',
            height: '1024px',
          },
        },
        mobile: {
          name: 'Mobile',
          styles: {
            width: '375px',
            height: '667px',
          },
        },
      },
    },
  },
};

export const Default = () => <Button>Click Me!</Button>;
export const Primary = () => <Button primary>Click Me!</Button>;
```

In the above example, we have defined three viewports: `desktop`, `tablet`, and `mobile`. We provided the width and height for each viewport styles. Now, when we run the Storybook server and open the `Button` story, we will see a new control panel that allows us to switch between different viewports and test our component's responsiveness.

## Conclusion

Creating responsive component stories in JavaScript Storybook allows us to easily test and showcase how our components behave at different screen sizes. By using the Viewport addon, we can efficiently develop and iterate on responsive designs. Give it a try in your next Storybook project and see the benefits it brings to your component development workflow!

#storybook #javascript #UIcomponents #responsive