---
layout: post
title: "Ternary operations for handling multiple data types in JavaScript"
description: " "
date: 2023-09-19
tags: [JavaScript, TernaryOperations]
comments: true
share: true
---

When working with JavaScript, it's common to come across situations where you need to handle multiple data types. One way to handle these scenarios is by using ternary operations, which allow you to conditionally assign a value based on the evaluation of a condition. This can be especially useful when you need to handle different data types, such as numbers, strings, booleans, or objects.

Let's take a look at some examples of how ternary operations can be used to handle multiple data types in JavaScript.

## Example 1: Handling Numbers

```javascript
const number = 10;
const result = typeof number === 'number' ? number * 2 : 'Invalid input';
console.log(result);  // Output: 20
```

In this example, we use the `typeof` operator to check if the `number` variable is of type `'number'`. If it is, we multiply the number by 2. Otherwise, we assign the string `'Invalid input'` to the `result` variable.

## Example 2: Handling Strings

```javascript
const name = 'John';
const greeting = `Hello, ${typeof name === 'string' ? name : 'Stranger'}!`;
console.log(greeting);  // Output: Hello, John!
```

In this case, we use a template literal to create a greeting message. The condition inside the ternary operation checks if `name` is of type `'string'`. If it is, we include the name in the greeting. Otherwise, we use the string `'Stranger'`.

## Example 3: Handling Booleans

```javascript
const loggedIn = true;
const message = loggedIn ? 'Welcome back!' : 'Please log in.';
console.log(message);  // Output: Welcome back!
```

Here, we use the boolean value of `loggedIn` to determine the message to display. If `loggedIn` is `true`, we show the welcome message; otherwise, we prompt the user to log in.

## Example 4: Handling Objects

```javascript
const user = { name: 'Jane', age: 25, isAdmin: true };
const adminStatus = user.isAdmin ? 'Admin' : 'User';
console.log(adminStatus);  // Output: Admin
```

In this example, we have an `isAdmin` property inside the `user` object. The ternary operation evaluates the value of `user.isAdmin` and assigns either `'Admin'` or `'User'` to the `adminStatus` variable depending on the result.

Using ternary operations allows you to handle multiple data types in a concise and readable way. By leveraging these conditional expressions, you can write more flexible and robust JavaScript code.

#JavaScript #TernaryOperations