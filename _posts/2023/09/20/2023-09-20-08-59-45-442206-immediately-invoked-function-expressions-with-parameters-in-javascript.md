---
layout: post
title: "Immediately Invoked Function Expressions with Parameters in JavaScript"
description: " "
date: 2023-09-20
tags: [JavaScript, IIFE]
comments: true
share: true
---

In JavaScript, an **Immediately Invoked Function Expression (IIFE)** is a function that is executed immediately after it is defined. This pattern is often used to create a private scope and avoid polluting the global namespace.

However, what if we want to pass **parameters** to an IIFE? Can we still achieve the benefits of encapsulation while also providing custom values to the function?

Yes, we can! We can pass parameters to an IIFE by simply wrapping it in parentheses and immediately invoking it.

Let's see an example:

```javascript
(function(parameter1, parameter2) {
  // code using the parameters
})(value1, value2);
```

In this example, we define an anonymous function with two parameters `parameter1` and `parameter2`. Then, we immediately invoke it **and pass the values `value1` and `value2`** as arguments.

This allows us to create a private scope inside the function where the parameters become local variables. The function can then utilize these values and perform any necessary computations or actions.

By using this pattern, we can prevent the variables defined within the IIFE from conflicting with other variables in the global scope. This helps to create modular and reusable code.

Remember to always use meaningful names for the parameters and ensure that the values passed to the function match the expected data types and order.

In conclusion, when using **Immediately Invoked Function Expressions in JavaScript**, we can pass parameters and create a private scope that encapsulates the variables inside the function. This helps to prevent namespace collisions and promotes cleaner code organization.

#JavaScript #IIFE