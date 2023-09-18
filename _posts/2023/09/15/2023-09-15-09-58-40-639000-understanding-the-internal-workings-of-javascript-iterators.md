---
layout: post
title: "Understanding the internal workings of JavaScript iterators"
description: " "
date: 2023-09-15
tags: [Iterators]
comments: true
share: true
---

An iterator is an object with a specific interface that allows you to traverse a collection one element at a time. The primary methods of an iterator are `next()` and `return()`. 

The `next()` method returns an object with two properties: `value` and `done`. The `value` property represents the current element of the collection, while the `done` property indicates whether there are any more elements to iterate over.

You can use a `for...of` loop to iterate over an iterator. This loop continuously calls the `next()` method until the `done` property of the returned object is `true`:

```javascript
const myArray = [1, 2, 3, 4, 5];
const iterator = myArray[Symbol.iterator]();

for (const element of iterator) {
    console.log(element);
}
```

In the above code, we use the `Symbol.iterator` property to obtain the iterator for the `myArray` object. Then, we use a `for...of` loop to iterate over the elements of the array.

Iterators can also be used with other JavaScript built-in objects such as strings, maps, and sets. The internal implementation of iterators varies depending on the object they are iterating over.

To create your own iterator, you need to implement the iterator protocol. The iterator protocol requires implementing a method named `next()` that returns the next value of the collection. Here's an example of a custom iterator:

```javascript
const myCustomIterable = {
    values: [1, 2, 3, 4, 5],
    [Symbol.iterator]() {
        let index = 0;
        return {
            next: () => {
                if (index < this.values.length) {
                    return {
                        value: this.values[index++],
                        done: false
                    };
                } else {
                    return {
                        done: true
                    };
                }
            }
        }
    }
};

for (const element of myCustomIterable) {
    console.log(element);
}
```

In this example, we create a custom iterable object with an array of values `values`. We implement the `Symbol.iterator` method to return an iterator object with the `next()` method. The `next()` method increments an `index` variable and returns the next value of the array until the end is reached.

Understanding the internal workings of JavaScript iterators can help you leverage their power and write more efficient code. Whether you're working with built-in objects or creating your own custom iterators, iterators are a handy tool to master. #JavaScript #Iterators