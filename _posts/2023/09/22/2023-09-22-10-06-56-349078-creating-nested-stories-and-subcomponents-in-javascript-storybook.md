---
layout: post
title: "Creating nested stories and subcomponents in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [Storybook, JavaScript]
comments: true
share: true
---

![Storybook](https://cdn-images-1.medium.com/max/1200/1*cyXCE-JcBelTyrK-58w6_Q.png)

Storybook is a powerful tool for developing UI components in isolation. It allows you to create and showcase different states of your components, providing a convenient way to test and document them. One of the key features of Storybook is the ability to create nested stories and subcomponents, which allows for even more flexibility and organization in your component library. In this tutorial, we will explore how to create nested stories and subcomponents in JavaScript Storybook.

## What are nested stories and subcomponents?

Nested stories are a way of organizing your components into a hierarchical structure within Storybook. This is particularly useful when you have components that contain other components, such as a component that renders a modal with different content inside.

Subcomponents, on the other hand, are components that are part of a larger component. They can be thought of as "child" components within a "parent" component. For example, a parent component might be a form, while the subcomponents could be input fields, buttons, or checkboxes.

## How to create nested stories

To create nested stories in Storybook, you need to organize your components into a folder structure that represents the hierarchy you want to create. Each folder should contain a `index.js` file, which will serve as the entry point for that level of the hierarchy.

Here's an example folder structure for a component library:

```javascript
├── components
│   ├── Button
│   │   ├── index.js
│   │   └── Button.stories.js
│   ├── Modal
│   │   ├── index.js
│   │   ├── Modal.stories.js
│   │   └── components
│   │       ├── Header.js
│   │       ├── Body.js
│   │       └── Footer.js
│   └── ...
```

In this example, the `Modal` component has its own folder, which contains a `Modal.stories.js` file for the top-level story. Additionally, it has a `components` folder that contains the subcomponents `Header.js`, `Body.js`, and `Footer.js`. Each subcomponent can also have its own story file.

To create the nested story, you need to import the subcomponents and use them within the parent component's story. Here's an example of how the `Modal.stories.js` file might look:

```javascript
import React from 'react';
import Modal from './index';
import Header from './components/Header';
import Body from './components/Body';
import Footer from './components/Footer';

export default {
  title: 'Modal',
  component: Modal,
};

export const Default = () => (
  <Modal>
    <Header />
    <Body />
    <Footer />
  </Modal>
);
```

When you run Storybook, you should see the nested story structure in the sidebar, with the parent component and its subcomponents nested under it. You can then click on each individual story to view and interact with them separately.

## Conclusion

Creating nested stories and subcomponents in JavaScript Storybook allows you to organize and showcase your components in a more structured and logical way. This can greatly enhance your component library's usability and maintainability. By utilizing nested stories, you can better document and test the different states and variations of your components. Start organizing your components into a nested structure today and take your component development workflow to the next level!

## #Storybook #JavaScript