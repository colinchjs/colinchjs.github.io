---
layout: post
title: "Understanding Promise.allSettled() method in Javascript"
description: " "
date: 2023-10-26
tags: [browser, browser]
comments: true
share: true
---

When working with asynchronous JavaScript, it is common to use Promises to handle multiple asynchronous operations. In some cases, you may want to execute a group of promises and handle the outcome of all of them, regardless of whether they were resolved or rejected. The `Promise.allSettled()` method comes in handy for this scenario.

## Table of Contents
- [Introduction to Promise.allSettled()](#introduction)
- [Usage](#usage)
- [Example](#example)
- [Browser Support](#browser-support)
- [Conclusion](#conclusion)

## Introduction to Promise.allSettled() {#introduction}
The `Promise.allSettled()` method returns a promise that resolves after all of the given promises have either resolved or rejected. This is different from the `Promise.all()` method, which immediately rejects if any of the promises are rejected. Instead, `Promise.allSettled()` waits for all the promises to settle, providing an array of objects that describe the outcome of each promise. Each object has a status (`"fulfilled"` or `"rejected"`) and a `value` or `reason` property that represents the fulfilled value or rejection reason, respectively.

## Usage {#usage}
The syntax of the `Promise.allSettled()` method is as follows:

```javascript
Promise.allSettled(iterable)
```

Here, `iterable` is an iterable object, such as an Array, that contains the promises to be settled. The method returns a promise that is fulfilled with an array of objects once all the promises in the iterable have settled.

## Example {#example}
Let's consider an example where we have an array of promises that need to be resolved:

```javascript
const promises = [
  Promise.resolve(1),
  Promise.reject(new Error("Oops")),
  Promise.resolve(3)
];

Promise.allSettled(promises)
  .then((results) => {
    results.forEach((result) => {
      if (result.status === "fulfilled") {
        console.log("Value:", result.value);
      } else if (result.status === "rejected") {
        console.log("Error:", result.reason);
      }
    });
  })
  .catch((error) => {
    console.log("An error occurred:", error);
  });
```

In this example, we have an array of promises where the second promise is intentionally rejected. The `Promise.allSettled()` method is used to wait for all the promises to settle. Once they have settled, we loop through the results array and log the value for fulfilled promises or the error for rejected promises.

Output:
```
Value: 1
Error: Error: Oops
Value: 3
```

## Browser Support {#browser-support}
The `Promise.allSettled()` method is supported in most modern browsers, including Chrome, Firefox, Safari, and Edge. However, it is not supported in Internet Explorer.

For up-to-date information on browser support, refer to the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled#browser_compatibility).

## Conclusion {#conclusion}
The `Promise.allSettled()` method is a useful addition to JavaScript's built-in Promise API. It allows you to handle multiple promises and obtain the outcome of each one, whether it resolved successfully or was rejected. By using this method, you can write more robust and flexible asynchronous code. Remember to check the browser support before using it in your projects.

#javascript #promises