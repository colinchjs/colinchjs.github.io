---
layout: post
title: "Using the Progress component in Chakra UI"
description: " "
date: 2023-09-25
tags: [react, chakraui]
comments: true
share: true
---

Chakra UI is a popular React component library that provides a set of accessible and customizable UI components. One of the components Chakra UI provides is the Progress component, which allows you to display linear progress bars on your web application. In this blog post, we will explore how to use the Progress component in Chakra UI.

## Installation

To start using Chakra UI and the Progress component in your React project, you need to install the required dependencies.

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Importing the Progress Component

Once you have Chakra UI installed, you can import the Progress component into your React component.

```javascript
import { Progress } from "@chakra-ui/react";
```

## Basic Usage

The Progress component in Chakra UI allows you to easily create a linear progress bar by specifying the `value` prop, which represents the progress value as a percentage.

```jsx
<Progress value={60} />
```

You can also customize the appearance of the progress bar by using the `colorScheme` prop. This prop accepts a color scheme defined in the Chakra UI theme. For example, you can use the "teal" color scheme like this:

```jsx
<Progress value={80} colorScheme="teal" />
```

## Controlled Progress

In addition to the basic usage, you can also control the progress dynamically by using the `value` prop as a state variable.

```jsx
import { useState } from "react";

function MyProgress() {
  const [progressValue, setProgressValue] = useState(0);

  const handleButtonClick = () => {
    setProgressValue((prevValue) => prevValue + 10);
  };

  return (
    <>
      <Button onClick={handleButtonClick}>Increase Progress</Button>
      <Progress value={progressValue} />
    </>
  );
}
```

## Conclusion

Using the Progress component in Chakra UI is a straightforward way to add visually appealing and accessible progress bars to your React application. By following the basic usage and exploring its customization options, you can create progress bars that match your application's design and functionality.

#react #chakraui