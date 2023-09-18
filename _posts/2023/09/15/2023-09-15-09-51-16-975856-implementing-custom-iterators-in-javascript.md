---
layout: post
title: "Implementing custom iterators in JavaScript"
description: " "
date: 2023-09-15
tags: [iterators]
comments: true
share: true
---

JavaScript provides built-in iterators like `for...of` and `Array.prototype.forEach()` to iterate over data structures like arrays and objects. However, there may be cases where you need to create your own custom iterator to iterate over a custom data structure or to have better control over the iteration process.

In this blog post, we will explore how to implement custom iterators in JavaScript to iterate over your own data structures.

## What is an Iterator?

An iterator is an object that provides a sequence of values or elements one at a time. It allows you to traverse through a collection or iterable object, providing you with the ability to access each item in the sequence or perform actions on them.

In JavaScript, an iterator is an object that must define a `next()` method. This method should return an object with two properties: `value` (the next value in the sequence) and `done` (a boolean indicating if there are any more values in the sequence).

## Creating a Custom Iterator

To create a custom iterator in JavaScript, you need to define an object that implements the `Iterable` and `Iterator` protocols. The `Iterable` protocol requires the object to have a `Symbol.iterator` method that returns the iterator object itself. The `Iterator` protocol requires the iterator object to have a `next()` method.

Let's take a look at an example of implementing a custom iterator for a custom data structure - a linked list.

```javascript
class Node {
  constructor(value, next = null) {
    this.value = value;
    this.next = next;
  }
}

class LinkedList {
  constructor() {
    this.head = null;
  }

  [Symbol.iterator]() {
    let current = this.head;

    return {
      next: () => {
        if (current) {
          const value = current.value;
          current = current.next;
          return { value, done: false };
        }
        
        return { done: true };
      }
    };
  }

  add(value) {
    const newNode = new Node(value);
    
    if (!this.head) {
      this.head = newNode;
    } else {
      let current = this.head;
      while (current.next) {
        current = current.next;
      }
      current.next = newNode;
    }
  }
}

// Usage
const list = new LinkedList();
list.add(1);
list.add(2);
list.add(3);

for (const value of list) {
  console.log(value);
}
```

In this example, we have a `LinkedList` class that represents a linked list data structure. The `LinkedList` class implements the `Symbol.iterator` method, returning an iterator object. The iterator object's `next()` method is implemented to traverse through the linked list and return the next value in the sequence.

The `LinkedList` class also has an `add()` method to add nodes to the linked list.

To iterate over the linked list, we can use the `for...of` loop, which automatically calls the iterator's `next()` method on each iteration.

## Conclusion

Implementing custom iterators in JavaScript allows you to have fine-grained control over the iteration process for your custom data structures. By implementing the `Iterable` and `Iterator` protocols, you can create iterators that can be used with the `for...of` loop or other iterator-consuming functions.

Custom iterators can be useful in scenarios where you need to iterate over complex data structures, perform operations on each element, or have more control over the iteration process.

#javascript #iterators