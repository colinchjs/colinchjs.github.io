---
layout: post
title: "Execution context in JavaScript"
description: " "
date: 2023-09-26
tags: [JavaScript, ExecutionContext]
comments: true
share: true
---

In JavaScript, the concept of execution context plays a crucial role in understanding how code is executed. When code is run in a JavaScript environment, it is executed within an execution context. An execution context is a container that holds all the necessary information for the code to be executed.

## Types of Execution Context

There are three main types of execution context in JavaScript:

1. Global Execution Context: The global execution context represents the default context that is created when the JavaScript engine starts running the code. It is the outermost context. All the variables and functions declared outside of any function are part of the global execution context. 

Example:

```javascript
var name = "John";

function sayHello() {
  console.log("Hello, " + name);
}

sayHello(); // Output: Hello, John
```

In the above example, the variable `name` and the function `sayHello` are part of the global execution context. They can be accessed from anywhere in the code.

2. Function Execution Context: Whenever a function is invoked in JavaScript, a new execution context is created for that function. Each function call has its own execution context which includes local variables, function arguments, and a reference to the outer environment (lexical environment).

Example:

```javascript
function addNumbers(a, b) {
  var sum = a + b;
  return sum;
}

var result = addNumbers(5, 10);
console.log(result); // Output: 15
```

In the above example, each time the `addNumbers` function is called, a new execution context is created with its own local variable `sum`. The execution context is destroyed once the function finishes executing.

3. Eval Execution Context: The eval() function in JavaScript creates an execution context known as eval execution context. When code is evaluated using eval(), a new execution context is created and the code is executed within this context.

## Execution Context Stack

JavaScript maintains a stack data structure known as the Execution Context Stack or call stack. Whenever a function is called, its execution context is pushed onto the stack. The execution context at the top of the stack is the one currently being executed. Once a function finishes executing, its execution context is popped from the stack and the control goes back to the previous execution context in the stack.

Understanding execution context and the call stack is essential in debugging JavaScript code and understanding the flow of execution.

#JavaScript #ExecutionContext