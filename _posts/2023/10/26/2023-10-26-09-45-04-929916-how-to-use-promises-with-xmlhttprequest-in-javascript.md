---
layout: post
title: "How to use promises with XMLHttpRequest in Javascript"
description: " "
date: 2023-10-26
tags: [promises]
comments: true
share: true
---

In JavaScript, the XMLHttpRequest object is commonly used for asynchronous data retrieval from a server. Traditionally, callbacks were used to handle the response, but with the introduction of Promises, we can now leverage their power to handle asynchronous operations in a more streamlined and readable way.

## What is a Promise?

A Promise is an object that represents a value that may not be available yet, but will be resolved in the future. It has three states: pending, fulfilled, or rejected. Promises are a great way to handle asynchronous operations as they provide a clean and organized way to write code that deals with callbacks.

## Using Promises with XMLHttpRequest

To use Promises with XMLHttpRequest, we can wrap the XMLHttpRequest object inside a Promise. The basic idea is to create a new Promise and resolve it when the XMLHttpRequest's `onload` event is triggered, or reject it when there is an error.

Here's an example of how you can use Promises with XMLHttpRequest:

```javascript
function makeRequest(url) {
  return new Promise(function(resolve, reject) {
    var xhr = new XMLHttpRequest();

    xhr.open('GET', url, true);

    xhr.onload = function() {
      if (xhr.status === 200) {
        resolve(xhr.response);
      } else {
        reject(Error(xhr.statusText));
      }
    };

    xhr.onerror = function() {
      reject(Error('Network Error'));
    };

    xhr.send();
  });
}

// Usage example
makeRequest('https://api.example.com/data')
  .then(function(response) {
    console.log('Data:', response);
  })
  .catch(function(error) {
    console.error('Error:', error);
  });
```

In this example, the `makeRequest` function wraps the XMLHttpRequest inside a Promise and returns it. The Promise is resolved when the `onload` event is triggered and the status is 200, indicating a successful response. If there is an error, the Promise is rejected.

To handle the Promise, we use the `then` method to handle the resolved value, and the `catch` method to handle any errors that occur.

## Conclusion

Using Promises with XMLHttpRequest can greatly simplify asynchronous operations in JavaScript. They provide a more organized and readable way to handle callbacks and make code more maintainable. Promises allow you to write code that is easier to reason about and handle errors more effectively.

By leveraging Promises, you can make your code more robust and handle asynchronous operations with ease. So give it a try and start using Promises with XMLHttpRequest in your JavaScript projects!

\#javascript #promises