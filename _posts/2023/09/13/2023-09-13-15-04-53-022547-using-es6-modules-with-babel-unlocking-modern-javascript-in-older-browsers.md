---
layout: post
title: "Using ES6 Modules with Babel: Unlocking Modern JavaScript in Older Browsers"
description: " "
date: 2023-09-13
tags: [Babel, modules]
comments: true
share: true
---

With the emergence of ES6 (ECMAScript 2015), JavaScript saw a significant upgrade with the introduction of various new features and syntax improvements. One of the most notable additions was the support for **ES6 modules**, which allows developers to organize their code into separate files and reuse modules across different parts of their application.

Unfortunately, not all browsers have native support for ES6 modules, especially older versions. This can pose a problem for developers who want to take advantage of the new language features but still have to support older browsers. Luckily, **Babel** comes to the rescue.

## What is Babel?

[Babel](https://babeljs.io/) is a popular JavaScript compiler that transforms modern JavaScript code into backward-compatible versions that can run on older browsers. It allows developers to write code using the latest language features, such as ES6 modules, and then compiles it down into a version that can be understood by older browsers.

## Setting Up Babel for ES6 Modules

To get started with using ES6 modules in older browsers using Babel, we need to set up a project and configure Babel accordingly. 

1. First, we need to install Babel by running the following command in the terminal or command prompt:
```shell
npm install --save-dev @babel/core @babel/preset-env
```

2. Next, we need to configure Babel by creating a `.babelrc` file in the root directory of our project. Add the following content to the file:
```json
{
  "presets": [
    "@babel/preset-env"
  ]
}
```

3. Now, we can start writing our JavaScript code using ES6 modules. For example, let's create two separate files: `main.js` and `module.js`. In `module.js`, we define a function named `hello` that we want to use in `main.js`.
```javascript
// module.js
export function hello() {
  return "Hello, World!";
}
```

4. In `main.js`, we can import the `hello` function from `module.js` using the `import` statement:
```javascript
// main.js
import { hello } from "./module.js";
console.log(hello());
```

5. Finally, we need to compile our code using Babel before deploying it to the web. We can do this by adding a build script in our `package.json` file:
```json
{
  "scripts": {
    "build": "babel src -d dist"
  }
}
```
Running `npm run build` will compile the code in the `src` directory and output the transformed code in the `dist` directory.

## Conclusion

By using Babel, we can enjoy the benefits of ES6 modules while still being able to support older browsers. Babel's ability to transpile modern JavaScript code into older versions enables us to write clean, modular code without worrying about browser compatibility issues.

#javascript #ES6 #Babel #modules