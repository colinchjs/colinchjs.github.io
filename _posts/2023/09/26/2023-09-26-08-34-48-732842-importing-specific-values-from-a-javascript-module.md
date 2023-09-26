---
layout: post
title: "Importing specific values from a JavaScript module"
description: " "
date: 2023-09-26
tags: [JavaScript, Modules]
comments: true
share: true
---

To begin, let's suppose we have a module named `math.js` that contains various mathematical functions:

```javascript
// math.js
export function add(a, b) {
  return a + b;
}

export function subtract(a, b) {
  return a - b;
}

export const PI = 3.14159;
```

Now, let's say we only want to import the `add` and `PI` values from the `math.js` module into our current file. We can achieve this using the `import` statement.

```javascript
// main.js
import { add, PI } from './math.js';

console.log(add(5, 3));  // Output: 8
console.log(PI);        // Output: 3.14159
```

In the above code, we use destructuring assignment to import only the `add` and `PI` values from the `math.js` module. The `import` statement specifies the names of the values we want to import within curly braces `{}`.

Now, when we run the `main.js` file, it will import the `add` and `PI` values and allow us to use them in our code.

This approach has a few advantages. First, it enables us to only import the specific values we need, reducing the amount of code we have to load into memory. Second, it improves code readability, as we know exactly which values are being imported.

In conclusion, importing specific values from a JavaScript module is quite straightforward using the `import` statement. By only importing the values we need, we can keep our code efficient and easy to understand. Give it a try in your own projects and see how it simplifies your codebase!

#JavaScript #Modules