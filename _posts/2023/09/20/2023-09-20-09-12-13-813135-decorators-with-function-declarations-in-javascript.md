---
layout: post
title: "Decorators with Function Declarations in JavaScript"
description: " "
date: 2023-09-20
tags: [JavaScript, Decorators]
comments: true
share: true
---

In JavaScript, a decorator is a higher-order function that can modify the behavior of another function or object. It allows you to add new functionalities or change the existing behavior of functions without modifying their source code. Decorators are widely used in JavaScript frameworks and libraries to enhance the functionality of classes, methods, or properties.

Decorators can be used with both function declarations and function expressions. In this blog post, we will focus on decorators with function declarations in JavaScript.

## Creating a Decorator

To create a decorator, we need to define a higher-order function that takes a function as an argument and returns a new function that wraps the original function. The new function can perform additional tasks before or after calling the original function.

```javascript
function loggerDecorator(fn) {
  return function (...args) {
    console.log(`Calling function: ${fn.name}`);
    const result = fn(...args);
    console.log(`Function ${fn.name} executed.`);
    return result;
  };
}
```

In the above example, `loggerDecorator` is a decorator that logs the function name before and after executing it. It takes the original function as an argument and returns a new function that does the logging and calls the original function.

## Applying a Decorator

To apply a decorator to a function declaration, we simply need to wrap the function declaration with the decorator function.

```javascript
@loggerDecorator
function greet(name) {
  console.log(`Hello, ${name}!`);
}
```

In the example above, the `@loggerDecorator` syntax is used to apply the `loggerDecorator` decorator to the `greet` function.

## Testing the Decorated Function

Now, let's test the decorated `greet` function:

```javascript
greet('John');
```

When we run the above code, we will see the following output in the console:

```
Calling function: greet
Hello, John!
Function greet executed.
```

As we can see, the decorator is successfully adding the logging functionality to the `greet` function without modifying its source code.

## Conclusion

Decorators with function declarations provide a powerful way to modify the behavior of functions in JavaScript. They allow you to enhance existing functions with additional functionalities without changing their source code. Decorators are widely used in JavaScript frameworks and libraries to add cross-cutting concerns and improve code reusability.

By using decorators effectively, you can easily add new features or change the behavior of functions in a clean and modular manner. So, go ahead and start decorating your functions for added versatility and flexibility!

**#JavaScript #Decorators**