---
layout: post
title: "Exploring different output formats supported by Rollup.js – CJS, ESM, UMD, and more"
description: " "
date: 2023-09-18
tags: [rollup]
comments: true
share: true
---

When you develop JavaScript applications with [Rollup.js](https://rollupjs.org/), you have the flexibility to choose from various output formats based on your project's requirements. In this blog post, we will explore the different output formats supported by Rollup.js, including CommonJS (CJS), ECMAScript Modules (ESM), Universal Module Definition (UMD), and more.

## CommonJS (CJS)
CommonJS (CJS) is a module format that is primarily used in Node.js applications. It allows you to import and export modules using `require` and `module.exports` syntax respectively. When targeting CJS output format in Rollup.js, you get a bundle that is compatible with Node.js and other systems supporting CommonJS.

To generate a CJS bundle using Rollup.js, add the following configuration in your `rollup.config.js` file:
```javascript
export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.cjs.js',
    format: 'cjs'
  }
}
```

## ECMAScript Modules (ESM)
ECMAScript Modules (ESM) is the official standard for JavaScript modules. It provides a syntax for importing and exporting modules using `import` and `export` statements. ESM is supported by modern browsers and can also be used in Node.js applications with the `--experimental-modules` flag.

To generate an ESM bundle using Rollup.js, use the following configuration:
```javascript
export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.esm.js',
    format: 'esm'
  }
}
```

## Universal Module Definition (UMD)
Universal Module Definition (UMD) is a format that allows your modules to be used in a variety of environments including browsers (as global variables), CommonJS, and AMD. UMD bundles provide compatibility with both AMD and CommonJS module systems, as well as being able to be included directly in the browser as a global variable.

To generate a UMD bundle using Rollup.js, add the following configuration:
```javascript
export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.umd.js',
    format: 'umd',
    name: 'MyLibrary'
  }
}
```
In the above configuration, replace `'MyLibrary'` with the appropriate name for your library.

## Other Output Formats
Apart from CJS, ESM, and UMD, Rollup.js also supports other output formats such as AMD (Asynchronous Module Definition), IIFE (Immediately Invoked Function Expression), and System.

To specify these formats, modify the `format` option in the Rollup.js configuration accordingly.

## Conclusion
Rollup.js provides flexibility in choosing the appropriate output format for your JavaScript applications. Whether you are targeting Node.js, modern browsers, or a wide range of environments, Rollup.js has got you covered with its support for various output formats like CJS, ESM, UMD, and more. By selecting the right format, you can optimize the performance and compatibility of your application or library.

#rollup #javascript #modules