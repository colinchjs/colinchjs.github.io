---
layout: post
title: "Implementing hot module replacement (HMR) with Rollup.js for faster development cycles"
description: " "
date: 2023-09-18
tags: [webdevelopment, Rollup]
comments: true
share: true
---

In modern web development, improving the development cycle is crucial to increase productivity and efficiency. One way to achieve this is by implementing hot module replacement (HMR), which allows developers to see immediate changes in their code without refreshing the entire page. In this blog post, we will explore how to set up HMR with Rollup.js, a popular module bundler.

## What is Hot Module Replacement (HMR)?
Hot Module Replacement is a feature that enables developers to update modules during runtime without losing the application's state. It replaces the changed modules without reloading the entire page, making the development process faster and more seamless.

## Setting up Rollup.js
Before we can implement HMR, we need to set up Rollup.js in our project. Make sure you have Node.js installed, and then follow these steps:

1. Create a new project directory:
   ```
   mkdir my-project
   cd my-project
   ```

2. Initialize a new npm project:
   ```
   npm init -y
   ```

3. Install Rollup.js and its plugins:
   ```
   npm install rollup rollup-plugin-serve rollup-plugin-livereload --save-dev
   ```

4. Create a Rollup configuration file named `rollup.config.js`:
   ```javascript
   import serve from 'rollup-plugin-serve';
   import livereload from 'rollup-plugin-livereload';

   export default {
     input: 'src/index.js',
     output: {
       file: 'dist/bundle.js',
       format: 'esm',
     },
     plugins: [
       serve({
         open: true,
         contentBase: ['dist'],
       }),
       livereload('dist'),
     ],
   };
   ```

5. Create a source file in the `src` directory, for example, `index.js`. Write some sample code to test HMR:
   ```javascript
   let count = 0;

   function incrementCount() {
     count++;
     console.log(`Count: ${count}`);
   }

   setInterval(incrementCount, 1000);
   ```

6. Add build and start scripts to your `package.json`:
   ```json
   "scripts": {
     "build": "rollup -c",
     "start": "rollup -c -w"
   }
   ```

## Implementing HMR with Rollup.js
Now that we have the basic Rollup setup completed, let's integrate HMR into our project:

1. Install the `rollup-plugin-hot` plugin: 
   ```
   npm install rollup-plugin-hot --save-dev
   ```

2. Update the `rollup.config.js` file with the hot module replacement plugin:
   ```javascript
   import serve from 'rollup-plugin-serve';
   import livereload from 'rollup-plugin-livereload';
   import hot from 'rollup-plugin-hot';

   export default {
     input: 'src/index.js',
     output: {
       file: 'dist/bundle.js',
       format: 'esm',
     },
     plugins: [
       hot({
         include: '**/*.js',
         public: 'dist',
       }),
       serve({
         open: true,
         contentBase: ['dist'],
       }),
       livereload('dist'),
     ],
   };
   ```

3. Modify the `index.js` file to enable module hot replacement:
   ```javascript
   let count = 0;

   if (import.meta.hot) {
     import.meta.hot.accept(() => {
       // Handle hot module replacement changes here
       console.log('Hot module replaced!');
     });
   }

   function incrementCount() {
     count++;
     console.log(`Count: ${count}`);
   }

   setInterval(incrementCount, 1000);
   ```

4. Start the development server with HMR enabled:
   ```
   npm start
   ```

5. Open your browser and navigate to `http://localhost:5000`. Open the developer console to see the count incrementing. Without refreshing the page, make changes to the code. You should see the hot module replacement taking effect immediately.

## Conclusion
Implementing hot module replacement with Rollup.js can significantly improve the development cycle by providing instant feedback when making code changes. By following the steps outlined in this blog post, you can set up HMR in your project and enjoy faster development cycles. Give it a try and experience the benefits for yourself!

#webdevelopment #Rollup.js