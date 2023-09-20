---
layout: post
title: "Method Chaining in JavaScript Functions"
description: " "
date: 2023-09-20
tags: [javascript, method]
comments: true
share: true
---

In JavaScript, method chaining allows you to call multiple methods on an object in a concise and readable manner. With method chaining, you can perform a series of operations on an object without having to repeatedly write the object name.

Here's an example that demonstrates method chaining in JavaScript functions:

```javascript
class Calculator {
  constructor(value = 0) {
    this.value = value;
  }

  add(num) {
    this.value += num;
    return this; // return the current object
  }

  subtract(num) {
    this.value -= num;
    return this;
  }

  multiply(num) {
    this.value *= num;
    return this;
  }

  divide(num) {
    this.value /= num;
    return this;
  }

  clear() {
    this.value = 0;
    return this;
  }
}

const calculator = new Calculator();
const result = calculator
  .add(5)
  .multiply(2)
  .subtract(3)
  .divide(4)
  .clear()
  .add(10)
  .subtract(2)
  .value;

console.log(result); // Output: 8
```

In the example above, we have a `Calculator` class with various methods such as `add()`, `subtract()`, `multiply()`, `divide()`, and `clear()`. Each method modifies the value stored in the `Calculator` object and returns the object itself using the `return this` statement.

By chaining these methods together, we can perform a sequence of calculations in a single line of code. In the end, we get the updated value of the calculator using the `value` property.

Method chaining is commonly used in JavaScript libraries and frameworks to provide a more fluent and expressive API. It allows for more readable code and reduces the need to create temporary variables.

#javascript #method-chaining