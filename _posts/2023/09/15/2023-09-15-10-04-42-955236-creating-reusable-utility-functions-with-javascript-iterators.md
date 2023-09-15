---
layout: post
title: "Creating reusable utility functions with JavaScript iterators"
description: " "
date: 2023-09-15
tags: [iterators]
comments: true
share: true
---

In JavaScript, iterators and generators are powerful features that allow us to iterate over data structures and manipulate them in a clean and concise manner. By leveraging iterators, we can create reusable utility functions that can perform various operations on different data types. In this blog post, we will explore how to create such utility functions using JavaScript iterators.

### What are iterators?

Iterators in JavaScript are objects that implement the iterator protocol. They provide a way to access elements of a collection one at a time, while being able to maintain their internal state. Iterators follow a specific structure with a `next()` method that returns the next value in the iteration sequence, along with a boolean `done` property that indicates if there are any more values left to be iterated over.

### Utility functions with iterators

One of the main advantages of iterators is that they allow us to abstract away the complexity of iterating over different data structures. We can create utility functions that encapsulate common operations that can be performed on arrays, sets, maps, and other iterable objects.

Let's take a look at an example utility function called `filter`. This function takes an iterable object and a predicate function as parameters, and returns a new iterable object that contains only the elements that satisfy the predicate.

```javascript
function* filter(iterable, predicate) {
  for (const item of iterable) {
    if (predicate(item)) {
      yield item;
    }
  }
}

// Usage example
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = [...filter(numbers, number => number % 2 === 0)];
console.log(evenNumbers); // Output: [2, 4]
```

In this example, the `filter` function uses a generator function (`function*`) to create an iterable object. It iterates over each item in the input iterable and yields only the items that satisfy the given predicate function.

By using iterators and generator functions, we can easily create utility functions like `map`, `reduce`, `find`, and many others. These functions can be reused across different data structures, making our code more modular and maintainable.

### Conclusion

JavaScript iterators provide a powerful mechanism for creating reusable utility functions that can operate on various data types. By encapsulating common operations in iterable objects, we can write cleaner and more maintainable code. Whether it's filtering an array, mapping over a set, or reducing a map, iterators allow us to abstract away the details of iteration and focus on the logic of our utility functions.

#JS #iterators