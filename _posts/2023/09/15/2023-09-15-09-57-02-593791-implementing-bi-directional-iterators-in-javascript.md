---
layout: post
title: "Implementing bi-directional iterators in JavaScript"
description: " "
date: 2023-09-15
tags: [JavaScript, BiDirectionalIterators]
comments: true
share: true
---

Iterators are an essential part of JavaScript, allowing us to loop over data structures and access their elements in a sequential manner. However, the built-in iterators of JavaScript only support moving forward through an iterable collection. In some scenarios, it can be beneficial to have **bi-directional iterators**, which enable iterating both forwards and backwards.

In this blog post, we will explore how to implement bi-directional iterators in JavaScript and discuss the advantages they offer.

## Bi-Directional Iterators

Bi-directional iterators enhance the capabilities of traditional iterators by allowing traversal in both directions. They provide two primary methods: `next` for moving forward and `previous` for moving backward through the collection. By supporting bidirectional movement, these iterators offer more flexibility and can be valuable in various data processing scenarios.

## Implementation

Let's dive into the implementation of bi-directional iterators in JavaScript. We will create a `BiDirectionalIterator` class that encapsulates the necessary functionality.

```javascript
class BiDirectionalIterator {
  constructor(collection) {
    this.collection = collection;
    this.index = 0;
  }

  next() {
    if (this.index < this.collection.length) {
      return { value: this.collection[this.index++], done: false };
    }
    return { value: null, done: true };
  }

  previous() {
    if (this.index > 0) {
      return { value: this.collection[--this.index], done: false };
    }
    return { value: null, done: true };
  }
}
```

In the above code, we have a `BiDirectionalIterator` class that takes a `collection` as its parameter. It also keeps track of the current `index` which represents the position of the iterator within the collection.

The `next()` method increments the index and returns the current element if it exists, along with a `done` flag indicating whether all elements have been traversed.

The `previous()` method decrements the index and returns the previous element if available, along with the `done` flag.

## Usage Example

Now that we have our bi-directional iterator implemented, let's see how we can make use of it with an example.

```javascript
const myCollection = ['a', 'b', 'c', 'd'];
const iterator = new BiDirectionalIterator(myCollection);

let result = iterator.next();
while (!result.done) {
  console.log(result.value); // Output: a, b, c, d
  result = iterator.next();
}

result = iterator.previous();
while (!result.done) {
  console.log(result.value); // Output: d, c, b, a
  result = iterator.previous();
}
```

In the example above, we create a `BiDirectionalIterator` object with an array `myCollection`. We then use the `next()` method to iterate forwards and the `previous()` method to iterate backwards through the collection. Both loops print the values in the console accordingly.

## Conclusion

Bi-directional iterators provide additional flexibility when working with iterable collections in JavaScript. By enabling traversal in both directions, these iterators enhance the capabilities of traditional iterators. Understanding how to implement and utilize bi-directional iterators can be advantageous in scenarios where bidirectional navigation is required.

#JavaScript #BiDirectionalIterators