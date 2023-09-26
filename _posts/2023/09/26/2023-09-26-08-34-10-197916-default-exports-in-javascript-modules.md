---
layout: post
title: "Default exports in JavaScript modules"
description: " "
date: 2023-09-26
tags: [javascript, modules]
comments: true
share: true
---

To define a default export in a module, you can simply use the `export default` syntax followed by the value or functionality you want to export. Here's an example:

```javascript
// math.js
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

export default {
  add,
  subtract,
};
```

In the above code, we are exporting an object with two functions, `add` and `subtract`, as the default export. This syntax allows us to import both functions together in another module by simply assigning them to a variable during the import.

```javascript
// main.js
import mathFunctions from './math.js';

const result = mathFunctions.add(5, 3); // 8
```

In the `main.js` module, we import the default export from `math.js` and assign it to the `mathFunctions` variable. We can then access the `add` function directly from the `mathFunctions` object.

Alternatively, you can also import the default export and rename it to a different variable name during the import, like this:

```javascript
import { add as sum } from './math.js';

const result = sum(5, 3); // 8
```

In this example, we are importing the default export `add` from `math.js` and renaming it to `sum` during the import. This allows us to use `sum` instead of `add` in our code.

Default exports can be very useful when you have a module that primarily exports a single value or functionality. They provide a clean and straightforward way to interact with and use those exports in your JavaScript applications.

#javascript #modules