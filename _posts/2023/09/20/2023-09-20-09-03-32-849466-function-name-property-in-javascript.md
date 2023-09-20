---
layout: post
title: "Function Name Property in JavaScript"
description: " "
date: 2023-09-20
tags: []
comments: true
share: true
---

In JavaScript, functions are first-class citizens, meaning they can be assigned to variables, passed as arguments to other functions, and even have properties of their own. One such property is the `name` property, which stores the name of the function.

## Accessing the Function Name Property

To access the `name` property of a function, you can simply use the dot notation on the function object. For example:

```javascript
function greeting() {
  console.log("Hello, world!");
}

console.log(greeting.name); // Output: greeting
```

In the above example, `greeting.name` will return the name of the function which is "greeting".

## Anonymous Functions

If a function is defined without a name, it is referred to as an anonymous function. When accessing the `name` property of an anonymous function, it will return an empty string.

```javascript
const anonymousFunc = function() {
  console.log("This is an anonymous function.");
};

console.log(anonymousFunc.name); // Output: ""
```

In the above example, `anonymousFunc.name` will return an empty string as the function is anonymous.

## Function Expressions

When using function expressions to define a function, the `name` property will still be accessible and return the name of the variable holding the function.

```javascript
const myFunction = function customName() {
  console.log("This is a function expression.");
};

console.log(myFunction.name); // Output: customName
```

In the above example, `myFunction.name` will return "customName".

## Function Declarations

For function declarations, the `name` property will return the name of the function itself.

```javascript
function sum(a, b) {
  return a + b;
}

console.log(sum.name); // Output: sum
```

In the above example, `sum.name` will return "sum".

## Conclusion

The `name` property of a function provides a convenient way to access the name of the function, making it useful for debugging and other scenarios where you need to work with function names programmatically.