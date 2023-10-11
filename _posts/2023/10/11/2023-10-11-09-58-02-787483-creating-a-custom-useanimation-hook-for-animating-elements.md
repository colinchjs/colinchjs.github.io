---
layout: post
title: "Creating a custom useAnimation hook for animating elements"
description: " "
date: 2023-10-11
tags: [webdevelopment, reactjs]
comments: true
share: true
---

In this tutorial, we'll explore how to create a custom React Hook called `useAnimation` that allows us to easily animate elements in our web applications. By the end, you'll have a reusable hook that you can use in different projects to bring your UI to life.

## Table of Contents
- [Introduction](#introduction)
- [Setting up the Project](#setting-up-the-project)
- [Creating the `useAnimation` Hook](#creating-the-useanimation-hook)
- [Animating Elements](#animating-elements)
- [Conclusion](#conclusion)

## Introduction

Animations play a crucial role in enhancing the user experience of a web application. With CSS animations, we can bring elements to life, making our UI more engaging and interactive. However, managing animations using CSS alone can become complex as the number of animations increases. That's where a custom `useAnimation` Hook can come in handy.

## Setting up the Project

Before we dive into implementing the `useAnimation` Hook, let's initialize a new React project.

Open your terminal and run the following command:

```shell
npx create-react-app use-animation-hook
```

Once the project is created, navigate to the project folder:

```shell
cd use-animation-hook
```

Now, let's install some dependencies required for our project:

```shell
npm install styled-components
npm install framer-motion
```

## Creating the `useAnimation` Hook

In the `src` folder, create a new file called `useAnimation.js`. This file will contain our custom `useAnimation` Hook.

```jsx
import { useEffect, useRef } from 'react';
import { useAnimation as useFramerMotionAnimation } from 'framer-motion';

const useAnimation = () => {
  const controlsRef = useRef(null);
  const controls = useFramerMotionAnimation();

  useEffect(() => {
    controlsRef.current = controls;
  }, [controls]);

  return controlsRef.current;
};

export default useAnimation;
```

In the above code, we import the necessary dependencies and define our `useAnimation` Hook. Inside the Hook, we use the `useFramerMotionAnimation` from `framer-motion` to create an animation control.

## Animating Elements

Now that we have our `useAnimation` Hook ready, let's use it to animate a simple element. In the `App.js` file, let's add the following code:

```jsx
import React from 'react';
import styled from 'styled-components';
import { motion } from 'framer-motion';
import useAnimation from './useAnimation';

const Box = styled(motion.div)`
  width: 200px;
  height: 200px;
  background-color: coral;
`;

const App = () => {
  const animationControls = useAnimation();

  return (
    <Box
      animate={animationControls}
      initial={{ opacity: 0, scale: 0 }}
      whileHover={{ scale: 1.2 }}
      whileTap={{ scale: 0.8 }}
    />
  );
};

export default App;
```

In the above code, we import the necessary dependencies, including our `useAnimation` Hook. We then define a simple `Box` component that uses the `motion.div` component from `framer-motion`. We pass the `animationControls` to the `animate` prop of the `Box` component, which will control the animation.

We set the initial styles of the `Box` component to have 0 opacity and scale, and define different animation states for when the user hovers over or taps on the box.

## Conclusion

In this tutorial, we learned how to create a custom `useAnimation` Hook using React. We explored how to set up a basic React project, install the necessary dependencies, and use the `useAnimation` Hook to animate elements using CSS animations in our web applications.

By encapsulating the logic of managing animations in a reusable Hook, we can easily animate elements across different components and projects. This not only makes our code more maintainable but also allows us to quickly iterate on our UI/UX designs.

Feel free to customize the `useAnimation` Hook to suit your specific animation needs and explore more advanced animation techniques with `framer-motion`.

Happy animating! #webdevelopment #reactjs