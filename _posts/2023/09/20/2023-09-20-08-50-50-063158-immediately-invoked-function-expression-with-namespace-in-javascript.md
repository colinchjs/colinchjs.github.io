---
layout: post
title: "Immediately Invoked Function Expression with Namespace in JavaScript"
description: " "
date: 2023-09-20
tags: [IIFE]
comments: true
share: true
---

In JavaScript, an Immediately Invoked Function Expression (IIFE) is a self-executing anonymous function that runs as soon as it is defined. It is often used to create a new scope and encapsulate code to prevent variable name clashes or pollution of the global namespace.

Additionally, using a namespace within an IIFE can further help organize and structure your code, making it more readable and maintainable. Let's see how to implement an IIFE with a namespace in JavaScript.

```javascript
(function(namespace) {
  // Code within the IIFE goes here

  // Example function within the namespace
  function greet(name) {
    console.log(`Hello, ${name}!`);
  }

  // Adding the function to the namespace
  namespace.greet = greet;

})(window.myApp = window.myApp || {});
```

In the above example, we define an IIFE that takes a namespace object as an argument. Inside the IIFE, we can add our code, including functions, variables, and other logic.

In this case, we define a `greet` function that logs a greeting message to the console. We then add this function to the `myApp` namespace by assigning it as a property of the `namespace` object.

By using the `window.myApp = window.myApp || {}` assignment, we ensure that we use an existing `myApp` namespace if available, or create a new one if it doesn't exist. This allows us to avoid overwriting or conflicting with any pre-existing code or variables.

With this approach, we can organize our code and make it more modular. We can then access the `greet` function as `myApp.greet('John')`, calling it from other parts of our application.

Using IIFEs with namespaces helps avoid global variable pollution and provides a clean and structured way to encapsulate code within your JavaScript applications.

#JavaScript #IIFE #Namespaces