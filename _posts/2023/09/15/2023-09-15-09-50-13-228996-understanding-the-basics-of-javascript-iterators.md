---
layout: post
title: "Understanding the basics of JavaScript iterators"
description: " "
date: 2023-09-15
tags: [javascript, iterators]
comments: true
share: true
---

## What are iterators?
Iterators are objects that define a sequence and a mechanism for iterating over that sequence. They provide a way to access individual elements of a collection one at a time, without exposing the underlying implementation details of the collection.

## How to use iterators?
To use an iterator, you need to follow a specific pattern:
1. Create an iterator object using the [Symbol.iterator]() method of the collection you want to iterate over.
2. Call the [next]() method on the iterator object to get the next element in the sequence.
3. The [next]() method returns an object with two properties: `value` which represents the current element in the sequence, and `done` which indicates whether there are any more elements in the sequence.

Here's an example of using an iterator to iterate over an array:

```javascript
const fruits = ["apple", "banana", "orange"];
const iterator = fruits[Symbol.iterator]();

let result = null;
while (!(result = iterator.next()).done) {
    console.log(result.value);
}
```

In the code above, we create an iterator object `iterator` using the `[Symbol.iterator]()` method of the array `fruits`. We then iterate over the array using a `while` loop, calling the `next()` method on the iterator object and logging the `value` property to the console.

The output of the above code will be:
```
apple
banana
orange
```

## Iterables and built-in iterables
In JavaScript, an iterable is any object that implements the `[Symbol.iterator]()` method. Arrays, strings, and maps are examples of built-in iterables.

```javascript
const iterableString = "hello";
const iterableArray = [1, 2, 3];
const iterableMap = new Map([["key1", "value1"], ["key2", "value2"]]);

const stringIterator = iterableString[Symbol.iterator]();
const arrayIterator = iterableArray[Symbol.iterator]();
const mapIterator = iterableMap[Symbol.iterator]();

console.log(stringIterator.next().value); // h
console.log(arrayIterator.next().value); // 1
console.log(mapIterator.next().value); // [ 'key1', 'value1' ]
```

In the code above, we create iterator objects `stringIterator`, `arrayIterator`, and `mapIterator` by calling the `[Symbol.iterator]()` method on the different iterables. We then call the `next()` method on each iterator to get the next element in the sequence and log it to the console.

## Conclusion
JavaScript iterators provide a powerful mechanism for iterating over various data structures. Understanding how to use iterators allows you to work with collections efficiently and perform operations on individual elements. Start using iterators in your JavaScript code and take advantage of this powerful feature!

#javascript #iterators