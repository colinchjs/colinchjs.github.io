---
layout: post
title: "How to cancel a Javascript promise"
description: " "
date: 2023-10-26
tags: []
comments: true
share: true
---

Javascript promises are often used to handle asynchronous operations in a more elegant and organized way. However, there may be times when we need to cancel a promise before it is resolved or rejected. In this article, we will explore different approaches to achieve promise cancellation in Javascript.

## Method 1: Using a Cancellation Token

One way to implement promise cancellation is by using a cancellation token. A cancellation token is an object that can be used to signal cancellation to an ongoing operation.

Here is an example of how to implement promise cancellation using a cancellation token:

```javascript
class CancellationToken {
  constructor() {
    this.isCancelled = false;
    this.cancelHandlers = [];
  }

  cancel() {
    if (this.isCancelled) return;
    this.isCancelled = true;
    this.cancelHandlers.forEach((handler) => handler());
  }

  registerCancelHandler(handler) {
    if (this.isCancelled) {
      handler();
    } else {
      this.cancelHandlers.push(handler);
    }
  }
}

function cancellablePromise(promiseFactory, cancellationToken) {
  return new Promise((resolve, reject) => {
    cancellationToken.registerCancelHandler(() => reject(new Error('Promise cancelled')));

    promiseFactory()
      .then((result) => {
        if (!cancellationToken.isCancelled) {
          resolve(result);
        }
      })
      .catch(reject);
  });
}
```

In this example, we define a `CancellationToken` class that is responsible for tracking the cancellation state and invoking registered cancel handlers. The `cancellablePromise` function takes a `promiseFactory` function that returns a promise and a `cancellationToken`. It wraps the `promiseFactory` function inside a new promise and registers a cancel handler that rejects the promise with an error when cancellation is requested.

## Method 2: Using a Third-Party Library

Another approach to promise cancellation is to use a third-party library that provides built-in support for cancellation. There are several popular libraries available, such as `bluebird` and `rxjs`, that offer additional features, including promise cancellation.

Here is an example of how to cancel a promise using the `bluebird` library:

```javascript
const Promise = require('bluebird');

const cancellation = new Promise.CancellationError();

const promise = new Promise((resolve, reject, onCancel) => {
  onCancel(() => {
    reject(new Error('Promise cancelled'));
  });

  // Add asynchronous operations here
});

promise.cancel(cancellation);
```

In this example, we create a `CancellationError` object from the `bluebird` library. We then create a promise and pass an `onCancel` callback to handle cancellation. Inside the callback, we reject the promise with an error when cancellation is requested.

## Conclusion

Promise cancellation can be a useful feature in certain scenarios where we need to abort asynchronous operations. In this article, we explored two methods for achieving promise cancellation in Javascript: using a cancellation token and using a third-party library. By understanding these techniques, you can handle promise cancellation effectively in your applications.

Remember to use these techniques when necessary, as promise cancellation may not be supported in all situations.