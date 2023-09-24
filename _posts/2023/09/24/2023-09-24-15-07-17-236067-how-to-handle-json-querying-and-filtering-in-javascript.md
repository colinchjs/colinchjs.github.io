---
layout: post
title: "How to handle JSON querying and filtering in JavaScript."
description: " "
date: 2023-09-24
tags: [javascript, JSON]
comments: true
share: true
---

In JavaScript, working with JSON data is a common task. JSON (JavaScript Object Notation) is a lightweight data interchange format that is easy for humans to read and write, and easy for machines to parse and generate. In this blog post, we will explore how to query and filter JSON data using JavaScript.

## Querying JSON Data

To query JSON data in JavaScript, you can use the `filter()` method. This method creates a new array with all elements that pass the specified test function.

Consider the following JSON data:

```javascript
const users = [
  {
    id: 1,
    name: "John",
    age: 25,
    profession: "Developer"
  },
  {
    id: 2,
    name: "Jane",
    age: 30,
    profession: "Designer"
  },
  {
    id: 3,
    name: "Mike",
    age: 35,
    profession: "Manager"
  }
];
```

To query this JSON data and get all users whose age is greater than 28, you can use the `filter()` method as follows:

```javascript
const filteredUsers = users.filter(user => user.age > 28);
console.log(filteredUsers);
```

The above code will output an array containing users with an age greater than 28:

```javascript
[
  {
    id: 2,
    name: "Jane",
    age: 30,
    profession: "Designer"
  },
  {
    id: 3,
    name: "Mike",
    age: 35,
    profession: "Manager"
  }
]
```

## Filtering JSON Data

In addition to querying JSON data based on a specific condition, you can also filter JSON data based on multiple conditions. One way to achieve this is by chaining multiple `filter()` methods.

Consider the following JSON data:

```javascript
const products = [
  {
    id: 1,
    name: "iPhone 12",
    price: 999,
    category: "Electronics",
    brand: "Apple"
  },
  {
    id: 2,
    name: "Samsung Galaxy S21",
    price: 899,
    category: "Electronics",
    brand: "Samsung"
  },
  {
    id: 3,
    name: "Nike Air Max",
    price: 129,
    category: "Shoes",
    brand: "Nike"
  }
];
```

To filter this JSON data and get all electronics products with a price less than or equal to 1000, you can chain multiple `filter()` methods as follows:

```javascript
const filteredProducts = products
  .filter(product => product.category === "Electronics")
  .filter(product => product.price <= 1000);

console.log(filteredProducts);
```

The code above will output an array containing the products that match both conditions:

```javascript
[
  {
    id: 1,
    name: "iPhone 12",
    price: 999,
    category: "Electronics",
    brand: "Apple"
  }
]
```

Now you have learned how to query and filter JSON data using JavaScript! This knowledge will be useful when working with JSON APIs or handling JSON data in your JavaScript applications.

#javascript #JSON