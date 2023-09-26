---
layout: post
title: "Understanding the import and export syntax in Rollup.js"
description: " "
date: 2023-09-18
tags: [rollupjs]
comments: true
share: true
---

## Importing Modules

To import a module into your JavaScript file with Rollup.js, you can use the `import` keyword followed by the module path. The module path can be either an absolute path or a relative path to the current file. Here's an example:

```javascript
import { foo, bar } from './myModule.js';
```

In the example above, we are importing the `foo` and `bar` named exports from the `myModule.js` file. You can also import the default export using the `default` keyword:

```javascript
import myFunction from './myModule.js';
```

Rollup.js will analyze your code and bundle the necessary modules into the final output file, eliminating any unused code by tree shaking.

## Exporting Modules

To export a module in Rollup.js, you can use the `export` keyword followed by the entities you want to export. Here are a few examples:

```javascript
export const myVariable = 'Hello, Rollup!';
```

In the example above, we are exporting a constant variable `myVariable`. You can also export functions, classes, and objects:

```javascript
export function myFunction() {
  // Function implementation
}

export class MyClass {
  // Class definition
}

export default myDefaultFunction;
```

The `export default` keyword is used to set the default export for a module. You can only have one default export per module, and it can be imported without using curly braces:

```javascript
import myDefaultFunction from './myModule.js';
```

## Conclusion

Understanding the import and export syntax in Rollup.js is crucial for building modular and maintainable JavaScript applications. With Rollup.js, you can easily import and export modules, allowing you to structure your codebase and manage dependencies effectively. Make sure to leverage the power of tree shaking to eliminate any unused code from your final bundled output.

#rollupjs #javascript