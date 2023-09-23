---
layout: post
title: "Getting the first value in a Map object"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

```javascript
const myMap = new Map();
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

const firstValue = [...myMap.values()][0];
console.log(firstValue); // Output: value1
```

In the above code, we create a new Map object called `myMap` and add key-value pairs to it. To retrieve all the values from the Map, we use the `values()` method and convert it to an array using the spread operator (`...`). Finally, we access the first element of the array using `[0]` and assign it to the `firstValue` variable.