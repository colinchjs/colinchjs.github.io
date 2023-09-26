---
layout: post
title: "Lazy evaluation in JavaScript memoization"
description: " "
date: 2023-09-27
tags: [programming, memoization]
comments: true
share: true
---

Lazy evaluation is a technique used in programming languages to defer the evaluation of an expression until it is needed. This can result in improved performance and efficiency, especially in scenarios where the evaluation of an expression is expensive or time-consuming. One common use case for lazy evaluation is memoization, which involves caching the results of function calls to avoid redundant computations.

## Memoization in JavaScript

Memoization is a powerful technique that can be used to optimize function performance by caching the results of function calls based on their input parameters. This allows subsequent calls with the same input parameters to retrieve the previously computed result from the cache, instead of recalculating it.

## Implementing Memoization in JavaScript

Let's take a look at an example of how to implement memoization in JavaScript.

```javascript
// 1. Create a memoize function that takes in a function as an argument
function memoize(fn) {
  // 2. Create an empty cache object
  const cache = {};

  // 3. Return a new function that acts as a wrapper around the original function
  return function (...args) {
    // 4. Convert the arguments into a string as the cache key
    const key = JSON.stringify(args);

    // 5. If the cache contains the result, return it
    if (cache[key]) {
      return cache[key];
    }

    // 6. Otherwise, compute the result and store it in the cache
    const result = fn.apply(this, args);
    cache[key] = result;

    // 7. Return the result
    return result;
  };
}

// Example usage

// A costly computation function
function fibonacci(n) {
  if (n <= 1) {
    return n;
  }

  return fibonacci(n - 1) + fibonacci(n - 2);
}

// Apply memoization to the fibonacci function
const memoizedFibonacci = memoize(fibonacci);

// Call the memoized fibonacci function
console.log(memoizedFibonacci(10));  // Output: 55 (computed)
console.log(memoizedFibonacci(10));  // Output: 55 (cached)
```

In the above example, we define a `memoize` function that takes in a function as an argument. It creates an empty cache object and returns a new function that acts as a wrapper around the original function. The wrapper function checks if the cache contains the result for the given input arguments. If the result exists in the cache, it is returned. Otherwise, the original function is called and the result is stored in the cache. Subsequent calls with the same arguments will retrieve the cached result, avoiding unnecessary computation.

By using memoization, we can significantly improve the performance of expensive or repetitive computations in JavaScript, reducing the overall execution time of our programs.

#programming #javascript #memoization