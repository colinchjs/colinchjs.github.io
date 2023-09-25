---
layout: post
title: "Using the Checkbox component in Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

To get started, make sure you have installed Chakra UI in your React project. You can do this by running the following command:

```
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Now let's create a basic example of using the Checkbox component in Chakra UI:

```jsx
import React, { useState } from 'react';
import { Checkbox } from '@chakra-ui/react';

function CheckboxExample() {
  const [isChecked, setIsChecked] = useState(false);

  const handleCheckboxChange = () => {
    setIsChecked(!isChecked);
  };

  return (
    <Checkbox
      isChecked={isChecked}
      onChange={handleCheckboxChange}
    >
      I agree to the terms and conditions
    </Checkbox>
  );
}

export default CheckboxExample;
```

In the code snippet above, we import the Checkbox component from `@chakra-ui/react`. We then define a functional component called `CheckboxExample` that contains a state variable `isChecked` and a function `handleCheckboxChange` to handle the checkbox state change.

In the `return` statement, we render the Checkbox component and pass the `isChecked` state and `handleCheckboxChange` function as props. The label text "I agree to the terms and conditions" is placed inside the Checkbox component.

Once a user interacts with the Checkbox component, the `handleCheckboxChange` function will toggle the value of `isChecked`, which will trigger a re-render and update the checkbox's visual state accordingly.

Using the Checkbox component in Chakra UI is that simple! You can further customize the appearance and behavior of the Checkbox component by passing additional props and using Chakra UI's style system.

In conclusion, the Checkbox component in Chakra UI is a powerful and convenient tool for implementing checkbox functionality in your React applications. With its accessibility features and customization options, it's a reliable choice for handling user input. Give it a try and make your checkboxes shine!

#React #ChakraUI