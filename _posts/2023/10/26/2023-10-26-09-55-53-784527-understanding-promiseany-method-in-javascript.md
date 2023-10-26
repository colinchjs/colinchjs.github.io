---
layout: post
title: "Understanding Promise.any() method in Javascript"
description: " "
date: 2023-10-26
tags: [promises]
comments: true
share: true
---

Javascript has introduced the `Promise.any()` method as a part of the ECMAScript 2021 (ES2021) specification. The `Promise.any()` method is used to handle multiple promises and returns a new promise that resolves when any of the input promises resolve. It is the opposite of the `Promise.all()` method, which waits for all promises to resolve.

## Usage

The syntax of `Promise.any()` is as follows:

```javascript
Promise.any(iterable)
```

The `iterable` parameter represents multiple promises that you want to handle. It can be an array-like object or an iterable (e.g., array, set).

## Resolving Behavior

When any promise in the input array resolves, the `Promise.any()` method will resolve with the value of the resolved promise. It does not matter whether the other promises are pending or rejected.

If all of the input promises are rejected, the `Promise.any()` method will throw an `AggregateError` which is a new type of error introduced in ES2021. The `AggregateError` contains an array of rejection reasons from all the input promises.

## Example

```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(resolve, 100, 'Resolved in 100ms');
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(resolve, 200, 'Resolved in 200ms');
});

const promise3 = new Promise((resolve, reject) => {
  setTimeout(resolve, 300, 'Resolved in 300ms');
});

const promises = [promise1, promise2, promise3];

Promise.any(promises)
  .then((value) => {
    console.log(value); // Logs the value of the first resolved promise
  })
  .catch((error) => {
    console.log(error); // Logs an AggregateError if all promises are rejected
  });
```

In the above example, three promises are created with different setTimeout durations. The `Promise.any()` method is used on the array of promises and the resolved value of the first resolved promise is logged. If all the promises are rejected, an `AggregateError` is caught and logged.

## Browser Compatibility

The `Promise.any()` method has decent browser support but is not supported in older browsers such as Internet Explorer. It is supported in modern browsers like Chrome, Firefox, Edge, and Safari. You can check the browser compatibility on [Can I use](https://caniuse.com/mdn-javascript_builtins_promise_any).

## Conclusion

The `Promise.any()` method is a powerful addition to the JavaScript Promise API. It allows you to handle multiple promises and resolves when any of the promises resolve. This can be useful in scenarios where you want to execute different promises concurrently and handle the first one that resolves. Stay updated with the latest JavaScript specifications to make the most out of modern JavaScript features.

*Tags: #javascript #promises*