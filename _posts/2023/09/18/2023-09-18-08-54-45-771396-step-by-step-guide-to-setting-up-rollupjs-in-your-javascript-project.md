---
layout: post
title: "Step-by-step guide to setting up Rollup.js in your JavaScript project"
description: " "
date: 2023-09-18
tags: [Rollup, JavaScript]
comments: true
share: true
---

### Step 1: Create a new JavaScript project

First, make sure you have Node.js installed on your machine. Open your terminal or command prompt and navigate to the directory where you want to create your new project. Run the following command to initialize a new npm package:

```bash
npm init -y
```

This will create a new `package.json` file in your project directory.

### Step 2: Install Rollup.js and its plugins

Next, let's install Rollup.js and some essential plugins. Run the following command to install them as dev dependencies:

```bash
npm install rollup rollup-plugin-node-resolve rollup-plugin-commonjs --save-dev
```

The `rollup` package is the main Rollup.js bundle, while `rollup-plugin-node-resolve` and `rollup-plugin-commonjs` are plugins that help Rollup.js handle modules from node_modules.

### Step 3: Create a Rollup config file

In order to customize the Rollup.js configuration for your project, you need to create a `rollup.config.js` file in the root of your project directory. Open your favorite text editor and create this file with the following content:

```javascript
import resolve from 'rollup-plugin-node-resolve';
import commonjs from 'rollup-plugin-commonjs';

export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.js',
    format: 'umd',
  },
  plugins: [
    resolve(),
    commonjs(),
  ],
};
```

In this config, we've specified the entry point of our application as `src/index.js` and the output bundle file as `dist/bundle.js`. The format is set to `umd` (Universal Module Definition) which can be used in both browser and Node.js environments. The `resolve` and `commonjs` plugins are added to handle the resolution and bundling of external modules.

### Step 4: Create your JavaScript source code

Now, create a `src` directory in your project and add your JavaScript source files. You can structure your code however you like, but make sure to have an entry point file that imports and exports the necessary modules.

### Step 5: Build your Rollup bundle

To build your Rollup bundle, simply run the following command in your terminal:

```bash
npx rollup -c
```

This will execute Rollup.js using the configuration file we created earlier.

### Step 6: Test your bundled code

Finally, you can test your bundled code by opening the generated `dist/bundle.js` file in a browser or by importing it into your Node.js application. Make sure to include the bundle file in your HTML or JavaScript code accordingly.

Congratulations! You have successfully set up Rollup.js in your JavaScript project.

#Rollup #JavaScript