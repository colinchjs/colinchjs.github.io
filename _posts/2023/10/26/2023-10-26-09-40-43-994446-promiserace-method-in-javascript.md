---
layout: post
title: "Promise.race() method in Javascript"
description: " "
date: 2023-10-26
tags: [promises]
comments: true
share: true
---

JavaScript is a powerful programming language that provides various built-in methods to work with promises, one of which is the `Promise.race()` method. In this blog post, we will explore what the `Promise.race()` method does and how it can be used in your JavaScript applications.

## Introduction to Promise.race()

The `Promise.race()` method is a static method that takes an iterable (an array or any other iterable object) of promises as input. It returns a new promise that is fulfilled or rejected as soon as one of the promises in the iterable is fulfilled or rejected.

## Usage of Promise.race()

The `Promise.race()` method is particularly useful when you have multiple asynchronous operations and you want to perform some action as soon as any one of them completes. Here is an example to demonstrate its usage:

```javascript
const promise1 = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Promise 1 resolved'), 2000);
});

const promise2 = new Promise((resolve, reject) => {
  setTimeout(() => resolve('Promise 2 resolved'), 1000);
});

Promise.race([promise1, promise2])
  .then(result => {
    console.log(result);
    // Resolves with the value of the promise that resolves first
  })
  .catch(error => {
    console.error(error);
    // Handles errors if any of the promises reject
  });
```

In this example, we create two promises `promise1` and `promise2` with different setTimeout intervals. We use `Promise.race()` to wait until either of the promises is resolved. The `then()` block logs the result from the resolved promise, and the `catch()` block handles any errors if one of the promises is rejected.

## Promise.race() in Error Handling

The `Promise.race()` method can also be useful for implementing a timeout functionality. For example, consider a scenario where you want to fetch some data using an API call, but you want to set a timeout in case the API takes too long to respond. You can achieve this using `Promise.race()` and a timer promise as shown below:

```javascript
const fetchData = new Promise(resolve => {
  setTimeout(() => resolve('Data fetched from API'), 5000);
});

const timeout = new Promise((resolve, reject) => {
  setTimeout(() => reject(new Error('Request timed out')), 3000);
});

Promise.race([fetchData, timeout])
  .then(result => {
    console.log(result);
    // Resolves with data if fetched before timeout
  })
  .catch(error => {
    console.error(error);
    // Handles timeout error if API call takes too long
  });
```

In this example, we create a `fetchData` promise that mimics an API call and takes 5 seconds to resolve. We also create a `timeout` promise that rejects with an error after 3 seconds. By using `Promise.race()`, we wait for either the `fetchData` promise to resolve or the `timeout` promise to reject. If the API call completes within 3 seconds, the `then()` block logs the fetched data. Otherwise, the `catch()` block handles the timeout error.

## Conclusion

The `Promise.race()` method in JavaScript is a powerful tool for handling asynchronous operations. It allows you to wait for the first promise to resolve or reject, making it invaluable in scenarios where you want to perform an action based on the first completion or handle timeouts. By utilizing `Promise.race()`, you can write cleaner and more efficient code for handling concurrency in your JavaScript applications.

For more information, you can refer to the official [MDN documentation on Promise.race()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race).

#javascript #promises