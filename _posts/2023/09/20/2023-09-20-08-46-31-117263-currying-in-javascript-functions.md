---
layout: post
title: "Currying in JavaScript Functions"
description: " "
date: 2023-09-20
tags: [Currying]
comments: true
share: true
---

To implement currying in JavaScript, we can use a higher-order function that returns a new function for each argument passed. Here's an example:

```javascript
function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function (...moreArgs) {
        return curried.apply(this, args.concat(moreArgs));
      };
    }
  };
}
```

In this example, the `curry` function takes another function `func` as an argument. It then returns a new function `curried` that accepts any number of arguments using the rest parameter syntax `...args`.

Inside the `curried` function, we check if the number of arguments passed is greater than or equal to the expected number of arguments for `func`. If so, we invoke `func` with the provided arguments using `func.apply(this, args)`. Otherwise, we return a new function that concatenates the current arguments with the additional arguments passed, and recursively invokes `curried`.

This allows us to progressively apply arguments to the curried function one at a time. Here's an example usage:

```javascript
function add(a, b, c) {
  return a + b + c;
}

const curriedAdd = curry(add);

console.log(curriedAdd(1)(2)(3)); // Output: 6
console.log(curriedAdd(1, 2)(3)); // Output: 6
console.log(curriedAdd(1)(2, 3)); // Output: 6
```

By currying the `add` function, we can invoke it either with all arguments at once or one argument at a time. This flexibility allows for easier function composition and partial function application.

Currying can be a powerful technique in JavaScript to create more flexible and reusable functions. By breaking down a function with multiple arguments into a series of single-argument functions, we gain enhanced control over function invocation and parameter binding.

#JavaScript #Currying