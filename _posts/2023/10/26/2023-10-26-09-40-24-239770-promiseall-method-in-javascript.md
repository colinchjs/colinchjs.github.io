---
layout: post
title: "Promise.all() method in Javascript"
description: " "
date: 2023-10-26
tags: [JavaScript, Promises]
comments: true
share: true
---

In JavaScript, the `Promise.all()` method is a powerful utility that allows you to combine multiple promises into a single promise. It takes an array of promises as an input and returns a new promise that resolves when all the input promises have resolved, or rejects if any of the promises reject.

## Syntax
```
Promise.all(iterable);
```

The `iterable` parameter is an array (or any other iterable object) containing the promises to be resolved.

## Usage
```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Resolved Promise 1');
  }, 1000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Resolved Promise 2');
  }, 2000);
});

const promise3 = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Resolved Promise 3');
  }, 1500);
});

Promise.all([promise1, promise2, promise3])
  .then((results) => {
    console.log(results);
  })
  .catch((error) => {
    console.log(error);
  });
```

In the above example, we create three promises (`promise1`, `promise2`, `promise3`) that resolve after different intervals of time using the `setTimeout()` function. We pass these promises as an array to `Promise.all()`.

When all the promises have resolved, the `then()` callback is invoked with an array of the resolved values. In this case, it will log `["Resolved Promise 1", "Resolved Promise 2", "Resolved Promise 3"]` to the console.

If any of the promises reject, the `catch()` callback is invoked with the reason for rejection.

## Handling Errors
If any of the promises in the input iterable reject, the `Promise.all()` method immediately rejects with the reason of the first rejected promise. The promises that are yet to resolve will be ignored.

To handle errors for individual promises, you can use the `catch()` method on each promise before passing them to `Promise.all()`. This way, you can handle errors separately for each promise.

## Summary

The `Promise.all()` method in JavaScript provides a convenient way to handle multiple promises simultaneously. It allows you to wait for all promises to resolve and perform further actions when they have all completed successfully. By using `Promise.all()`, you can efficiently manage and synchronize asynchronous tasks in your JavaScript code.

> **Hashtags:** #JavaScript #Promises