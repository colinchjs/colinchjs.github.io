---
layout: post
title: "Iterating over a Map object using forEach()"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

To iterate over a `Map` object using `forEach()`, you can follow these steps:

1. Create a `Map` object and populate it with key-value pairs. Here's an example:

```javascript
const map = new Map();
map.set('key1', 'value1');
map.set('key2', 'value2');
map.set('key3', 'value3');
```

2. Use the `forEach()` method to iterate over the `Map` object.

```javascript
map.forEach((value, key) => {
   console.log(`Key: ${key}, Value: ${value}`);
});
```

In the above code, we pass a callback function to `forEach()` that takes two parameters: `value` and `key`. The function is executed for each entry in the `Map`, and the current `value` and `key` are passed as arguments to the callback function.

You can perform any desired operations inside the callback function. In this example, we simply log each key-value pair to the console.

Note: The order of iteration in a `Map` object is based on the order of insertion.