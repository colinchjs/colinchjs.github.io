---
layout: post
title: "Using non-unique keys in a Map object"
description: " "
date: 2023-09-23
tags: [programming, maps]
comments: true
share: true
---

Maps are an important data structure in programming that allow you to store key-value pairs. In most programming languages, each key within a map must be unique, meaning you cannot have multiple values associated with the same key. However, in certain cases, you may need to use non-unique keys in a Map object. In this article, we will explore how to achieve this behavior.

## Traditional Map Behavior

By default, when you add a key-value pair to a map, if the key already exists, the existing value will be replaced with the new value. For example, consider the following code snippet in JavaScript:

```javascript
const map = new Map();
map.set('apple', 5);
map.set('banana', 3);
map.set('apple', 7);

console.log(map.get('apple')); // Output: 7
```

In this example, the value associated with the key 'apple' is initially set to 5, but it is later overridden with a new value of 7.

## Using an Array or Object as Key

To use non-unique keys in a Map object, you can utilize an array or object as the key. Since arrays and objects are reference types in most programming languages, they can be used as keys because their reference values remain unique, even if their content changes.

Let's take a look at an example using JavaScript:

```javascript
const map = new Map();
const key1 = { id: 1 };
const key2 = { id: 2 };

map.set(key1, 'Value 1');
map.set(key2, 'Value 2');
map.set(key1, 'New Value');

console.log(map.get(key1)); // Output: New Value
```

In this example, we create two unique objects `key1` and `key2` and use them as keys in the map. Even though `key1` is assigned a new value, it still retains its uniqueness as a key.

Similarly, you can use arrays or objects as keys in other programming languages like Python, Java, or C++ with their respective Map implementations.

## Conclusion

In situations where you need non-unique keys within a Map object, using an array or object as the key is a viable solution. By understanding the reference behavior of these data types, you can work around the traditional requirement of unique keys and store multiple values associated with a single key in a Map object.

#programming #maps