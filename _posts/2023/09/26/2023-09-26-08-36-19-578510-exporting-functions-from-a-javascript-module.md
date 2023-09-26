---
layout: post
title: "Exporting functions from a JavaScript module"
description: " "
date: 2023-09-26
tags: [modules]
comments: true
share: true
---

## 1. Default Export
The default export is used when there is a single function or object to export from a module. It allows us to import the function with any name we choose. Here's an example of exporting a function as the default export:

```javascript
// mathUtils.js
export default function add(a, b) {
  return a + b;
}
```

To import the default export in another file, we use the `import` keyword:

```javascript
// index.js
import addNumbers from './mathUtils';

console.log(addNumbers(2, 3)); // Output: 5
```

## 2. Named Export
Named exports are used when we want to export multiple functions or objects from a module. We can export multiple entities by listing them inside curly braces. Here's an example of exporting multiple functions as named exports:

```javascript
// mathUtils.js
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

To import named exports, we need to use their specific names:

```javascript
// index.js
import { add, subtract } from './mathUtils';

console.log(add(2, 3)); // Output: 5
console.log(subtract(5, 2)); // Output: 3
```

## 3. Mixed Export
In some cases, we may want to have both default and named exports in a module. This can be achieved by combining both exports. Here's an example:

```javascript
// mathUtils.js
export default function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}
```

To import the default and named exports together, we can use a combination of import statements:

```javascript
// index.js
import addNumbers, { subtract } from './mathUtils';

console.log(addNumbers(2, 3)); // Output: 5
console.log(subtract(5, 2)); // Output: 3
```

## Conclusion
Exporting functions from a JavaScript module is a fundamental concept for code organization and reusability. By using default and named exports, we can easily share functions across different parts of an application. Whether you need to export a single function as a default export or multiple functions as named exports, JavaScript provides flexible options to suit your needs.

#javascript #modules