---
layout: post
title: "Promise.reject() method in Javascript"
description: " "
date: 2023-10-26
tags: [promises]
comments: true
share: true
---

In JavaScript, promises are a powerful way to handle asynchronous operations. They enable us to write cleaner and more readable code by avoiding callback hell. Promises represent the eventual completion or failure of an asynchronous operation and allow us to chain multiple operations together.

The `Promise.reject()` method is a static method that returns a new Promise object that is rejected with the given reason. It is commonly used when we want to explicitly reject a promise with a specific error or failure message.

## Syntax

The syntax of the `Promise.reject()` method is as follows:

```javascript
Promise.reject(reason);
```

- `reason` (optional): The reason for rejecting the promise. This can be any value, such as an error object, an error message, or any other data type.

## Example

Let's look at a simple example to understand how `Promise.reject()` works:

```javascript
function checkNumber(number) {
  return new Promise((resolve, reject) => {
    if (typeof number === "number") {
      resolve("Number is valid.");
    } else {
      reject("Invalid input. Please provide a number.");
    }
  });
}

checkNumber(10)
  .then((message) => {
    console.log(message);
  })
  .catch((error) => {
    console.error(error);
  });

checkNumber("abc")
  .then((message) => {
    console.log(message);
  })
  .catch((error) => {
    console.error(error);
  });
```

In this example, we have a `checkNumber()` function that returns a promise. It checks if the provided argument is a valid number. If it is, the promise is resolved with the message "Number is valid." If it is not, the promise is rejected with the error message "Invalid input. Please provide a number."

We use `Promise.reject()` inside the `checkNumber()` function to explicitly reject the promise when the input is not a number.

When we call `checkNumber(10)`, the promise is resolved, and the message "Number is valid" is logged to the console. However, when we call `checkNumber("abc")`, the promise is rejected, and the error message "Invalid input. Please provide a number" is logged to the console.

## Conclusion

The `Promise.reject()` method allows us to explicitly reject a promise with a specific reason. It is useful when we want to handle and propagate errors in our code. By combining it with other promise methods like `then()` and `catch()`, we can create robust and fault-tolerant asynchronous JavaScript applications.

For more information, you can refer to the [MDN documentation on Promise.reject()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/reject).

`#javascript` `#promises`