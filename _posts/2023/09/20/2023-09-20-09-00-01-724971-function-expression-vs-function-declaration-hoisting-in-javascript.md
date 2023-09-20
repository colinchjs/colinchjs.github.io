---
layout: post
title: "Function Expression vs Function Declaration Hoisting in JavaScript"
description: " "
date: 2023-09-20
tags: [javascript, hoisting]
comments: true
share: true
---

When working with JavaScript, it's essential to understand the concept of hoisting and how it affects function expressions and function declarations. Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase, before the code is executed.

## Function Declaration Hoisting

Function declarations are hoisted in JavaScript, meaning they can be called before they are defined in the code. This allows us to call a function even before it appears in the code, as long as it's defined within the same scope.

```javascript
myFunction(); // Output: "Hello, world!"

function myFunction() {
  console.log("Hello, world!");
}
```

In the example above, we can see that the `myFunction` is called before its declaration, yet it still produces the expected output. This is because function declarations are hoisted to the top of their containing scope during compilation.

## Function Expression

On the other hand, function expressions are not hoisted in the same way as function declarations. Function expressions are created by assigning a function to a variable. Since variable assignments are not hoisted, we must define the function expression before calling it.

```javascript
myFunction(); // Output: TypeError: myFunction is not a function

var myFunction = function() {
  console.log("Hello, world!");
};
```

In this example, we encounter a `TypeError` because the function expression `myFunction` is assigned to a variable after it is called. Unlike function declarations, function expressions must be defined before they are called.

## Conclusion

In summary, function declarations are hoisted, allowing us to call them before their actual declaration in the code. However, function expressions are not hoisted in the same way, meaning they must be defined before they are called.

Understanding the differences between function expressions and function declarations and how they are hoisted in JavaScript is crucial to avoid unexpected behavior in your code.

#javascript #hoisting