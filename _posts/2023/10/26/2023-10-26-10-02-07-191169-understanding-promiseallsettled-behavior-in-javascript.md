---
layout: post
title: "Understanding Promise.allSettled() behavior in Javascript"
description: " "
date: 2023-10-26
tags: []
comments: true
share: true
---

Promises are a crucial concept in JavaScript to handle asynchronous operations, allowing us to write code that is more readable and maintainable. Introduced in ES6, promises improved the way we deal with asynchronous code by providing a standardized way to handle success and failure cases.

One of the useful methods that ES2020 introduced to the Promise API is `Promise.allSettled()`. This method is similar to `Promise.all()`, but with one crucial difference: `Promise.allSettled()` **doesn't short-circuit** when any of the promises in the iterable fails. Instead, it waits for all the promises to either fulfill or reject before returning the results.

To understand this behavior better, let's look at an example:

```javascript
const promises = [
  Promise.resolve('Resolved Promise 1'),
  Promise.reject('Rejected Promise 2'),
  Promise.reject('Rejected Promise 3'),
  Promise.resolve('Resolved Promise 4')
];

Promise.allSettled(promises)
  .then(results => console.log(results));
```

In this example, we have an array of four promises. The first and fourth promises are resolved, while the second and third promises are rejected.

When we execute `Promise.allSettled()` on this array, the resulting promise doesn't reject immediately after encountering the first rejected promise. Instead, it waits for all the promises to settle and returns an array of objects representing the status of each promise.

The `results` array will contain objects with two properties: `status` and `value` (or `reason` in case of rejection). The `status` property will be either `"fulfilled"` or `"rejected"`, while the `value` property will hold the resolved value or the `reason` property will hold the rejection reason.

In our example, the output will be:

```javascript
[
  { status: 'fulfilled', value: 'Resolved Promise 1' },
  { status: 'rejected', reason: 'Rejected Promise 2' },
  { status: 'rejected', reason: 'Rejected Promise 3' },
  { status: 'fulfilled', value: 'Resolved Promise 4' },
]
```

As we can see, `Promise.allSettled()` returns the result of all promises, whether they are fulfilled or rejected.

It's important to note that `Promise.allSettled()` works with any iterable, not just array-like objects. It also returns a promise, allowing us to chain additional `.then()` or `.catch()` handlers to handle the results accordingly.

In conclusion, `Promise.allSettled()` provides a useful way to handle multiple promises, especially when we want to wait for all of them to settle regardless of their individual success or failure. By understanding its behavior and utilizing it effectively, we can write more robust and error-tolerant asynchronous code in JavaScript.

For further information, you can refer to the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/allSettled).