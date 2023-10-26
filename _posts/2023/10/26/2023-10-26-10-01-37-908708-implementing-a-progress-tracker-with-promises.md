---
layout: post
title: "Implementing a progress tracker with promises"
description: " "
date: 2023-10-26
tags: [References]
comments: true
share: true
---

## Introduction
In JavaScript, promises are a powerful tool for handling asynchronous operations. They provide an elegant way to handle asynchronous code and improve the readability and maintainability of our code. In this article, we will explore how to implement a progress tracker using promises.

## Problem Statement
Imagine you have a task that involves multiple asynchronous operations, such as downloading files or making API calls. You want to track the progress of each operation and perform some action when all operations are completed. How can you achieve this using promises?

## Solution
To implement a progress tracker with promises, we can leverage the `Promise.all()` method and create a custom progress tracker class.

## Creating the Progress Tracker Class
Let's create a `ProgressTracker` class that will track the progress of multiple promises. The class will have methods to add promises, track their progress, and perform an action when all promises are completed.

```javascript
class ProgressTracker {
  constructor(promises) {
    this.promises = promises;
    this.completedCount = 0;
    this.totalCount = promises.length;
  }

  addPromise(promise) {
    this.promises.push(promise);
    this.totalCount++;
  }

  trackProgress() {
    this.promises.forEach(promise => {
      promise.then(() => {
        this.completedCount++;
        this.checkCompletion();
      });
    });
  }

  checkCompletion() {
    if (this.completedCount === this.totalCount) {
      this.onCompletion();
    }
  }

  onCompletion() {
    console.log('All promises completed!');
    // Perform action when all promises are completed
  }
}
```

## Using the Progress Tracker
Now that we have implemented the `ProgressTracker` class, let's see how we can use it to track the progress of promises:

```javascript
const promise1 = new Promise(resolve => setTimeout(resolve, 2000));
const promise2 = new Promise(resolve => setTimeout(resolve, 3000));
const promise3 = new Promise(resolve => setTimeout(resolve, 1000));

const progressTracker = new ProgressTracker([promise1, promise2]);
progressTracker.addPromise(promise3);
progressTracker.trackProgress();
```

In the above example, we create three promises with different timeouts. We create a `ProgressTracker` instance with `promise1` and `promise2`, and then add `promise3` to the tracker. Finally, we call the `trackProgress()` method to start tracking the progress. When all promises are completed, the `onCompletion()` method will be called.

## Conclusion
Implementing a progress tracker with promises in JavaScript can greatly simplify the handling of multiple asynchronous operations. By leveraging the `Promise.all()` method and creating a custom progress tracker class, we can easily track the progress of promises and perform actions when all promises are completed.

By organizing and managing our asynchronous code effectively, we can enhance the performance and user experience of our applications.

#References
- [JavaScript Promises - MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [JavaScript Promises: An Introduction](https://scotch.io/tutorials/javascript-promises-an-introduction)
- [Async Programming Techniques with Promises](https://developers.google.com/web/fundamentals/primers/promises)