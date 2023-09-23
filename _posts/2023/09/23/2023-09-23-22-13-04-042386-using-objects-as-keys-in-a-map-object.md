---
layout: post
title: "Using objects as keys in a Map object"
description: " "
date: 2023-09-23
tags: [JavaScript, Objects]
comments: true
share: true
---

In JavaScript, the `Map` object is a built-in data structure that allows you to store key-value pairs. By default, the keys in a `Map` are converted to strings. However, sometimes you may want to use objects as keys instead. In this blog post, we will explore how to use objects as keys in a `Map` object.

## Creating a `Map` with object keys

To use objects as keys in a `Map` object, you need to understand how JavaScript handles object equality. In JavaScript, objects are compared by reference, not by their contents. This means that two objects with the same property values are considered different if they are separate instances.

Let's start by creating a `Map` object and using an object as a key:

```javascript
const map = new Map();

const key = { name: 'John' };
const value = 'Some value';

map.set(key, value);

console.log(map.get(key)); // Output: Some value
```

In this example, we create a `Map` object, define an object `key` with a `name` property, and set a value for that key using the `set` method. We can retrieve the value later using the `get` method.

## Using objects with different references

As mentioned earlier, JavaScript compares objects by reference. This means that even if two objects have identical property values, they will be treated as different keys if they are separate instances. Let's see an example:

```javascript
const map = new Map();

const key1 = { name: 'John' };
const key2 = { name: 'John' };
const value1 = 'Value 1';
const value2 = 'Value 2';

map.set(key1, value1);
map.set(key2, value2);

console.log(map.get(key1)); // Output: Value 1
console.log(map.get(key2)); // Output: Value 2
```

In this example, we create two separate objects `key1` and `key2`, both with the same property values. Despite having the same values, they are treated as different keys in the `Map` object.

## Using object references as keys

If you want to use the same object reference as a key, you can store the reference in a variable and use it consistently. Here's an example:

```javascript
const map = new Map();

const key = { name: 'John' };
const value = 'Some value';

map.set(key, value);

console.log(map.get(key)); // Output: Some value

// Changing the object's property does not affect the key
key.name = 'Jane';

console.log(map.get(key)); // Output: Some value
```

In this example, we create an object `key` and set a value for it in the `Map` object. Even if we modify the property of the object, the key in the `Map` remains the same.

## Conclusion

In JavaScript, the `Map` object allows you to use objects as keys, although they are compared using their reference. Understanding how object equality works is crucial when using objects as keys. By keeping these concepts in mind, you can effectively use objects as keys in a `Map` object and handle them accordingly.

#JavaScript #Map #Objects #Keys