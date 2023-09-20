---
layout: post
title: "Function Parameters Destructuring in JavaScript"
description: " "
date: 2023-09-20
tags: [javascript, destructuring]
comments: true
share: true
---

## Array Destructuring

When working with arrays, we can use array destructuring to easily extract values. Let's look at an example:

```javascript
function getFirstAndLastNames([firstName, lastName]) {
  console.log(`First name: ${firstName}`);
  console.log(`Last name: ${lastName}`);
}

const fullName = ['John', 'Doe'];
getFirstAndLastNames(fullName);
```

In this example, we define a function `getFirstAndLastNames` that takes an array as its parameter. Inside the function, we destructure the array parameter into two variables, `firstName` and `lastName`. We then log the extracted values to the console.

When calling the `getFirstAndLastNames` function with the `fullName` array, the values `'John'` and `'Doe'` are extracted and logged.

## Object Destructuring

Similarly, we can use object destructuring to extract values from an object. Consider the following example:

```javascript
function printPersonInfo({ name, age }) {
  console.log(`Name: ${name}`);
  console.log(`Age: ${age}`);
}

const person = {
  name: 'John Doe',
  age: 25
};

printPersonInfo(person);
```

In this case, the `printPersonInfo` function takes an object as its parameter. Inside the function, we destructure the object parameter into two variables, `name` and `age`. The values are then printed to the console.

When calling the `printPersonInfo` function with the `person` object, the values `'John Doe'` and `25` are extracted and logged.

## Default Values

Destructuring also allows us to set default values in case a value is not present. This can be particularly useful when working with optional object properties or arrays.

```javascript
function getConfig({ timeout = 5000, maxRetries = 3 }) {
  console.log(`Timeout: ${timeout}`);
  console.log(`Max retries: ${maxRetries}`);
}

const config = {
  timeout: 10000
};

getConfig(config);
```

In this example, the `getConfig` function expects an object parameter with optional properties `timeout` and `maxRetries`. If a property is not present in the object, the default value specified in the parameter definition is used.

When calling the `getConfig` function with the `config` object, the values `10000` and the default value `3` are logged. Since the `timeout` property is present in the object, it overrides the default value.

Using function parameters destructuring in JavaScript allows us to easily extract values from arrays or objects, making our code more readable and concise. It is a powerful feature that can greatly improve our development workflow.

#javascript #destructuring