---
layout: post
title: "The "arguments" Keyword in Arrow Functions in JavaScript"
description: " "
date: 2023-09-20
tags: [JavaScript, ArrowFunctions]
comments: true
share: true
---

In JavaScript, arrow functions provide a concise way to write functions. They have a syntactic shorter form compared to traditional function expressions. However, when it comes to accessing the arguments passed to a function, arrow functions behave differently.

In regular functions, the `arguments` keyword is a local variable that holds an array-like object containing all the arguments passed to the function. This is useful when the number of arguments is unknown or when we want to create functions with a variable number of parameters.

```javascript
function sum(a, b) {
    console.log(arguments);
    return a + b;
}

sum(2, 4, 6); // Output: [2, 4, 6]
```

However, when using arrow functions, the `arguments` keyword is not available. Arrow functions do not have their own `arguments` object binding. They inherit the `arguments` from the containing scope.

```javascript
const sum = (a, b) => {
    console.log(arguments); // ReferenceError: arguments is not defined
    return a + b;
}

sum(2, 4, 6);
```

If you really need to access the arguments inside an arrow function, you can do so by using the rest parameter syntax (`...args`).

```javascript
const sum = (...args) => {
    console.log(args); // Output: [2, 4, 6]
    return args.reduce((acc, curr) => acc + curr, 0);
}

sum(2, 4, 6);
```

In summary, the `arguments` keyword is not available in arrow functions, but you can use the rest parameter syntax to achieve a similar functionality. Be mindful of this difference when using arrow functions, especially when you rely on accessing arguments dynamically. 

#JavaScript #ArrowFunctions