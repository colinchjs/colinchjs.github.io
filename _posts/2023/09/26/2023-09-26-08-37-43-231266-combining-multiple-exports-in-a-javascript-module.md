---
layout: post
title: "Combining multiple exports in a JavaScript module"
description: " "
date: 2023-09-26
tags: [JavaScript, Modules]
comments: true
share: true
---

When working with JavaScript modules, you may find yourself needing to export multiple functions or objects from a single file. Instead of exporting them individually, you can combine them into a single, cohesive export. This can help simplify your code and make it easier to import and use those exports in other parts of your application.

## Method 1: Exporting an object literal

One way to combine multiple exports in a JavaScript module is by exporting an **object literal**. Here's an example:

```javascript
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;

export default {
  add,
  subtract
};
```

In this example, we're exporting two functions `add` and `subtract` individually. Then, we're combining them into an object literal and exporting that object as the default export. 

With this approach, you can import the entire object and access the exported functions as properties:

```javascript
import math from './math';

console.log(math.add(5, 3)); // Outputs: 8
console.log(math.subtract(5, 3)); // Outputs: 2
```

## Method 2: Renaming exports using object destructuring

Another way to combine multiple exports is by renaming them using **object destructuring**. Here's an example:

```javascript
export const multiply = (a, b) => a * b;
export const divide = (a, b) => a / b;

export { multiply as times, divide as quotient };
```

In this example, we're exporting two functions `multiply` and `divide` individually. Then, we're using object destructuring syntax to rename those exports as `times` and `quotient`.

You can import the renamed exports directly:

```javascript
import { times, quotient } from './math';

console.log(times(5, 3)); // Outputs: 15
console.log(quotient(6, 3)); // Outputs: 2
```

## Conclusion

Combining multiple exports in a JavaScript module can help make your code more organized and concise. Whether you choose to export an object literal or use object destructuring to rename your exports, leveraging these techniques can improve the readability and maintainability of your codebase.

#JavaScript #Modules