---
layout: post
title: "Exploring the Storybook UI in Javascript Storybook"
description: " "
date: 2023-09-22
tags: [Storybook, JavaScriptStorybook]
comments: true
share: true
---

Are you a JavaScript developer looking for a way to build, test, and document UI components in isolation? Have you heard of Storybook? If not, you're in for a treat!

Storybook is a powerful tool used by developers to explore and showcase UI components in an interactive and isolated environment. It allows you to build and test components without the need for a complete application. Let's dive into how you can make the most out of the Storybook UI.

## Getting Started

To begin, you'll need to have Node.js and npm installed on your machine. If you don't have them yet, you can download and install them from the official Node.js website.

Once you have Node.js and npm installed, you can set up Storybook by following these steps:

1. Open your terminal or command prompt and navigate to your project directory.
2. Run the following command to initialize a new JavaScript project:

```shell
npm init -y
```

3. Next, install Storybook globally using the following command:

```shell
npm install -g @storybook/cli
```

4. Initialize Storybook in your project:

```shell
npx sb init
```

5. Once the installation is complete, run the following command to start Storybook:

```shell
npm run storybook
```

## Adding Stories

Now that you have Storybook set up, it's time to add your first story. Stories are individual components or sets of components with some properties that you want to showcase. To add a story, follow these steps:

1. Inside the `src` directory of your project, create a new folder called `components`.
2. Inside the `components` folder, create a new file for your component, for example, `Button.js`.
3. In the `Button.js` file, write your component code. Here's an example of a basic button component:

```javascript
import React from 'react';

const Button = ({ label, onClick }) => {
  return <button onClick={onClick}>{label}</button>;
};

export default Button;
```

4. Now, create a new file called `Button.stories.js` inside the same `components` folder.
5. In the `Button.stories.js` file, import your component and define your stories using the Storybook syntax. Here's an example:

```javascript
import React from 'react';
import Button from './Button';

export default {
  title: 'Components/Button',
  component: Button,
};

export const Primary = () => <Button label="Primary Button" />;
export const Secondary = () => <Button label="Secondary Button" />;
export const Disabled = () => <Button label="Disabled Button" disabled />;
```

## Exploring the Storybook UI

1. Once you've added your stories, start or restart Storybook by running the command `npm run storybook` in your terminal.
2. Open your browser and go to `http://localhost:6006` (the default Storybook port).
3. You should now see the Storybook UI with your component stories listed on the left sidebar.
4. Click on a story name to view the component in the Storybook canvas, where you can interact with it, view different states, and modify its properties.

## Conclusion

Storybook provides a powerful environment for JavaScript developers to build and showcase UI components in isolation. By following the steps outlined in this article, you've set up Storybook, added your first story, and explored the Storybook UI.

Start exploring Storybook today and experience the benefits of developing, testing, and documenting your UI components in a clean and interactive way! Don't forget to share your experiences using #Storybook and #JavaScriptStorybook. Happy coding!