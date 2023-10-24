---
layout: post
title: "Constructor functions for math operations in JavaScript"
description: " "
date: 2023-10-24
tags: []
comments: true
share: true
---

In JavaScript, we can use constructor functions to create reusable objects that perform math operations. Constructor functions allow us to define a blueprint for creating multiple instances of objects with the same properties and methods.

## Addition Function

Let's start by creating a constructor function for addition. This function will take two numbers as parameters and provide a method to perform the addition operation.

```javascript
function Addition(num1, num2) {
  this.num1 = num1;
  this.num2 = num2;
}

Addition.prototype.calculate = function() {
  return this.num1 + this.num2;
}
```

Here, we define the `Addition` function and use the `this` keyword to assign the parameters `num1` and `num2` as properties of the object being created. The `calculate` method is added to the `Addition` prototype, which allows all instances of `Addition` to access this method.

To create an instance of the `Addition` object and perform the addition operation, we can do the following:

```javascript
const add = new Addition(5, 3);
console.log(add.calculate()); // Output: 8
```

## Subtraction Function

Similarly, we can create a constructor function for subtraction. This function will also take two numbers as parameters and provide a method to perform the subtraction operation.

```javascript
function Subtraction(num1, num2) {
  this.num1 = num1;
  this.num2 = num2;
}

Subtraction.prototype.calculate = function() {
  return this.num1 - this.num2;
}
```

Here, we define the `Subtraction` function and add the necessary properties and methods. The usage of the constructor function is similar to the addition example mentioned earlier:

```javascript
const subtract = new Subtraction(8, 2);
console.log(subtract.calculate()); // Output: 6
```

## Summary

Constructor functions can be useful in creating reusable objects for performing various mathematical operations in JavaScript. By using prototype methods, we can ensure that all instances of these objects have access to the same set of operations. This approach allows for cleaner code organization and better code reusability.

With the addition and subtraction examples provided above, you can extend the concept to create more complex math operation constructor functions.