---
layout: post
title: "Using addons in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [JavaScript, Storybook]
comments: true
share: true
---

JavaScript Storybook is a powerful tool for developing, testing, and documenting UI components in isolation. It offers a wide range of addons that enhance the functionalities of Storybook and make it even more versatile. In this article, we will explore how to use addons in JavaScript Storybook to maximize our component development workflow.

## Getting Started with Addons

To begin, make sure you have Storybook set up in your JavaScript project. If you haven't done this yet, you can follow the official documentation to install and configure Storybook.

Once you have Storybook up and running, installing addons is easy. Simply open the terminal in your project directory and execute the following command:

```
npm install @storybook/addons
```

This command installs the official addons package, which provides a collection of useful addons that you can use in your Storybook.

## Enabling Addons

To enable an addon in your Storybook, you need to update the `main.js` configuration file located in the `.storybook` directory. Open the `main.js` file and add the following lines:

```javascript
module.exports = {
  addons: [
    '@storybook/addon-actions',
    '@storybook/addon-knobs',
  ],
};
```

In this example, we enable two popular addons: `@storybook/addon-actions` and `@storybook/addon-knobs`. These addons provide functionalities to interact with and manipulate components within Storybook.

## Using Addons

Once you have enabled the desired addons, you can start using them in your Storybook stories. Let's see how we can use the `@storybook/addon-actions` and `@storybook/addon-knobs` addons.

### @storybook/addon-actions

The `@storybook/addon-actions` addon allows you to create interactive actions for your components. You can listen to those actions and perform actions or log data when the user interacts with the component.

To use `@storybook/addon-actions`, import it in your story file:

```javascript
import { action } from '@storybook/addon-actions';
```

Then, you can use the `action` function to create events within your components:

```javascript
export const Button = () => (
  <button onClick={action('clicked')}>Click me</button>
);
```

### @storybook/addon-knobs

The `@storybook/addon-knobs` addon provides a set of UI controls that allow you to dynamically change data and props of the components. This is useful for tweaking and testing different scenarios without having to modify the code.

To use `@storybook/addon-knobs`, import it in your story file:

```javascript
import { withKnobs, text } from '@storybook/addon-knobs';
```

Then, wrap your story with the `withKnobs` decorator and use the `text` function to create editable text knobs:

```javascript
export const Card = () => {
  const name = text('Name', 'John Doe');
  return <div>{name}</div>;
};

export default {
  title: 'Card',
  decorators: [withKnobs],
};
```

## Conclusion

Addons greatly expand the capabilities of JavaScript Storybook and make component development even more efficient. By using addons like `@storybook/addon-actions` and `@storybook/addon-knobs`, you can improve the interactivity and flexibility of your components.

Remember to explore the Storybook documentation to discover more addons and functionalities that can enhance your development workflow. Happy coding!

#JavaScript #Storybook #UIcomponents #ComponentDevelopment #Addons