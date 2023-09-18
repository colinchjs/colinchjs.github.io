---
layout: post
title: "Generating source maps with Rollup.js for easier debugging in the browser"
description: " "
date: 2023-09-18
tags: [Rollup, SourceMaps]
comments: true
share: true
---

Debugging JavaScript code can be challenging, especially when the code has been bundled and minified. However, with the help of **source maps**, developers can easily debug optimized code by mapping it back to its original source code. In this article, we'll explore how to generate source maps using Rollup.js, a popular JavaScript module bundler.

## What are Source Maps?

Source maps are files that contain information about the mapping between the original source code and the code that is executed in the browser. They provide a way to debug minified and bundled JavaScript code by allowing developers to see the original code structure, variable names, and even set breakpoints.

## Why Use Rollup.js for Generating Source Maps?

Rollup.js is a lightweight and efficient module bundler that is gaining popularity in the JavaScript community. It offers built-in support for generating source maps, making it a convenient choice for creating optimized bundles with easy debugging capabilities.

## Getting Started with Rollup.js and Source Maps

To start using Rollup.js for generating source maps, we need to follow a few simple steps:

1. **Install Rollup.js**: If you haven't already, you can install Rollup.js globally by running the following command in your terminal:

```
npm install -g rollup
```

2. **Create a Rollup Configuration File**: In the root of your project, create a `rollup.config.js` file. This file will contain the configuration options for Rollup.js. Here's a basic example:

```javascript
import { terser } from "rollup-plugin-terser";

export default {
  input: "src/main.js",
  output: {
    file: "dist/bundle.js",
    format: "iife",
    sourcemap: true,
  },
  plugins: [terser()],
};
```

In the above configuration, we specify the entry point for our application (`src/main.js`), the output file path (`dist/bundle.js`), the format of the bundle (`iife` stands for Immediately Invoked Function Expression), and enable source map generation by setting `sourcemap` to `true`.

3. **Install Rollup Plugins**: To enable source map generation, we need to install the `rollup-plugin-terser` plugin, which minifies and generates source maps for our code. Install it by running the following command:

```
npm install rollup-plugin-terser --save-dev
```

4. **Build the Bundle with Source Maps**: Now we can build the bundle using Rollup.js and generate the source maps. Navigate to your project's root directory in the terminal and run the following command:

```
rollup -c
```

Rollup.js will read the configuration file you created (`rollup.config.js`), bundle your code, and generate the optimized bundle along with the source map file.

## Debugging with Source Maps in the Browser

To debug the bundled code using the source map, you need to open the browser's developer tools and navigate to the "Sources" tab. You should see the original source files and can set breakpoints, inspect variables, and step through your code just like when debugging the unoptimized code.

With source maps, you can now **simplify the debugging process** when working with bundled and minified JavaScript code. Rollup.js makes it easy to generate source maps, allowing you to focus on writing clean and efficient code without sacrificing the ability to debug effectively.

#Rollup #SourceMaps