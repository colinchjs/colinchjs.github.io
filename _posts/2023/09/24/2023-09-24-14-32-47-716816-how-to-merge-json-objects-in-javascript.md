---
layout: post
title: "How to merge JSON objects in JavaScript."
description: " "
date: 2023-09-24
tags: [javascript, JSON]
comments: true
share: true
---

Merging JSON objects in JavaScript can be useful when you want to combine multiple JSON objects into a single object. This allows you to consolidate data from multiple sources or manipulate the structure of the JSON objects. In this article, we'll explore three different methods to achieve this.

## Method 1: Using the Spread Operator

One way to merge JSON objects is by using the spread operator (`...`). The spread operator allows us to expand an object or array into individual components. Here's an example:

```javascript
const obj1 = { name: "John", age: 30 };
const obj2 = { address: "123 Main St", city: "New York" };

const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj);
```

Output:
```
{ name: "John", age: 30, address: "123 Main St", city: "New York" }
```

In this example, we use the spread operator to copy the key-value pairs from `obj1` and `obj2` into `mergedObj`.

## Method 2: Using `Object.assign()`

Another way to merge JSON objects is by using the `Object.assign()` method. This method copies the values of all enumerable properties from one or more source objects to a target object. Here's an example:

```javascript
const obj1 = { name: "John", age: 30 };
const obj2 = { address: "123 Main St", city: "New York" };

const mergedObj = Object.assign({}, obj1, obj2);

console.log(mergedObj);
```

Output:
```
{ name: "John", age: 30, address: "123 Main St", city: "New York" }
```

In this example, we use `Object.assign()` to merge the properties of `obj1` and `obj2` into `{}` (empty object).

## Method 3: Using `JSON.parse()` and `JSON.stringify()`

Sometimes, if the JSON objects are stored as strings, you can merge them by parsing the strings into objects, merging the objects, and then converting them back into a JSON string. Here's an example:

```javascript
const jsonStr1 = '{"name": "John", "age": 30}';
const jsonStr2 = '{"address": "123 Main St", "city": "New York"}';

const obj1 = JSON.parse(jsonStr1);
const obj2 = JSON.parse(jsonStr2);

const mergedObj = { ...obj1, ...obj2 };

const mergedJsonStr = JSON.stringify(mergedObj);

console.log(mergedJsonStr);
```

Output:
```
{"name":"John","age":30,"address":"123 Main St","city":"New York"}
```

In this example, we parse the JSON strings `jsonStr1` and `jsonStr2` into objects using `JSON.parse()`, merge the objects using the spread operator, and then convert the merged object back into a JSON string using `JSON.stringify()`.

## Conclusion

Merging JSON objects is a common operation in JavaScript when dealing with JSON data. Whether you choose to use the spread operator, `Object.assign()`, or `JSON.parse()` and `JSON.stringify()`, all three methods can help you combine and manipulate JSON objects effectively.

#javascript #JSON #object #merge