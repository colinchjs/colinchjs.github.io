---
layout: post
title: "Exploring tree-shaking techniques in Rollup.js for removing unused code"
description: " "
date: 2023-09-18
tags: [techblog, rollupjs]
comments: true
share: true
---

In modern web development, optimizing the size of our JavaScript bundles is a crucial step towards improving the performance of our applications. One technique that helps achieve this is tree-shaking, which involves removing the unused code from our bundles.

Rollup.js is a popular JavaScript module bundler that provides excellent support for tree-shaking. Let's explore some techniques we can use with Rollup.js to effectively eliminate unused code.

### 1. Use ES6 Modules

ES6 modules are static, meaning their imports and exports are known at compile-time. This allows Rollup.js to analyze the module dependencies and determine which code can be safely removed during the bundling process.

To take advantage of tree-shaking in Rollup.js, ensure that your codebase uses ES6 module syntax consistently. This includes using `import` and `export` statements instead of CommonJS or AMD syntax.

### 2. Mark Dependencies as Side Effects Free

By default, Rollup.js assumes that imported modules have side effects, such as modifying global objects or altering the DOM. This prevents the removal of seemingly unused code. However, if you know that specific modules have no side effects, you can *mark them as side effect free* using the `@rollup/plugin-node-resolve` plugin.

To mark a module as side effect free, add a `sideEffects` property to its package.json file:

```json
{
  "name": "my-module",
  "sideEffects": false
}
```

This tells Rollup.js that the module has no side effects, enabling more aggressive tree-shaking.

### 3. Use Pure Functions

Rollup.js can effectively remove unused functions if they are *pure functions*. Pure functions are functions whose return value depends only on their input values, without any side effects. By marking functions as pure, Rollup.js can safely remove them when they are not used.

To mark a function as pure in JavaScript, you can use the `/** @pure */` JSDoc comment or the `pure` attribute in TypeScript:

```javascript
/** @pure */
function add(a, b) {
  return a + b;
}
```

By using pure functions, you ensure that your codebase is more tree-shakeable, leading to smaller bundle sizes.

### Conclusion

Tree-shaking is an essential technique for eliminating unused code from our JavaScript bundles, leading to smaller file sizes and improved performance. Rollup.js provides excellent support for tree-shaking and offers various techniques like using ES6 modules, marking modules as side effect-free, and using pure functions.

Implementing these techniques can significantly optimize the size of your bundles and enhance the overall performance of your web applications.

#techblog #rollupjs #treeshaking