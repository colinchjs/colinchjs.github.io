---
layout: post
title: "Constructor functions for promises and async/await in JavaScript"
description: " "
date: 2023-10-24
tags: []
comments: true
share: true
---

Promises are a powerful feature introduced in JavaScript to handle async operations. They provide a clean and intuitive way to write asynchronous code and avoid callback hell. In this blog post, we will explore how to create promises using constructor functions in JavaScript.

## Creating a Promise

To create a promise in JavaScript, we use the `Promise` constructor function. It takes a single argument, a callback function, which in turn takes two arguments: `resolve` and `reject`. The `resolve` function is used to fulfill the promise, while the `reject` function is used to reject it.

Here's an example:

```javascript
const myPromise = new Promise((resolve, reject) => {
  // Perform an asynchronous operation

  const success = true;

  if (success) {
    resolve("Promise fulfilled");
  } else {
    reject("Promise rejected");
  }
});
```

In the example above, we create a new promise `myPromise` and perform an asynchronous operation inside the callback function. If the operation is successful, we call `resolve` and pass the fulfilled value as an argument. Otherwise, we call `reject` and pass the rejected value.

## Handling Promise Fulfillment and Rejection

Once a promise is created, we can use the `then` method to handle its fulfillment, and the `catch` method to handle its rejection. The `then` method takes a callback function that will be executed when the promise is fulfilled, while the `catch` method takes a callback function that will be executed when the promise is rejected.

Continuing from the previous example, here's how we can handle promise fulfillment and rejection:

```javascript
myPromise
  .then((result) => {
    console.log(result);
  })
  .catch((error) => {
    console.error(error);
  });
```

In the `then` callback, we log the fulfilled result to the console. In the `catch` callback, we log the rejected error to the console. This allows us to handle the promise's outcome accordingly.

# Async/Await in JavaScript

Async/await is a syntax sugar introduced in ECMAScript 2017 that makes working with promises even more elegant. It allows us to write asynchronous code in a synchronous-like manner, making it easier to read and understand.

## Using the async Keyword

To use the await keyword, we need to declare the containing function with the async keyword. This tells JavaScript that the function is asynchronous and can contain await expressions.

Here's an example:

```javascript
async function fetchData() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  return data;
}
```

In the example above, we define an asynchronous function `fetchData`. Within the function, we use the `await` keyword to wait for the result of the `fetch` request and the subsequent parsing of JSON data. Finally, we return the data.

## Handling Errors with try/catch

To handle errors when using async/await, we can use the try/catch statement. This allows us to catch any errors that occur during the execution of the asynchronous code.

Continuing from the previous example, here's how we can handle errors:

```javascript
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error(error);
  }
}
```

In this example, any errors that occur during the fetching or parsing of data will be caught and logged to the console. This makes it easier to handle and debug errors in our asynchronous code.

## Conclusion

In this blog post, we explored how to create promises using constructor functions in JavaScript. We also learned about the async/await syntax sugar introduced in ECMAScript 2017, which makes working with promises even more elegant. By using promises and async/await, we can write clean and readable asynchronous code in JavaScript.

References:
- [MDN Web Docs - Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN Web Docs - async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)