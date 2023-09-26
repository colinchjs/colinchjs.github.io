---
layout: post
title: "How to loop through JSON data in JavaScript."
description: " "
date: 2023-09-24
tags: [JSON]
comments: true
share: true
---

JSON (JavaScript Object Notation) is a popular data format commonly used for sending and receiving data in web applications. In JavaScript, looping through JSON data allows us to access and manipulate the data efficiently. In this tutorial, we will explore different techniques to loop through JSON data in JavaScript.

## 1. Looping through an Array of JSON Objects

If your JSON data consists of an array of JSON objects, you can use a for loop or forEach loop to iterate through the array and access the properties of each object.

```javascript
const jsonData = [
  { "name": "John", "age": 25 },
  { "name": "Alice", "age": 30 },
  { "name": "Bob", "age": 35 }
];

// Using a for loop
for (let i = 0; i < jsonData.length; i++) {
  console.log(jsonData[i].name);
  console.log(jsonData[i].age);
}

// Using forEach loop
jsonData.forEach(obj => {
  console.log(obj.name);
  console.log(obj.age);
});
```

## 2. Looping through a JSON Object

If your JSON data is an object with key-value pairs, you can use a for...in loop or Object.keys() method to loop through the object.

```javascript
const jsonData = {
  "name": "John",
  "age": 25,
  "email": "john@example.com"
};

// Using a for...in loop
for (let key in jsonData) {
  console.log(key + ": " + jsonData[key]);
}

// Using Object.keys()
Object.keys(jsonData).forEach(key => {
  console.log(key + ": " + jsonData[key]);
});
```

## Conclusion

Looping through JSON data is a fundamental skill in JavaScript as it allows you to access and manipulate the data effectively. Whether you have an array of JSON objects or a JSON object with key-value pairs, you can choose the appropriate looping technique to iterate through the data. By understanding these techniques, you can utilize JSON data to its full potential in your JavaScript applications.

#javascript #JSON