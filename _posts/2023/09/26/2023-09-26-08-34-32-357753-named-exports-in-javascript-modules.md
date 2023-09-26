---
layout: post
title: "Named exports in JavaScript modules"
description: " "
date: 2023-09-26
tags: [Modules]
comments: true
share: true
---

To define named exports in a JavaScript module, we use the `export` keyword followed by the `name` of the entity we want to export. Let's look at an example:

```javascript
// mathUtils.js

export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
export const multiply = (a, b) => a * b;
export const divide = (a, b) => a / b;
```

In the above code, we have defined four named exports: `add`, `subtract`, `multiply`, and `divide`. These are functions that perform basic mathematical operations.

To import these exports in another JavaScript file, we use the `import` keyword followed by the `name` of the exported entity, enclosed in curly braces `{}`. Here's how we can import and use these named exports:

```javascript
// main.js

import { add, subtract, multiply, divide } from './mathUtils.js';

console.log(add(5, 3)); // Output: 8
console.log(subtract(10, 4)); // Output: 6
console.log(multiply(2, 6)); // Output: 12
console.log(divide(15, 3)); // Output: 5
```

In the above code, we import the named exports `add`, `subtract`, `multiply`, and `divide` from the `mathUtils.js` module using the relative path `'./mathUtils.js'`. We can then use these functions in our `main.js` file.

Alternatively, we can use the `*` symbol to import all named exports as properties of a single object. Here's how the import statement would look:

```javascript
// main.js

import * as mathUtils from './mathUtils.js';

console.log(mathUtils.add(5, 3)); // Output: 8
console.log(mathUtils.subtract(10, 4)); // Output: 6
console.log(mathUtils.multiply(2, 6)); // Output: 12
console.log(mathUtils.divide(15, 3)); // Output: 5
```

In the above code, we import all the named exports from `mathUtils.js` and assign them to the `mathUtils` object. We can then access each export using dot notation.

Named exports provide great flexibility when working with JavaScript modules. By exporting specific entities and selectively importing them, we can keep our code modular, maintainable, and reusable.

#JavaScript #Modules