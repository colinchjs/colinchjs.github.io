---
layout: post
title: "How to handle timeouts in promises"
description: " "
date: 2023-10-26
tags: []
comments: true
share: true
---

In JavaScript, promises are a powerful tool used for managing asynchronous operations. Promises allow you to handle success or failure of an asynchronous task in a structured manner. However, there may be cases where you want to handle timeouts for promises to prevent them from hanging indefinitely. In this blog post, we will explore different approaches to handling timeouts in promises.

## Table of Contents
- [Using Promise.race()](#using-promise.race)
- [Using setTimeout() and Promise.reject()](#using-settimeout-and-promise.reject)

## Using Promise.race()

One approach to handling timeouts in promises is by using the `Promise.race()` function. This function takes an array of promises as input and returns a new promise that is settled with the result of the first promise that settles (either resolves or rejects).

To implement a timeout using `Promise.race()`, you can create a promise that rejects after a certain duration if the original promise does not resolve or reject within that time. Here's an example:

```javascript
function timeoutPromise(promise, timeout) {
    return Promise.race([
        promise,
        new Promise((_, reject) =>
            setTimeout(() => reject(new Error('Promise timed out')), timeout)
        )
    ]);
}

// Usage example
const myPromise = new Promise((resolve) => setTimeout(() => resolve('Success!'), 2000));
const timeoutDuration = 3000;

timeoutPromise(myPromise, timeoutDuration)
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

In the example above, the `timeoutPromise()` function takes a promise and a timeout duration as input. It creates a new promise that rejects with an error message if the original promise does not resolve or reject within the specified timeout.

## Using setTimeout() and Promise.reject()

Another common approach to handling timeouts in promises is by combining `setTimeout()` and `Promise.reject()`. You can create a promise that rejects after the specified timeout using `setTimeout()` and then use it with `Promise.race()` to handle the timeout.

Here's an example:

```javascript
function timeoutPromise(promise, timeout) {
    return new Promise((resolve, reject) => {
        setTimeout(() => reject(new Error('Promise timed out')), timeout);
        promise.then(resolve, reject);
    });
}

// Usage example
const myPromise = new Promise((resolve) => setTimeout(() => resolve('Success!'), 2000));
const timeoutDuration = 3000;

timeoutPromise(myPromise, timeoutDuration)
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

In this example, the `timeoutPromise()` function creates a new promise using `setTimeout()` to reject with an error message if the original promise does not resolve or reject within the specified timeout. It then uses `promise.then()` to either resolve or reject the original promise based on its outcome.

## Conclusion

Handling timeouts in promises is important to prevent them from hanging indefinitely. You can use the `Promise.race()` function or combine `setTimeout()` and `Promise.reject()` to implement timeouts for promises. Choose the approach that best fits your use case and ensures that your asynchronous operations have proper timeouts.

# References
- [MDN Web Docs - Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN Web Docs - Promise.race()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)
- [MDN Web Docs - setTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout)