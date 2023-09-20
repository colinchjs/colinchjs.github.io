---
layout: post
title: "Function Closure vs Object Closure in JavaScript"
description: " "
date: 2023-09-20
tags: [javascript, closures]
comments: true
share: true
---

JavaScript is a versatile programming language with various features that enable developers to write clean and efficient code. Among these features are closures, which allow functions to remember and access variables from their parent scope even after the parent function has finished executing. Closures are widely used in JavaScript to create private variables and functions, encapsulate data, and create modular code.

There are two types of closures commonly used in JavaScript: function closures and object closures. Let's understand the difference between these two types and when to use each.

## Function Closures

A function closure, also known as a lexical closure, is created when a function is defined inside another function and the inner function references variables from the outer function. The inner function retains its access to the outer function's scope, even after the outer function has finished executing.

Here's an example of a function closure:

```javascript
function outerFunction() {
  var outerVariable = 'Hello,';

  function innerFunction(name) {
    console.log(outerVariable + ' ' + name);
  }

  return innerFunction;
}

var greet = outerFunction();
greet('John'); // Output: Hello, John
```

In the above code, the `innerFunction` forms a closure by referencing the `outerVariable`. Even after the `outerFunction` has completed execution and returned, the closure retains access to `outerVariable` and can use it when invoked.

Function closures are useful when you need to create private variables or encapsulate data within a function. They provide a way to create reusable functions with internal state.

## Object Closures

Object closures, also known as factory functions, are a variation of closures where functions are used to create and return a new object. These functions define private variables as properties of the returned object, allowing those variables to be accessed or manipulated only through the object's public methods.

Let's illustrate object closures with an example:

```javascript
function createCounter() {
  var count = 0;

  return {
    increment: function() {
      count++;
    },
    decrement: function() {
      count--;
    },
    getCount: function() {
      return count;
    }
  };
}

var counter = createCounter();
counter.increment();
counter.increment();
console.log(counter.getCount()); // Output: 2
```

In the above code, the `createCounter` function acts as a factory function that returns an object with three methods: `increment`, `decrement`, and `getCount`. The `count` variable is private and can only be modified or accessed through these methods.

Object closures are useful when you want to create multiple instances of an object with private data and methods.

## Conclusion

Closures are a powerful feature of JavaScript that allow functions to remember and access variables from their parent scopes. Function closures are created when a function references variables from its outer function, while object closures use factory functions to create and return objects with private data.

Understanding the difference between function closures and object closures is crucial when designing and implementing JavaScript code. Using the appropriate closure type can lead to cleaner, more modular code and help improve code organization and encapsulation.

#javascript #closures