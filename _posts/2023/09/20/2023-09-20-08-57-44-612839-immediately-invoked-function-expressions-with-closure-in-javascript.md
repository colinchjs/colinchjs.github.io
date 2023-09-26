---
layout: post
title: "Immediately Invoked Function Expressions with Closure in JavaScript"
description: " "
date: 2023-09-20
tags: [Closures]
comments: true
share: true
---

Immediately Invoked Function Expressions (IIFEs) are a popular JavaScript pattern that allows you to execute a function immediately after defining it. This can be useful when you want to encapsulate code and prevent variables from polluting the global namespace. When combined with closures, IIFEs become even more powerful.

## What is a closure?

In JavaScript, a closure is created when an inner function has access to variables from its outer function, even after the outer function has finished executing. This means that the inner function "remembers" the environment in which it was created, including any variables that were in scope at the time.

```javascript
function outer() {
  let x = 10;

  function inner() {
    console.log(x);
  }

  return inner;
}

const closure = outer();
closure(); // Output: 10
```

In the example above, the `inner` function is returned from the `outer` function and assigned to the `closure` variable. When `closure` is invoked, it still has access to the `x` variable from the `outer` function, even though `outer` has already finished executing. This is the power of closures.

## Combining IIFEs and closures

IIFEs and closures can be combined to create self-contained modules or to achieve other specific functionality. By wrapping a function expression in parentheses and immediately invoking it, we can create a closure that maintains its own private variables.

```javascript
const module = (function () {
  let count = 0;

  function increment() {
    count++;
    console.log(count);
  }

  function decrement() {
    count--;
    console.log(count);
  }

  return {
    increment: increment,
    decrement: decrement
  };
})();

module.increment(); // Output: 1
module.increment(); // Output: 2
module.decrement(); // Output: 1
```

In the example above, the IIFE immediately invokes the anonymous function, creating a closure that encapsulates the `count` variable and the `increment` and `decrement` functions. The returned object allows us to access and manipulate the `count` variable through the `increment` and `decrement` methods, while keeping it hidden from the global scope.

## Conclusion

Using Immediately Invoked Function Expressions with closures is a powerful technique in JavaScript. It helps create self-contained modules, prevents global namespace pollution, and allows for better encapsulation of code. By understanding and utilizing this pattern, you can write cleaner and more maintainable JavaScript code.

#JavaScript #Closures #IIFE