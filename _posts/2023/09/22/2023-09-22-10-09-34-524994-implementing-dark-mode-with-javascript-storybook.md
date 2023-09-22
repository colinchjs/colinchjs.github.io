---
layout: post
title: "Implementing dark mode with Javascript Storybook"
description: " "
date: 2023-09-22
tags: [f0f0f0, f0f0f0]
comments: true
share: true
---

Dark mode has become a popular trend in modern user interfaces, providing a visually appealing and eye-friendly experience for users. In this blog post, we will explore how to implement dark mode using JavaScript and Storybook, a popular tool for building UI components.

## Prerequisites

- Basic knowledge of JavaScript and CSS
- Familiarity with Storybook and its setup

## Step 1: Setting up Storybook

First, let's make sure we have Storybook installed and set up in our project. If you haven't done this yet, follow these steps:

1. Install Storybook using npm or yarn:
   
   ```bash
   $ npm install --global @storybook/cli
   ```
   
   or
   
   ```bash
   $ yarn global add @storybook/cli
   ```
   
2. Initialize a new Storybook project in your project's root directory:
   
   ```bash
   $ npx sb init
   ```
   
   or
   
   ```bash
   $ yarn sb init
   ```
   
3. Start the Storybook server:
   
   ```bash
   $ npm run storybook
   ```
   
   or
   
   ```bash
   $ yarn storybook
   ```

## Step 2: Creating a Dark Mode toggle component

Now, let's create a component that will act as a toggle for enabling/disabling the dark mode. In this example, we will create a basic button component:

```javascript
import React, { useState } from 'react';

const DarkModeToggle = () => {
    const [isDarkMode, setIsDarkMode] = useState(false);

    const toggleDarkMode = () => {
        setIsDarkMode(!isDarkMode);
    };

    return (
        <button onClick={toggleDarkMode}>
            {isDarkMode ? 'Disable Dark Mode' : 'Enable Dark Mode'}
        </button>
    );
};

export default DarkModeToggle;
```

## Step 3: Styling for Dark Mode

Now that we have our toggle component, let's add styling for the dark mode. You can customize the styling according to your project requirements:

```css
body {
    background-color: #f0f0f0;
    color: #333;
}

.dark-mode {
    background-color: #333;
    color: #f0f0f0;
}
```

## Step 4: Applying Dark Mode to Storybook

To apply dark mode to our Storybook, we'll need to modify the `preview-head.html` file located in the `.storybook` directory. Add the following JavaScript code to dynamically toggle the dark mode class:

```html
<script>
    document.addEventListener('DOMContentLoaded', function() {
        const darkModeToggle = document.getElementById('dark-mode-toggle');

        darkModeToggle.addEventListener('change', function(event) {
            const body = document.querySelector('body');
        
            if (event.target.checked) {
                body.classList.add('dark-mode');
            } else {
                body.classList.remove('dark-mode');
            }
        });
    });
</script>
```

## Step 5: Testing Dark Mode

Now we can test our dark mode implementation. Add the `DarkModeToggle` component to your Storybook stories and adjust its positioning according to your UI design:

```javascript
import React from 'react';
import DarkModeToggle from './DarkModeToggle';

export default {
    title: 'Components/DarkModeToggle',
    component: DarkModeToggle,
};

const Template = (args) => <DarkModeToggle {...args} />;

export const Default = Template.bind({});
Default.args = {};
```

Once the Storybook server restarts, you will see the dark mode toggle component. Clicking on it should switch your Storybook preview to dark mode!

## Conclusion

Implementing dark mode with JavaScript and Storybook is a straightforward process that allows you to provide a visually appealing user experience. By following the steps outlined above, you can easily incorporate dark mode into your Storybook project. Have fun building with dark mode! #storybook #javascript #darkmode