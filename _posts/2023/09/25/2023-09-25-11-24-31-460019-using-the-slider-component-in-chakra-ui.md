---
layout: post
title: "Using the Slider component in Chakra UI"
description: " "
date: 2023-09-25
tags: [chakraui, react]
comments: true
share: true
---

In this tutorial, we will explore how to use the Slider component in Chakra UI, a popular UI component library for React. The Slider component allows users to select a value from a range by dragging a slider handle.

To begin, make sure you have Chakra UI installed in your React project. If you haven't installed it yet, you can do so by running the following command:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Once you have Chakra UI installed, you can import the Slider component in your React component like this:

```jsx
import { Slider, SliderTrack, SliderFilledTrack, SliderThumb } from '@chakra-ui/react';
```

Now, let's add the Slider component to your React component's render function:

```jsx
function MySliderComponent() {
  return (
    <Slider defaultValue={50} min={0} max={100} onChange={(value) => console.log(value)}>
      <SliderTrack bg="gray.100">
        <SliderFilledTrack bg="teal.500" />
        <SliderThumb bg="teal.500" boxShadow="lg" boxSize={6} />
      </SliderTrack>
    </Slider>
  );
}
```

In the code above, we create a Slider component with a default value of 50, a minimum value of 0, and a maximum value of 100. When the value of the slider changes, the `onChange` callback will be called with the new value.

We customize the appearance of the Slider component by adding child components, such as the SliderTrack, SliderFilledTrack, and SliderThumb. Here, we set the background color of the SliderTrack to "gray.100", the background color of the SliderFilledTrack to "teal.500", and the background color of the SliderThumb to "teal.500". We also add a boxShadow and set the boxSize of the SliderThumb to 6 for some additional styling.

That's it! You now have a working Slider component in your Chakra UI application. You can further customize the Slider component by exploring the various props and styling options available in the Chakra UI documentation.

Happy coding! #chakraui #react