---
layout: post
title: "Function Declaration vs Function Expression in JavaScript"
description: " "
date: 2023-09-20
tags: [JavaScript, Functions]
comments: true
share: true
---

When working with JavaScript, you may come across two ways to define a function: function declarations and function expressions. Although both methods achieve the same result – creating a reusable block of code – there are some differences between them that you should be aware of. In this article, we will delve into the distinctions between function declarations and function expressions in JavaScript.

## Function Declaration
A function declaration in JavaScript begins with the `function` keyword followed by the name of the function and a pair of parentheses (). The function body is enclosed within curly brackets {}. Here's an example of a function declaration:

```javascript
function greet(name) {
  console.log("Hello, " + name + "!");
}
```

In a function declaration, the function is hoisted to the top of its scope. This means it can be called before it is defined in the code. For example, you can call the `greet()` function before its actual declaration:

```javascript
greet("John"); // Output: Hello, John!

function greet(name) {
  console.log("Hello, " + name + "!");
}
```

## Function Expression
Unlike function declarations, function expressions involve assigning a function to a variable. The function is created as part of an expression and can be assigned to a variable, passed as an argument to another function, or returned as a result. Here's an example of a function expression:

```javascript
var greet = function(name) {
  console.log("Hello, " + name + "!");
};
```

In function expressions, the function is not hoisted like function declarations. Therefore, you cannot call the function before its definition in the code. The following code would result in an error:

```javascript
greet("John"); // Error: greet is not a function

var greet = function(name) {
  console.log("Hello, " + name + "!");
};
```

To avoid this issue, you should define the function expression before calling it:

```javascript
var greet = function(name) {
  console.log("Hello, " + name + "!");
};

greet("John"); // Output: Hello, John!
```

## Conclusion
The main difference between function declarations and function expressions lies in hoisting. Function declarations are hoisted to the top of their scope, allowing them to be called before they are defined. On the other hand, function expressions need to be defined before they can be called, as they are not subject to hoisting.

Understanding the distinctions between function declarations and function expressions can help you write cleaner, more organized JavaScript code. Whether you choose to use function declarations or function expressions largely depends on your specific use case and coding style.

#JavaScript #Functions