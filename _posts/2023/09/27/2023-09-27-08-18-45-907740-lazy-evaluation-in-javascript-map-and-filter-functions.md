---
layout: post
title: "Lazy evaluation in JavaScript map and filter functions"
description: " "
date: 2023-09-27
tags: [lazyevaluation]
comments: true
share: true
---

Lazy evaluation is a powerful technique in programming that allows for efficient computation by deferring the evaluation of expressions until they are actually needed. JavaScript map and filter functions are commonly used to iterate over arrays and manipulate their elements. In this blog post, we will explore how lazy evaluation can be applied to these array functions, resulting in improved performance.

## Lazy Evaluation with the map function

The `map` function in JavaScript is used to iterate over an array and transform each element based on a given transformation function. By default, `map` creates a new array with the results of applying the provided function to each element of the original array.

However, we can achieve lazy evaluation by wrapping the transformation function inside a generator function. This ensures that the transformation is only applied when the generated value is actually consumed. Let's see an example:

```javascript
const arr = [1, 2, 3, 4, 5];

function* mapGenerator(array, transformation) {
  for (let i = 0; i < array.length; i++) {
    yield transformation(array[i]);
  }
}

const lazyMapped = mapGenerator(arr, x => x * 2);

// Only when the value is consumed, the transformation is applied
console.log(lazyMapped.next().value); // Output: 2
console.log(lazyMapped.next().value); // Output: 4
console.log(lazyMapped.next().value); // Output: 6
```

In this example, the `mapGenerator` function uses the `yield` keyword to return the transformed value lazily. By calling `next()` on the `lazyMapped` iterator, we are able to consume the values one by one, and the transformation is only applied at the time of consumption.

## Lazy Evaluation with the filter function

The `filter` function in JavaScript is used to iterate over an array and return a new array with elements that satisfy a given condition. Similar to `map`, we can apply lazy evaluation to the `filter` function by using a generator function. Take a look at the example code below:

```javascript
const arr = [1, 2, 3, 4, 5];

function* filterGenerator(array, condition) {
  for (let i = 0; i < array.length; i++) {
    if (condition(array[i])) {
      yield array[i];
    }
  }
}

const lazyFiltered = filterGenerator(arr, x => x % 2 === 0);

// Only elements that satisfy the condition are returned
console.log(lazyFiltered.next().value); // Output: 2
console.log(lazyFiltered.next().value); // Output: 4
```

In this case, we have the `filterGenerator` function that yields elements of the array that satisfy the condition provided. By using the generator function, the filtered elements are only produced when they are actually requested.

## Conclusion

Lazy evaluation can be a useful technique when working with array transformations using the `map` and `filter` functions in JavaScript. By deferring the evaluation of expressions until they are needed, we can achieve better performance and memory efficiency. Embracing lazy evaluation allows for the efficient manipulation of large arrays with reduced resource consumption.

#javascript #lazyevaluation