---
layout: post
title: "Using Rollup.js alongside popular CSS frameworks like Tailwind CSS and Bootstrap"
description: " "
date: 2023-09-18
tags: [webdevelopment, rollupjs]
comments: true
share: true
---

Rollup.js is a popular JavaScript module bundler that helps optimize your code and create efficient bundles for your web applications. While it is mainly used for JavaScript modules, you can also use Rollup.js to bundle your CSS files, including popular frameworks like Tailwind CSS and Bootstrap.

In this blog post, we will guide you through the process of setting up Rollup.js with Tailwind CSS and Bootstrap, so you can bundle and optimize your CSS files for your web project.

## Prerequisites

Before getting started, make sure you have the following prerequisites installed on your machine:

- [Node.js](https://nodejs.org) (version 12 or higher)
- [npm](https://www.npmjs.com/) (usually comes with Node.js)

## Step 1: Setting up a new project

Create a new folder for your project and navigate to it in your command line interface. Then, initiate a new npm project by running the following command:

```shell
npm init -y
```

This command creates a `package.json` file that will track your project's dependencies and configurations.

## Step 2: Installing the required packages

To use Rollup.js with Tailwind CSS and Bootstrap, we need to install a few packages. Run the following command to install the required packages:

```shell
npm install rollup rollup-plugin-postcss postcss-import postcss autoprefixer tailwindcss bootstrap
```

## Step 3: Configuring Rollup.js

Create a new file named `rollup.config.js` in the root of your project directory. Open the file and add the following code:

```javascript
import postcss from "rollup-plugin-postcss";
import autoprefixer from "autoprefixer";
import tailwindcss from "tailwindcss";
import resolve from "@rollup/plugin-node-resolve";

export default {
  input: "src/main.js",
  output: {
    file: "dist/bundle.js",
    format: "iife",
    sourcemap: true,
  },
  plugins: [
    resolve(),
    postcss({
      extract: true,
      minimize: true,
      plugins: [tailwindcss, autoprefixer],
    }),
  ],
};
```

This configuration file sets up Rollup.js to bundle our CSS file using PostCSS with Tailwind CSS and Bootstrap.

## Step 4: Creating a CSS entry point

In your project folder, create a new folder named `src` if not already present. Inside the `src` folder, create a new file named `main.css`. Open the file and add the following code:

```css
@import 'tailwindcss/tailwind.css';
@import 'bootstrap/dist/css/bootstrap.css';

/* Your custom CSS code goes here */
```

This file serves as our CSS entry point where we import Tailwind CSS and Bootstrap, along with any other custom CSS you want to include.

## Step 5: Building your CSS bundle

In your command line interface, run the following command to build your CSS bundle:

```shell
npx rollup -c
```

Rollup.js will use the configuration file we created earlier (`rollup.config.js`) to bundle your CSS files. The bundled CSS file will be generated in the `dist` folder with the name `bundle.js`.

## Step 6: Including the bundled CSS in your HTML

Now that we have our bundled CSS file, we need to include it in our HTML file. Add the following HTML code in your `index.html` file:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My App</title>
  <link rel="stylesheet" href="dist/bundle.css">
  <!-- Other head elements -->
</head>
<body>
  <!-- Your HTML code goes here -->
  <script src="dist/bundle.js"></script>
</body>
</html>
```

Make sure to update the paths if your `index.html` and `dist` folder are located in different places.

## Step 7: Running your project

To see your bundled CSS in action, run a local server or open your `index.html` file directly in your web browser. You should now have Tailwind CSS, Bootstrap, and your custom CSS included and applied to your web project.

Congratulations! You have successfully set up Rollup.js with Tailwind CSS and Bootstrap, optimizing and bundling your CSS files for your web project.

#webdevelopment #rollupjs #tailwindcss #bootstrap