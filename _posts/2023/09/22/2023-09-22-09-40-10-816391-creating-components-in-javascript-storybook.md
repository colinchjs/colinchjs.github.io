---
layout: post
title: "Creating components in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [storybook]
comments: true
share: true
---

JavaScript Storybook is an excellent tool for developing and testing UI components in isolation. It provides a dedicated environment for building, documenting, and visualizing components. In this blog post, we will explore how to create components in JavaScript Storybook.

## Setting Up JavaScript Storybook
Before we dive into creating components, let's quickly set up JavaScript Storybook in our project. Here are the steps:

1. Install Storybook globally using npm:
   ```bash
   npm install -g @storybook/cli
   ```

2. Initialize Storybook in your project directory:
   ```bash
   npx sb init
   ```

3. Run Storybook:
   ```bash
   npm run storybook
   ```

Once Storybook is up and running, you can access it in your browser at [http://localhost:6006](http://localhost:6006). Now let's move on to creating our first component.

## Creating a Component
Storybook organizes components into separate modules called "stories". A story represents a specific use case or variation of a component. To create a component in Storybook, follow these steps:

1. Inside the `src/components` directory, create a new file for your component. For example, let's create a `Button.js` component.

2. Define your component by importing React and writing your component code. Here's an example of a simple button component:

   ```javascript
   import React from 'react';

   const Button = ({ label, onClick }) => {
     return (
       <button onClick={onClick}>{label}</button>
     );
   };

   export default Button;
   ```

3. Create a new file in the `src/stories` directory, named after your component. For example, `Button.stories.js`.

4. In the story file, import the necessary dependencies, including the React component itself, and define stories using the `storiesOf` function provided by Storybook.

   ```javascript
   import React from 'react';
   import { storiesOf } from '@storybook/react';
   import Button from '../components/Button';

   storiesOf('Button', module)
     .add('Default', () => (
       <Button label="Click me" onClick={() => console.log('Button clicked')} />
     ))
     .add('Disabled', () => (
       <Button label="Click me" disabled />
     ));
   ```

5. Save the file, and Storybook will automatically detect and render the stories.

## Visualizing Components in Storybook
Once you have created stories for your components, you can visualize and interact with them in the Storybook UI. Storybook provides a fully interactive playground where you can tweak props, test different scenarios, and document usage.

You can also document additional information about your component, such as usage examples, prop types, and component API by adding annotations in the form of [decorators](https://storybook.js.org/docs/react/get-started/decorators).

## Conclusion
JavaScript Storybook is a powerful tool that simplifies the development and testing of UI components. It allows developers to create, visualize, and document components in isolation. By following the steps outlined in this article, you can start creating components in Storybook and streamline your component development process.

#javascript #storybook