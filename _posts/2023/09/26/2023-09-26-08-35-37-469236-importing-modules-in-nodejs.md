---
layout: post
title: "Importing modules in Node.js"
description: " "
date: 2023-09-26
tags: [NodeJS, Modules]
comments: true
share: true
---

In Node.js, modules are used to organize code into reusable units. They allow you to split your program into separate files, making it easier to maintain and collaborate with others. In this blog post, we will explore different ways of importing modules in Node.js.

#### 1. Using the `require` function

Node.js provides a built-in `require` function that allows you to import modules. This function takes the file path or module name as a parameter and returns the exported module.

```javascript
const myModule = require('./myModule'); // relative path
const lodash = require('lodash'); // module name
```

#### 2. Importing Named Exports

When a module exports multiple values, you can import specific values using destructuring assignment.

```javascript
const { firstName, lastName } = require('./person'); // import specific values
```

#### 3. Importing Default Exports

Modules can also have a default export, which is the primary value exported from the module. To import the default export, use the following syntax:

```javascript
const defaultExport = require('./myModule').default; // import default export
```

#### 4. ES6 `import` statement

Starting from Node.js v13 and with the `"type": "module"` flag enabled, you can use the ES6 `import` statement to import modules. This requires you to use `.mjs` file extension instead of `.js`.

```javascript
import myModule from './myModule.mjs';
```

Note that when using the `import` statement, you can only import default exports. Named exports are not supported.

---

Importing modules in Node.js is an essential concept that allows you to organize and reuse your code. Whether you use the `require` function or the ES6 `import` statement, understanding how modules work is crucial for building scalable and maintainable Node.js applications.

#NodeJS #Modules