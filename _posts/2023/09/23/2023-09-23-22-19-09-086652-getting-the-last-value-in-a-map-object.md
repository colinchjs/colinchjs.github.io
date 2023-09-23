---
layout: post
title: "Getting the last value in a Map object"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

Here's an example of how you can get the last value in a `Map` object:

```javascript
const myMap = new Map();

myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

const values = Array.from(myMap.values());
const lastValue = values[values.length - 1];

console.log(lastValue); // Output: value3
```

In the above example, we create a `Map` object `myMap` and add three key-value pairs to it. We convert the `myMap.values()` iterator into an array using `Array.from()` and store it in the `values` variable. Finally, we retrieve the last value from the `values` array using `values.length - 1` index and assign it to the `lastValue` variable.

Remember to adapt the code to your specific use case.