---
layout: post
title: "How to timeout a promise in Javascript"
description: " "
date: 2023-10-26
tags: [References]
comments: true
share: true
---

In JavaScript, promises are a powerful way to handle asynchronous operations. However, there may be situations where you want to add a timeout to a promise, so that it automatically rejects after a specified period of time. This can be useful to handle scenarios where a promise takes too long to resolve or when you want to enforce a maximum wait time.

In this blog post, we will explore two approaches to timeout a promise in JavaScript: using the `Promise.race()` method and creating a custom timeout function.

## 1. Using Promise.race()

One way to timeout a promise is by using the `Promise.race()` method. This method takes an array of promises and returns a new promise that is settled as soon as any of the input promises is settled.

To implement a timeout using `Promise.race()`, you can create a new promise that rejects after a specified timeout period:

```javascript
const timeoutPromise = (promise, timeout) => {
  return Promise.race([
    promise,
    new Promise((_, reject) => {
      setTimeout(() => {
        reject(new Error('Promise timeout'));
      }, timeout);
    })
  ]);
};
```

In the above example, the `timeoutPromise` function takes a promise and a timeout value as parameters. It creates a new promise that resolves either with the original promise's result or rejects with an error after the specified timeout.

Here's an example of using the `timeoutPromise` function:

```javascript
const fetchData = () => {
  return new Promise(resolve => {
    // Simulating an asynchronous operation
    setTimeout(() => {
      resolve('Data fetched successfully');
    }, 2000);
  });
};

timeoutPromise(fetchData(), 1500)
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.error(error);
  });
```

In this example, the `fetchData` function returns a promise that resolves after 2 seconds. However, we set the timeout to 1.5 seconds using the `timeoutPromise` function. As a result, the promise times out and rejects with an error.

## 2. Creating a Custom Timeout Function

Another approach to timeout a promise is by creating a custom timeout function. This involves wrapping the original promise with a new promise and using `setTimeout` to reject the new promise after the specified timeout.

Here's an example implementation of a custom timeout function:

```javascript
const timeout = (promise, timeout) => {
  return new Promise((resolve, reject) => {
    const timeoutId = setTimeout(() => {
      reject(new Error('Promise timeout'));
    }, timeout);

    promise
      .then(result => {
        clearTimeout(timeoutId);
        resolve(result);
      })
      .catch(error => {
        clearTimeout(timeoutId);
        reject(error);
      });
  });
};
```

In this example, the `timeout` function takes a promise and a timeout value. It creates a new promise and uses `setTimeout` to reject it after the specified timeout. If the original promise resolves or rejects before the timeout, the custom promise is resolved or rejected accordingly, and the timeout is cleared using `clearTimeout()`.

Here's an example of using the custom `timeout` function:

```javascript
timeout(fetchData(), 1500)
  .then(result => {
    console.log(result);
  })
  .catch(error => {
    console.error(error);
  });
```

This example is similar to the previous one, but we are now using the custom `timeout` function instead of `timeoutPromise`. The result is the same – the promise times out and rejects with an error.

## Conclusion

In this blog post, we explored two approaches to timeout a promise in JavaScript. The first approach is by using the `Promise.race()` method to create a new promise that settles as soon as the original promise or a timeout promise is settled. The second approach involves creating a custom timeout function that wraps the original promise and rejects it after a specified timeout period.

By adding a timeout to promises, you can handle scenarios where you want to enforce a maximum wait time or handle promises that take too long to resolve. Choose the approach that best fits your requirements and integrate it into your JavaScript code.

#References
- [MDN Web Docs: Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN Web Docs: Promise.race()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/race)
- [MDN Web Docs: clearTimeout()](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/clearTimeout)