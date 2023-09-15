---
layout: post
title: "Creating composable functions with JavaScript iterators"
description: " "
date: 2023-09-15
tags: [javascript, iterators]
comments: true
share: true
---

In JavaScript, iterators provide a powerful way to work with collections of data. They allow us to iterate over items one by one, providing a streamlined way to perform operations on the data.

One of the benefits of working with iterators is the ability to create composable functions. Composable functions are functions that can be combined and chained together to create more complex operations.

Let's explore how we can create composable functions using JavaScript iterators.

## Example scenario

Let's say we have an array of numbers and we want to perform multiple operations on it. We want to filter out even numbers, square each number, and then sum them all up.

### Step 1: Create the iterator

We start by creating an iterator from our array of numbers using the `Symbol.iterator` method:

```javascript
const numbers = [1, 2, 3, 4, 5];
const iterator = numbers[Symbol.iterator]();
```

### Step 2: Define composable functions

Next, we define three composable functions: `filter`, `map`, and `reduce`.

#### 1. `filter`

The `filter` function takes a callback as an argument and only returns the items that satisfy the provided condition:

```javascript
function* filter(iterator, condition) {
  for (const item of iterator) {
    if (condition(item)) {
      yield item;
    }
  }
}
```

#### 2. `map`

The `map` function takes a callback as an argument and applies the provided function to each item:

```javascript
function* map(iterator, transform) {
  for (const item of iterator) {
    yield transform(item);
  }
}
```

#### 3. `reduce`

The `reduce` function takes a callback as an argument and aggregates the items into a single value:

```javascript
function reduce(iterator, callback, initialValue) {
  let accumulator = initialValue;

  for (const item of iterator) {
    accumulator = callback(accumulator, item);
  }

  return accumulator;
}
```

### Step 3: Chain the composable functions

Now, we can chain the composable functions together to perform the desired operations:

```javascript
const result = reduce(
  map(
    filter(numbers[Symbol.iterator](), num => num % 2 === 0),
    num => num ** 2
  ),
  (sum, num) => sum + num,
  0
);

console.log(result); // Output: 20
```

Here, we first filter out the even numbers, then square each number, and finally, sum them up.

## Conclusion

By leveraging JavaScript iterators, we are able to create composable functions that allow us to perform complex operations on collections of data. This composability enables us to write more concise and reusable code, enhancing the overall maintainability and flexibility of our applications.

#javascript #iterators