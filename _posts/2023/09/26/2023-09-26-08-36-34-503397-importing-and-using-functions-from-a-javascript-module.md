---
layout: post
title: "Importing and using functions from a JavaScript module"
description: " "
date: 2023-09-26
tags: []
comments: true
share: true
---

To import functions from a JavaScript module, you can use the `import` statement. Let's take a look at an example:

```javascript
import { greet, sum } from './math.js';

greet('John'); // Output: Hello, John!
console.log(sum(5, 10)); // Output: 15
```

In this example, we're importing the `greet` and `sum` functions from the `math.js` module. The `import` statement allows us to specify the specific functions we want to import, encased in curly braces `{}`. The `./math.js` indicates the relative path to the module file.

Once imported, we can use the functions as if they were defined in the current module. In the above code snippet, we call the `greet` function and pass in the name 'John', which will print 'Hello, John!' to the console. We also call the `sum` function to calculate the sum of two numbers and log the result to the console.

It's important to note that the imported functions must be exported from the module in order to be accessible outside of it. In the `math.js` module, you would typically export the functions like this:

```javascript
export function greet(name) {
  console.log(`Hello, ${name}!`);
}

export function sum(a, b) {
  return a + b;
}
```

Within the module, the `export` keyword is used to make the functions available for import in other modules.

By using JavaScript modules and importing functions, you can take advantage of code reusability and create more modular and maintainable applications.