---
layout: post
title: "How to handle cancellation requests with promises"
description: " "
date: 2023-10-26
tags: []
comments: true
share: true
---

In JavaScript, Promises are used to handle asynchronous operations and provide a way to handle the success or failure of the operation. However, there may be cases where you need to cancel a Promise if it is no longer needed or if the user explicitly requests to cancel the operation.

While cancellation is not natively supported in JavaScript Promises, there are techniques you can use to implement cancellation behavior. One common approach is to use a cancellation token along with the Promise. Let's see how it can be done.

## Using a Cancellation Token

A cancellation token is an object that can be used to signal whether an operation should be cancelled or not. It provides a way to notify the Promise that it should stop executing and reject itself if necessary.

Here's an example implementation of a cancellation token:

```javascript
class CancellationToken {
  constructor() {
    this.isCancelled = false;
  }

  cancel() {
    this.isCancelled = true;
  }
}
```

In this example, the `CancellationToken` class provides a boolean `isCancelled` property that indicates whether the operation should be cancelled or not. It also provides a `cancel` method to set the `isCancelled` flag to `true`.

Now, let's see how we can use this cancellation token along with a Promise to handle cancellation requests.

```javascript
function fetchData(cancelToken) {
  return new Promise((resolve, reject) => {
    // Simulating an asynchronous operation
    const timeoutId = setTimeout(() => {
      if (cancelToken.isCancelled) {
        reject(new Error("Operation cancelled"));
      } else {
        resolve("Data fetched successfully");
      }
    }, 2000);

    // Cleanup function to cancel the operation
    cancelToken.cleanup = () => {
      clearTimeout(timeoutId);
      reject(new Error("Operation cancelled"));
    };
  });
}
```

In this example, we have a `fetchData` function that takes a `cancelToken` parameter. Inside the Promise executor function, we simulate an asynchronous operation using `setTimeout`. If the `isCancelled` flag is set to `true`, we reject the Promise with an "Operation cancelled" error. Otherwise, we resolve the Promise with the fetched data.

We also provide a `cleanup` function on the `cancelToken` object, which can be used to explicitly cancel the operation. It clears the timeout and rejects the Promise with the same error message.

## Handling Cancellation

To handle cancellation, you can call the `cancel` method on the `CancellationToken` object whenever you want to cancel the operation:

```javascript
const cancelToken = new CancellationToken();

fetchData(cancelToken)
  .then((data) => {
    console.log(data);
  })
  .catch((error) => {
    console.log(error.message);
  });

// Somewhere else in the code
cancelToken.cancel();
```

In this example, we create a new `CancellationToken` object and pass it to the `fetchData` function. We then use the Promise's `then` and `catch` methods to handle the success and failure of the operation. Finally, we call the `cancel` method on the `cancelToken` object to cancel the operation.

## Conclusion

Handling cancellation requests with Promises can be achieved by using a cancellation token along with the Promise. By incorporating cancellation logic and cleanup functions, you can gracefully cancel asynchronous operations when needed.

Remember to provide a way for the user or the system to initiate the cancellation request and handle it appropriately in your code.