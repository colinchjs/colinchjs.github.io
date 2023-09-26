---
layout: post
title: "Using Map object for memoization in JavaScript"
description: " "
date: 2023-09-23
tags: [memoization]
comments: true
share: true
---

Memoization is a technique used in computer programming to cache the results of a function call and return the cached value for subsequent calls to the same inputs. This can greatly improve the performance of a function by avoiding redundant computations.

In JavaScript, one way to implement memoization is by using the `Map` object. `Map` is a built-in data structure that allows you to store key-value pairs, similar to objects but with some additional features.

Here's an example of how you can use the `Map` object for memoization:

```javascript
// Create a new Map object
const cache = new Map();

// Define the function you want to memoize
function expensiveFunction(n) {
  // Check if the result is already memoized
  if (cache.has(n)) {
    console.log("Fetching from cache...");
    return cache.get(n);
  }

  // Perform the expensive computation
  console.log("Computing...");
  const result = n * n;

  // Memoize the result
  cache.set(n, result);

  return result;
}

// Call the expensive function multiple times
console.log(expensiveFunction(5)); // Output: Computing... 25
console.log(expensiveFunction(5)); // Output: Fetching from cache... 25
console.log(expensiveFunction(10)); // Output: Computing... 100
console.log(expensiveFunction(10)); // Output: Fetching from cache... 100
```

In the example above, we use a `Map` called `cache` to store the memoized results. Before computing the expensive function, we check if the result is already stored in the `cache` by calling `cache.has(n)`. If the result is in the `cache`, we simply retrieve it using `cache.get(n)`. Otherwise, we perform the computation and store the result in the `cache` using `cache.set(n, result)`.

By using the `Map` object for memoization, we can avoid redundant computations and improve the overall performance of our code. This can be especially useful when dealing with computationally expensive tasks or recursive functions.

#javascript #memoization