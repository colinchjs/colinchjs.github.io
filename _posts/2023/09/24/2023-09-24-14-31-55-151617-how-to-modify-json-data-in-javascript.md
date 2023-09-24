---
layout: post
title: "How to modify JSON data in JavaScript."
description: " "
date: 2023-09-24
tags: [JSON, JavaScript]
comments: true
share: true
---

JSON (JavaScript Object Notation) is a widely used format for data interchange. It is commonly used to transmit data between a server and a web application. Modifying JSON data in JavaScript is a common task when working with APIs or handling data received from external sources.

In this blog post, we will explore different techniques to modify JSON data in JavaScript.

## Accessing JSON data

Before modifying JSON data, we need to access the specific properties or values we want to modify. JavaScript provides a simple way to access and manipulate JSON data through the `JSON.parse()` function. This function parses the JSON string and converts it into a JavaScript object.

Here's an example:

```javascript
let jsonString = `{"name": "John", "age": 30, "city": "New York"}`;
let data = JSON.parse(jsonString);

// Accessing properties
console.log(data.name); // "John"
console.log(data.age); // 30
console.log(data.city); // "New York"
```

## Modifying JSON data

Once we have accessed the JSON data, we can modify its properties or values using JavaScript. There are several approaches to modify JSON data based on the specific requirements.

### Approach 1: Direct assignment

The simplest way to modify JSON data is by directly assigning new values to the properties. We can directly access the properties using dot notation or bracket notation and assign new values.

```javascript
data.name = "Jane";
data.age = 35;
data.city = "San Francisco";
```

### Approach 2: Using `Object.assign()`

The `Object.assign()` method is helpful when we want to merge multiple objects or update specific properties of an object.

```javascript
Object.assign(data, { name: "Jane", age: 35, city: "San Francisco" });
```

### Approach 3: Using spread syntax

The spread syntax is another way to modify JSON data by copying existing properties and adding or updating specific properties.

```javascript
data = { ...data, name: "Jane", age: 35, city: "San Francisco" };
```

### Approach 4: Using lodash library

If you prefer a library, **lodash** provides a simple and efficient way to modify JSON data with its `_.assign()` method.

```javascript
_.assign(data, { name: "Jane", age: 35, city: "San Francisco" });
```

## Converting modified data back to JSON

After modifying the JSON data, if we want to convert it back to a JSON string, we can use the `JSON.stringify()` function.

```javascript
let modifiedJsonString = JSON.stringify(data);
```

## Conclusion

Modifying JSON data in JavaScript is a straightforward process once we access the desired properties. There are different approaches available, ranging from direct assignment to using methods like `Object.assign()`, spread syntax, or libraries like lodash. Choose the approach that best suits your needs and enjoy modifying JSON data effortlessly in JavaScript.

#JSON #JavaScript