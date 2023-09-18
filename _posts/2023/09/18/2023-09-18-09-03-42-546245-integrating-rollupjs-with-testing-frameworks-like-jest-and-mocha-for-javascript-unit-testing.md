---
layout: post
title: "Integrating Rollup.js with testing frameworks like Jest and Mocha for JavaScript unit testing"
description: " "
date: 2023-09-18
tags: [testing, rollup]
comments: true
share: true
---

In modern JavaScript development, it's important to ensure that your code is thoroughly tested. Testing frameworks like Jest and Mocha make it easier to write and execute unit tests, providing more confidence in the quality of your code. However, when using a module bundler like Rollup.js, there are additional steps involved in setting up and configuring the testing environment.

### Setting up Jest with Rollup.js

1. Install the necessary dependencies:
```shell
npm install --save-dev jest jest-cli rollup-plugin-commonjs rollup-plugin-node-resolve@13.0.0
```
2. Add a `jest.config.js` file to the root of your project:
```javascript
module.exports = {
  transform: {
    "^.+\\.js$": "babel-jest"
  },
  moduleNameMapper: {
    "\\.(css|less)$": "<rootDir>/mocks/styleMock.js"
  }
};
```
3. Create a `mocks` folder in your project's root directory.
4. Inside the `mocks` folder, create a `styleMock.js` file with the following content:
```javascript
module.exports = {};
```
5. Modify your `rollup.config.js` file to use the `commonjs` and `node-resolve` plugins:
```javascript
import commonjs from 'rollup-plugin-commonjs';
import resolve from 'rollup-plugin-node-resolve';

export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.js',
    format: 'cjs',
  },
  plugins: [
    commonjs(),
    resolve({
      browser: true,
    }),
  ],
};
```
6. Update your `package.json` file to include the `jest` command:
```json
{
  "scripts": {
    "test": "jest"
  }
}
```
7. Write your unit tests in files with the `.test.js` extension and place them next to your source files.

### Setting up Mocha with Rollup.js

1. Install the necessary dependencies:
```shell
npm install --save-dev mocha rollup-plugin-commonjs rollup-plugin-node-resolve@13.0.0
```
2. Modify your `rollup.config.js` file to use the `commonjs` and `node-resolve` plugins:
```javascript
import commonjs from 'rollup-plugin-commonjs';
import resolve from 'rollup-plugin-node-resolve';

export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.js',
    format: 'cjs',
  },
  plugins: [
    commonjs(),
    resolve({
      browser: true,
    }),
  ],
};
```
3. Create a `test-runner.js` file in your project's root directory with the following content:
```javascript
import 'source-map-support/register';
import glob from 'glob';
import Mocha from 'mocha';

const mocha = new Mocha();

glob('src/**/*.test.js', (err, files) => {
  if (err) {
    console.error(err);
    process.exit(1);
  }

  files.forEach((file) => mocha.addFile(file));

  mocha.run((failures) => {
    process.exitCode = failures ? 1 : 0;
  });
});
```
4. Update your `package.json` file to include the `test` script and the modified `test-runner.js` file:
```json
{
  "scripts": {
    "test": "node test-runner.js"
  }
}
```
5. Write your unit tests in files with the `.test.js` extension and place them next to your source files.

### Conclusion

By integrating Rollup.js with testing frameworks like Jest and Mocha, you can streamline your unit testing process and ensure that your code behaves as expected. Following the steps outlined in this post, you'll be on your way to writing high-quality JavaScript code and catching bugs before they become problems.

#testing #rollup.js #jest #mocha