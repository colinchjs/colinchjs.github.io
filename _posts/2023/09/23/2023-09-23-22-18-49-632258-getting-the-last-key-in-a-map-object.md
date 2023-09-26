---
layout: post
title: "Getting the last key in a Map object"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

Method #1: Using the `Array.from()` method

One way to get the last key in a `Map` object is by using the `Array.from()` method, which converts an iterable object into an array. Here's an example:

```javascript
const myMap = new Map();
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

const lastKey = Array.from(myMap.keys()).pop();

console.log(lastKey); // Output: key3
```

In this example, we first create a `Map` object called `myMap` and add some key-value pairs to it. Then, we use `Array.from()` to convert the keys of the map into an array. Finally, we apply the `pop()` method on the array, which removes and returns the last element, giving us the last key.

Method #2: Looping through the `Map` object

Another way to get the last key in a `Map` object is by using a loop to iterate over the keys and keep track of the last key encountered. Here's an example:

```javascript
const myMap = new Map();
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

let lastKey;
for (const key of myMap.keys()) {
  lastKey = key;
}

console.log(lastKey); // Output: key3
```

In this example, we define a variable `lastKey` outside the loop and update it with each iteration of the loop. At the end, `lastKey` will hold the last key encountered in the loop, which is the desired result.

Both methods provide a way to retrieve the last key in a `Map` object in JavaScript. Depending on your specific use case, choose the method that best suits your needs.

#JavaScript #Map