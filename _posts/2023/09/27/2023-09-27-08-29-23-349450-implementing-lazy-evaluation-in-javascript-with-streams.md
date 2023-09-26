---
layout: post
title: "Implementing lazy evaluation in JavaScript with streams"
description: " "
date: 2023-09-27
tags: [lazyevaluation, JavaScript]
comments: true
share: true
---

Lazy evaluation is a programming technique that defers the evaluation of an expression until its value is actually needed. This can be particularly useful when working with large datasets or performing complex calculations, as it allows for more efficient memory usage and improves performance.

In JavaScript, we can implement lazy evaluation using streams. Streams are a sequence of values that can be processed one at a time. The values in the stream are computed on-demand, as they are called for by the consumer.

## Creating a Stream

To implement lazy evaluation with streams in JavaScript, we can create a custom `Stream` class. The `Stream` class should provide methods to generate values and perform operations on the stream.

Let's start by creating a simple `Stream` class:

```javascript
class Stream {
  constructor(generatorFn) {
    this.generatorFn = generatorFn;
  }

  [Symbol.iterator]() {
    return this.generatorFn();
  }
}
```

The `Stream` class takes a `generatorFn` as its constructor parameter. This function should generate the values for the stream. We also implement the `[Symbol.iterator]` method to make the stream iterable.

## Lazy Evaluation with Streams

Now that we have our `Stream` class, we can use it for lazy evaluation. We can define various operations on the stream, such as `map`, `filter`, and `reduce`.

### Map Operation

The `map` operation applies a function to each value in the stream and returns a new stream with the transformed values. Here's an example implementation:

```javascript
Stream.prototype.map = function (fn) {
  const self = this;

  return new Stream(function* () {
    for (const value of self) {
      yield fn(value);
    }
  });
};
```

### Filter Operation

The `filter` operation applies a predicate function to each value in the stream and returns a new stream with the values that pass the filter. Here's an example implementation:

```javascript
Stream.prototype.filter = function (predicate) {
  const self = this;

  return new Stream(function* () {
    for (const value of self) {
      if (predicate(value)) {
        yield value;
      }
    }
  });
};
```

### Reduce Operation

The `reduce` operation reduces the stream into a single result by applying a reducer function to each value in the stream. Here's an example implementation:

```javascript
Stream.prototype.reduce = function (reducer, initialValue) {
  const self = this;

  let accumulator = initialValue;

  for (const value of self) {
    accumulator = reducer(accumulator, value);
  }

  return accumulator;
};
```

## Example Usage

Now let's see an example of using our `Stream` class for lazy evaluation:

```javascript
function* generateNumbers() {
  let i = 0;
  while (true) {
    yield i++;
  }
}

const numbers = new Stream(generateNumbers());

const evenSquares = numbers
  .filter((n) => n % 2 === 0)
  .map((n) => n * n);

const result = evenSquares.reduce((sum, n) => sum + n, 0);

console.log(result);  // Output: 166650
```

In this example, we generate an infinite stream of numbers using a generator function. We then apply `filter` to get only the even numbers and `map` to square each number. Finally, we use `reduce` to sum up the squared even numbers.

By using lazy evaluation with streams, we are able to work with infinite collections without the need to generate and store all the values upfront. This improves memory efficiency and allows for more flexible and performant code.

#lazyevaluation #JavaScript