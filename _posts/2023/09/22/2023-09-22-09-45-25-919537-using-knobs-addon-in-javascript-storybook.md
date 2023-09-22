---
layout: post
title: "Using Knobs addon in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [javascript, storybook]
comments: true
share: true
---

If you're using JavaScript Storybook to develop and showcase your components, you might already be aware of the various addons available to enhance your workflow. One such popular addon is the **Knobs** addon.

## What is the Knobs Addon?

The **Knobs** addon is a powerful tool that allows you to interactively change the values of your component's props right from the Storybook UI. It provides a simple and intuitive way to tweak the appearance and behavior of your components in real-time, without having to modify your code.

## How to Install the Knobs Addon?

To install the Knobs addon in your JavaScript Storybook project, follow these steps:

1. Open your terminal and navigate to the root directory of your project.
2. Run the following command to install the Knobs addon:

```bash
npm install @storybook/addon-knobs --save-dev
```

3. Once the installation is complete, open the `.storybook/main.js` file in your project.
4. Add the following code snippet to the `addons` array:

```javascript
module.exports = {
  addons: [
    '@storybook/addon-knobs'
  ],
};
```

5. Save the file and start or restart your Storybook server.

## How to Use the Knobs Addon?

Using the Knobs addon is pretty straightforward. Here's an example of how you can use it to modify a component's props:

```javascript
import React from 'react';
import { withKnobs, text } from '@storybook/addon-knobs';

export default {
  title: 'MyComponent',
  decorators: [withKnobs],
};

export const MyComponent = () => {
  const name = text('Name', 'John Doe');
  const age = text('Age', '25');
  
  return (
    <div>
      <h2>{name}</h2>
      <p>{`Age: ${age}`}</p>
    </div>
  );
};
```

In the code above, we import the `withKnobs` decorator and the `text` knob from the `@storybook/addon-knobs` package. Then, we use the `text` knob to create editable properties for `name` and `age` variables. By default, the `text` knob will display the provided default value, but you can modify it in the Storybook UI.

## Conclusion

The Knobs addon is a valuable tool for JavaScript Storybook developers, allowing for easy customization of component props through an intuitive UI. By leveraging the power of the Knobs addon, you can easily experiment with different configurations without having to modify your code every time. Give it a try and see how it can enhance your component development process!

**#javascript #storybook**