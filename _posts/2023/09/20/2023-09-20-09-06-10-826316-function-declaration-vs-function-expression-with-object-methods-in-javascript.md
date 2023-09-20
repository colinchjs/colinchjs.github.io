---
layout: post
title: "Function Declaration vs Function Expression with Object Methods in JavaScript"
description: " "
date: 2023-09-20
tags: []
comments: true
share: true
---

In JavaScript, there are two common ways to define functions: **Function Declarations** and **Function Expressions**. When it comes to defining methods on objects, both approaches can be used. However, there are some key differences between the two. In this blog post, we will explore the differences and discuss when to use each approach.

## Function Declaration

A function declaration is the traditional way of defining a function in JavaScript. It starts with the `function` keyword, followed by the function name and a pair of parentheses for the arguments. Here's an example of a function declaration:

```javascript
function sayHello(name) {
   console.log(`Hello, ${name}!`);
}
```

When defining a method on an object using a function declaration, we can assign the function directly to a property of the object:

```javascript
const person = {
   name: "John",
   sayHello: function() {
      console.log(`Hello, ${this.name}!`);
   }
};
```

In the example above, the `sayHello` function is defined as a method on the `person` object. Notice that we use the `function` keyword and the function name `sayHello`.

## Function Expression

A function expression is another way to define a function in JavaScript. In this approach, a function is defined inside an expression, which can be assigned to a variable. Here's an example of a function expression:

```javascript
const sayHello = function(name) {
   console.log(`Hello, ${name}!`);
};
```

To define a method on an object using a function expression, we can assign the function expression to a property of the object:

```javascript
const person = {
   name: "John",
   sayHello: function() {
      console.log(`Hello, ${this.name}!`);
   }
};
```

In this example, the `sayHello` function is defined as a method on the `person` object. Notice that we use a function expression instead of a function declaration.

## Key Differences

The main difference between function declarations and function expressions lies in how they are hoisted. Function declarations are hoisted, which means they can be called before they are declared in the code. On the other hand, function expressions are not hoisted and cannot be called before they are assigned to a variable.

Another important difference is that function declarations create named functions and function expressions create anonymous functions by default. However, we can assign a name to a function expression using a variable.

## When to Use Each Approach

- **Function Declaration**: Use function declarations when you need to define a reusable function that may be called before its actual declaration in the code. Function declarations are hoisted, allowing them to be used anywhere in the code.

- **Function Expression**: Use function expressions when you need to define a function as an expression within a larger expression or assign it to a variable. Function expressions are useful when creating object methods or passing functions as arguments to other functions.

In conclusion, both function declarations and function expressions have their place in JavaScript, and each approach has its own benefits. Understanding the differences between the two will help you make informed decisions when defining functions, especially when working with object methods.