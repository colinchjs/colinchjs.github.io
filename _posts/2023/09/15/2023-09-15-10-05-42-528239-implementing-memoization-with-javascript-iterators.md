---
layout: post
title: "Implementing memoization with JavaScript iterators"
description: " "
date: 2023-09-15
tags: []
comments: true
share: true
---

Memoization is a technique used to optimize the performance of a function by caching the results of previous function calls. It can significantly improve the execution time of functions that are computationally expensive or involve repetitive calculations. In JavaScript, iterators provide an elegant way to implement memoization.

## What is an Iterator?

An iterator is an object that defines a sequence and potentially a return value upon its termination. It provides a uniform interface for traversing data structures, such as arrays, maps, sets, and custom data structures. Iterators have a `next()` method which returns the next value in the sequence along with a boolean indicating if the sequence has reached its end.

## Implementing Memoization with Iterators

To implement memoization with iterators, we can create a higher-order function that takes a function as an argument and returns a memoized version of the function. Here's an example:

```javascript
function memoize(fn) {
  const cache = new Map();

  return function*(...args) {
    const key = JSON.stringify(args);

    if (cache.has(key)) {
      yield* cache.get(key);
    } else {
      const result = fn(...args);
      cache.set(key, result);
      yield* result;
    }
  }
}
```

In the above code, we've defined a function called `memoize` that takes a function `fn` as an argument. Inside the `memoize` function, we create a `cache` object using a `Map` to store the previously computed results.

The returned function is a generator function denoted by the asterisk (*) before the function keyword. It takes any number of arguments using the spread syntax `(...args)`.

Inside the returned function, we generate a unique `key` by stringifying the arguments using `JSON.stringify`. We first check if the `cache` has a matching `key`. If it does, we yield the memoized result using the `yield*` syntax, which iterates over the cached result.

If the `cache` does not have the `key`, we compute the result by invoking the original function `fn` with the arguments. We cache the result by setting the `key` along with the computed result using `cache.set(key, result)`. Finally, we yield the computed result.

## Using Memoization with Iterators

Now, let's see how we can use the memoization function with an example. Consider a function that generates a Fibonacci sequence up to a given number:

```javascript
function* fibonacciGenerator(limit) {
  let [prev, current] = [0, 1];

  while (current <= limit) {
    yield current;
    [prev, current] = [current, prev + current];
  }
}

const memoizedFibonacci = memoize(fibonacciGenerator);
```

In the code above, we define a generator function `fibonacciGenerator` that generates Fibonacci numbers up to a given `limit`. We then create a memoized version of the `fibonacciGenerator` function using our `memoize` function.

Now, whenever we call the `memoizedFibonacci` function, it will first check if the result for the given arguments has already been cached. If it has, it will return the memoized result; otherwise, it will compute the result and cache it for future use.

```javascript
for (const value of memoizedFibonacci(100)) {
  console.log(value);
}

// Output: 1 1 2 3 5 8 13 21 34 55 89
```

In the example above, we iterate over the Fibonacci sequence up to `100` using the `memoizedFibonacci` function. The result is printed to the console, and we can see that the Fibonacci sequence is generated correctly.

## Conclusion

Implementing memoization with JavaScript iterators can greatly optimize the performance of functions by caching the results of previous function calls. By using the `yield*` syntax to iterate over cached results, we can efficiently handle computations and repetitive calculations. Memoization is particularly effective for functions with expensive computations or those that are repeatedly called with the same arguments.