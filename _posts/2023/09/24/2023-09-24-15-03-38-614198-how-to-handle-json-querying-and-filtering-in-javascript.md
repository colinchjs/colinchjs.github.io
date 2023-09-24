---
layout: post
title: "How to handle JSON querying and filtering in JavaScript."
description: " "
date: 2023-09-24
tags: [javascript, JSON]
comments: true
share: true
---

JSON (JavaScript Object Notation) is a widely used data format for storing and transmitting data. In JavaScript, dealing with JSON data is a common task, especially when working with APIs or processing data.

In this blog post, we will explore different techniques for querying and filtering JSON data in JavaScript.

## 1. Accessing JSON Properties

To access properties in JSON data, you can use dot notation or square bracket notation. Dot notation is used when you know the property name in advance, whereas square bracket notation is useful when the property name is dynamic or contains special characters.

```javascript
const json = {
  name: "John",
  age: 30,
  address: {
    street: "123 Main Street",
    city: "New York"
  }
};

console.log(json.name); // Output: John
console.log(json["age"]); // Output: 30
console.log(json.address.street); // Output: 123 Main Street
```

## 2. Filtering JSON Arrays

If you have an array of JSON objects and need to filter it based on certain criteria, you can use the `filter()` method. This method creates a new array containing elements that meet the specified condition.

```javascript
const data = [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 },
  { name: "Smith", age: 35 }
];

const filteredData = data.filter((item) => item.age > 30);
console.log(filteredData);
// Output: [{ name: "Smith", age: 35 }]
```

## 3. Querying JSON with Lodash

Lodash is a popular JavaScript utility library that provides useful functions for working with arrays, objects, and more. It includes a powerful querying and filtering API for JSON data.

First, install lodash using npm:

```bash
npm install lodash
```

Then, import the necessary functions and use them to query and filter JSON data:

```javascript
const _ = require('lodash');

const data = [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 },
  { name: "Smith", age: 35 }
];

const filteredData = _.filter(data, { age: 30 });
console.log(filteredData);
// Output: [{ name: "John", age: 30 }]

const sortedData = _.sortBy(data, 'age');
console.log(sortedData);
// Output: [{ name: "Jane", age: 25 }, { name: "John", age: 30 }, { name: "Smith", age: 35 }]
```

## Conclusion

Handling JSON querying and filtering in JavaScript is an essential skill for working with JSON data effectively. By understanding how to access properties, filter arrays, and use utility libraries like Lodash, you can easily manipulate and extract the information you need.

#javascript #JSON