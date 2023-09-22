---
layout: post
title: "Creating interactive component showcase with Javascript Storybook"
description: " "
date: 2023-09-22
tags: [React, Storybook]
comments: true
share: true
---

Storybook is a powerful tool for developing and documenting UI components in a systematic and interactive way. It allows you to create an isolated environment where you can easily visualize, test, and document your components. In this blog post, we will explore how to set up and use Storybook to create an interactive component showcase using Javascript.

## Setting Up Storybook

To get started with Storybook, make sure you have Node.js installed on your machine. Open your terminal and follow these steps:

1. Create a new directory for your project and navigate to it:
```
mkdir my-component-showcase
cd my-component-showcase
```

2. Initialize a new npm project:
```
npm init -y
```

3. Install Storybook as a development dependency:
```
npx -p @storybook/cli sb init --type react
```

4. Start the Storybook development server:
```
npm run storybook
```

## Creating Component Stories

Now that Storybook is set up, let's create some stories for our components.

1. Inside the project directory, create a new subdirectory called `src`.

2. Inside the `src` directory, create a new file called `MyComponent.stories.js`.

3. In `MyComponent.stories.js`, import the necessary dependencies:
```javascript
import React from 'react';
import { storiesOf } from '@storybook/react';
import MyComponent from './MyComponent';
```

4. Create a Storybook story using the `storiesOf` function:
```javascript
storiesOf('MyComponent', module)
  .add('Default', () => <MyComponent />)
  .add('With Props', () => <MyComponent prop1="value1" prop2="value2" />);
```

In the code above, we define two stories for `MyComponent`. The first story, named "Default", shows the component without any props. The second story, named "With Props", demonstrates the component with some example props.

## Showcasing Components in Storybook

1. Open the Storybook development server at `http://localhost:6006` in your preferred browser. You should see the Storybook UI with a list of stories on the left panel.

2. Click on a story to view the rendered component. You can interact with it, modify props (if applicable), and see the changes instantly.

## Adding Interactivity

Storybook provides addons that extend its functionality and allow for interactivity. Let's add the Knobs addon to modify component props dynamically.

1. Stop the Storybook development server (`Ctrl + C` in the terminal).

2. Install the `@storybook/addon-knobs` package:
```
npm install --save-dev @storybook/addon-knobs
```

3. Open the `.storybook/main.js` file and add the following configuration:
```javascript
module.exports = {
  stories: ['../src/**/*.stories.js'],
  addons: ['@storybook/addon-knobs'],
};
```

4. Restart the Storybook development server (`npm run storybook`).

5. Modify the component stories to use the Knobs addon:
```javascript
import { withKnobs, text, boolean } from '@storybook/addon-knobs';

const stories = storiesOf('MyComponent', module);
stories.addDecorator(withKnobs);

stories
  .add('Default', () => {
    const prop1 = text('Prop 1', 'default value');
    const prop2 = boolean('Prop 2', false);
    return <MyComponent prop1={prop1} prop2={prop2} />;
  });
```

## Conclusion

With Storybook, you can easily create an interactive component showcase for your Javascript project. It allows you to develop and document UI components in an isolated environment, making it easier to iterate and collaborate. By leveraging addons like Knobs, you can add interactivity to your component stories, making the showcase even more powerful.

#React #Storybook