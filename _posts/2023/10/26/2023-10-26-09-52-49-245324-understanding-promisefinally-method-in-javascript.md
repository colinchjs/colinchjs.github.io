---
layout: post
title: "Understanding Promise.finally() method in Javascript"
description: " "
date: 2023-10-26
tags: [asynchronous]
comments: true
share: true
---

JavaScript is a popular programming language known for its asynchronous nature. When dealing with asynchronous operations, it is common to use Promises to handle callbacks and ensure a more structured approach to managing asynchronous code. 

One handy method available for Promises in JavaScript is the `finally()` method. In this blog post, we will explore what the `finally()` method does and how to use it effectively.

## Table of Contents
- [What is Promise.finally()?](#what-is-promise-finally)
- [Usage](#usage)
- [Example](#example)
- [Benefits of using finally()](#benefits-of-using-finally)
- [Conclusion](#conclusion)

## What is Promise.finally()?
The `finally()` method is a part of the Promise API that allows you to register a callback function that will be invoked regardless of whether the Promise is resolved or rejected. It provides a way to perform clean-up tasks or execute code that needs to be run at the end of a Promise chain, irrespective of its outcome.

## Usage
The `finally()` method can be used by chaining it onto a Promise. Syntaxically, it is placed after the `then()` or `catch()` methods and before the closing semicolon. 

Here's its syntax:
```javascript
promise
  .then(onFulfilled)
  .catch(onRejected)
  .finally(onFinally);
```

The `onFinally` callback will be executed whether the Promise is resolved or rejected.

## Example
Let's consider an example where we fetch data from an API using Promises. We want to display a loading spinner while the data is being fetched, regardless of whether the request succeeds or fails. 

```javascript
function fetchData() {
  showSpinner();

  return fetch('https://api.example.com/data')
    .then(response => response.json())
    .then(data => {
      // Handle the data
      showData(data);
    })
    .catch(error => {
      // Handle the error
      showError(error);
    })
    .finally(() => {
      hideSpinner();
    });
}

fetchData();
```

In the above example, the `finally()` method is used to hide the loading spinner, ensuring that the spinner is always removed, no matter the outcome of the Promise.

## Benefits of using finally()
The `finally()` method has several benefits when working with Promises:
- It allows you to consolidate code that needs to be executed regardless of the Promise outcome.
- It avoids code repetition by providing a single place to handle clean-up tasks.
- It gives you a way to handle final operations, such as hiding loaders, closing connections, and releasing resources.

## Conclusion
The `finally()` method in JavaScript is a powerful tool that allows you to execute code at the end of a Promise chain, whether the Promise is resolved or rejected. This makes it a valuable addition to your asynchronous programming toolkit. By using `finally()`, you can easily handle clean-up tasks and ensure consistent behavior in your applications.

Remember to take advantage of the `finally()` method in your asynchronous JavaScript code to improve the readability and maintainability of your projects.

*#javascript #asynchronous*