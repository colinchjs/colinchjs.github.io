---
layout: post
title: "Parameters in JavaScript Functions"
description: " "
date: 2023-09-20
tags: [JavaScript, Functions]
comments: true
share: true
---

To define a parameter in a JavaScript function, we simply include it within the parentheses following the function name. Let's take a look at a basic example:

```javascript
function greet(name) {
  console.log("Hello, " + name + "!");
}

greet("John");
```

In the above example, we define a function called `greet` that takes a single parameter `name`. Inside the function body, we use the `console.log` function to display a personalized greeting to the provided name. When we call the `greet` function with the argument `"John"`, it will output `Hello, John!`.

We can also define multiple parameters in a JavaScript function by separating them with commas:

```javascript
function addNumbers(num1, num2) {
  return num1 + num2;
}

console.log(addNumbers(5, 10));
```

In the above example, we define a function `addNumbers` that takes two parameters `num1` and `num2`. Inside the function, we use the `return` keyword to specify that the result of adding `num1` and `num2` should be returned. When we call the `addNumbers` function with the arguments `5` and `10`, it will output `15` to the console.

Parameters can also have default values, which are used when the arguments are not provided:

```javascript
function incrementNumber(num, increment = 1) {
  return num + increment;
}

console.log(incrementNumber(5)); // Outputs 6
console.log(incrementNumber(10, 5)); // Outputs 15
```

In the above example, we define a function `incrementNumber` with two parameters `num` and `increment`. The `increment` parameter has a default value of `1`, so if we call the function without providing a second argument, it will use the default value. When we call the `incrementNumber` function with the argument `5`, it will output `6`. Similarly, when we provide `10` and `5` as arguments, it will output `15`.

Using parameters in JavaScript functions allows us to write reusable code that can adapt to different input values. By leveraging the power of parameters, we can make our functions more flexible and versatile, improving the overall functionality of our JavaScript applications.

#JavaScript #Functions