---
layout: post
title: "Creating a range slider component with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

## Getting Started

Before we begin, make sure you have Chakra UI installed in your project. If you haven't, you can install it by running the following command:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Creating the Range Slider Component

First, let's create a new file called `RangeSlider.js` and import the necessary dependencies:

```jsx
import React from 'react';
import { Box, Slider, SliderTrack, SliderFilledTrack, SliderThumb } from '@chakra-ui/react';
```

Next, we can define our `RangeSlider` component:

```jsx
const RangeSlider = () => {
  const handleChange = (value) => {
    // Handle the value change here
  };

  return (
    <Box width="300px">
      <Slider defaultValue={50} min={0} max={100} onChange={handleChange}>
        <SliderTrack>
          <SliderFilledTrack />
        </SliderTrack>
        <SliderThumb />
      </Slider>
    </Box>
  );
};

export default RangeSlider;
```

In the `RangeSlider` component, we use the `Slider` component from Chakra UI to create the slider. We provide a default value, minimum value, and maximum value using the `defaultValue`, `min`, and `max` props.

To visualize the range on the slider, we wrap the `SliderFilledTrack` component inside a `SliderTrack` component. The `SliderThumb` component represents the draggable thumb of the slider.

Finally, we can use the `Box` component from Chakra UI to provide a fixed width to our slider.

## Using the Range Slider Component

To use the `RangeSlider` component in your application, import it into your desired file and include it in your JSX:

```jsx
import React from 'react';
import RangeSlider from './RangeSlider';

const App = () => {
  return (
    <div>
      <h1>Range Slider Example</h1>
      <RangeSlider />
    </div>
  );
};

export default App;
```

## Conclusion

In this tutorial, we learned how to create a range slider component with Chakra UI. We explored the basic structure of the component and how to use it in your React application. Range sliders are a versatile UI element that can be used in a variety of scenarios, such as selecting a price range or filtering data. With Chakra UI, creating and customizing these components becomes a breeze. Happy coding!

#ChakraUI #React