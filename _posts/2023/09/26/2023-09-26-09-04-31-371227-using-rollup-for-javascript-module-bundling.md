---
layout: post
title: "Using Rollup for JavaScript module bundling"
description: " "
date: 2023-09-26
tags: [babel)]
comments: true
share: true
---

If you are working on a JavaScript project that requires bundling modules, you may come across [Rollup](https://rollupjs.org/). Rollup is a popular module bundler that optimizes your code for production by combining multiple modules into a single file. In this blog post, we will explore how to use Rollup to bundle your JavaScript modules.

## Getting Started with Rollup

To begin using Rollup, you need to have [Node.js](https://nodejs.org/) installed on your machine. Once Node.js is set up, open your terminal and navigate to the project directory.

First, initialize a new Node.js project by running the following command:

```bash
npm init -y
```

Next, install Rollup as a development dependency using npm:

```bash
npm install --save-dev rollup
```

## Creating a Basic Configuration

After installing Rollup, you need to create a configuration file, typically named `rollup.config.js`, at the root of your project directory. This file will define how Rollup bundles your modules.

Here's an example of a basic `rollup.config.js`:

```javascript
export default {
  input: 'src/main.js',
  output: {
    file: 'dist/bundle.js',
    format: 'cjs',
  },
}
```

In this configuration, we specify the input file (`src/main.js`) and the output file (`dist/bundle.js`). We also set the output format to CommonJS (`cjs`), but you can choose other formats like ES module or UMD according to your project's needs.

## Bundling Modules with Rollup

To bundle your JavaScript modules using Rollup, open your terminal and run the following command:

```bash
npx rollup -c rollup.config.js
```

This command will use the `rollup.config.js` file to bundle your modules and generate the output file specified in the configuration.

By default, Rollup uses the ES module syntax for importing and exporting modules. You can leverage plugins to transform your code or handle different module formats. For example, you can use the [Babel plugin](https://rollupjs.org/guide/en/#babel) to transpile your code for older browser support.

## Conclusion

Rollup simplifies the process of bundling JavaScript modules for your projects. With its easy configuration and powerful optimization features, it is a great choice for optimizing your code for production. Give Rollup a try and see how it can improve your JavaScript bundling workflow.

#JavaScript #Rollup