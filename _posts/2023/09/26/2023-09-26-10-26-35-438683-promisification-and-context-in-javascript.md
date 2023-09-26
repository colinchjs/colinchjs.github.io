---
layout: post
title: "Promisification and context in JavaScript"
description: " "
date: 2023-09-26
tags: [javascript, promisification]
comments: true
share: true
---

Promisification is a technique in JavaScript that allows you to convert functions with a callback-based API into functions that return a Promise. This can make your code more readable and easier to work with, especially when dealing with asynchronous operations.

Context, on the other hand, refers to the object that a function is bound to when it is invoked. In JavaScript, the context of a function can be determined by the way it is called, whether it is a regular function call or a method call on an object.

## Promisification

To promisify a function, you need to wrap it with a new function that returns a Promise. This new function should handle the success and error cases and resolve or reject the Promise accordingly.

Here's an example of promisifying a `setTimeout` function:

```javascript
function delay(ms) {
  return new Promise((resolve) => {
    setTimeout(resolve, ms);
  });
}

delay(2000).then(() => {
  console.log('Delay for 2 seconds complete');
});
```

In this example, the `delay` function returns a Promise that resolves after the specified number of milliseconds. You can then use the `.then()` method to perform actions once the delay is complete.

Promisification can be especially useful when working with APIs that use callbacks, such as making HTTP requests with `fetch` or using Node.js modules that rely on callbacks.

## Context

In JavaScript, the context of a function can be determined by how it is called. If a function is called as a method on an object, then the context (`this` keyword) refers to that object. If a function is called as a regular function, then the context is the global object (`window` in a browser or `global` in Node.js).

Here's an example to illustrate context:

```javascript
const person = {
  name: 'John',
  sayHello: function() {
    console.log(`Hello, my name is ${this.name}`);
  }
};

person.sayHello(); // Output: Hello, my name is John

const sayHelloFunc = person.sayHello;
sayHelloFunc(); // Output: Hello, my name is undefined
```

In this example, we have an object `person` with a `sayHello` method. When we call `person.sayHello()`, the `this` keyword inside the `sayHello` method refers to the `person` object, so it can access the `name` property.

However, when we assign the `person.sayHello` method to the variable `sayHelloFunc` and invoke it as a regular function, the `this` keyword refers to the global object (`window` in this case). As a result, it can't access the `name` property, and the output is `undefined`.

Understanding context is crucial when working with JavaScript, especially when working with complex objects and object-oriented programming.

#javascript #promisification #context