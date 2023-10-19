---
layout: post
title: "What are CRUD operations in JavaScript?"
description: " "
date: 2023-10-20
tags: []
comments: true
share: true
---

CRUD stands for Create, Read, Update, and Delete. These operations are essential in any application that interacts with a database or needs to manage data. In JavaScript, you can perform CRUD operations using various techniques and libraries.

## Create (C)

Creating data in JavaScript involves adding new records to a database or an array. Here's an example of how you can create a new object and add it to an array using pure JavaScript:

```javascript
const records = [];

function createRecord(name, email) {
  const record = { name, email };
  records.push(record);
}

createRecord("John Doe", "john@gmail.com");
```

In addition to the above approach, many JavaScript frameworks and libraries offer higher-level abstractions and tools that simplify the process of creating data.

## Read (R)

Reading data in JavaScript involves retrieving existing records from a database or an array. Here's an example of how you can read records from an array using pure JavaScript:

```javascript
function getRecords() {
  return records;
}

console.log(getRecords()); // Output: [{ name: "John Doe", email: "john@gmail.com" }]
```

Similarly to the create operation, JavaScript frameworks and libraries offer convenient methods to retrieve data from databases or APIs.

## Update (U)

Updating data in JavaScript involves modifying existing records. Here's an example of how you can update a record in an array using pure JavaScript:

```javascript
function updateRecord(email, newName) {
  const record = records.find((r) => r.email === email);
  if (record) {
    record.name = newName;
  }
}

updateRecord("john@gmail.com", "Jane Smith");
console.log(getRecords()); // Output: [{ name: "Jane Smith", email: "john@gmail.com" }]
```

JavaScript frameworks and libraries often provide ways to perform updates more efficiently, such as by using query builders or ORM (Object-Relational Mapping) libraries.

## Delete (D)

Deleting data in JavaScript involves removing existing records from a database or an array. Here's an example of how you can delete a record from an array using pure JavaScript:

```javascript
function deleteRecord(email) {
  const index = records.findIndex((r) => r.email === email);
  if (index !== -1) {
    records.splice(index, 1);
  }
}

deleteRecord("john@gmail.com");
console.log(getRecords()); // Output: []
```

As with the other CRUD operations, JavaScript frameworks and libraries often provide more sophisticated methods to handle deletion, including cascading deletes and soft deletes.

CRUD operations are an integral part of developing applications that manage data. By understanding and implementing these operations, you can efficiently manipulate and interact with data in your JavaScript projects.

_References:_
- [MDN Web Docs - CRUD](https://developer.mozilla.org/en-US/docs/Glossary/CRUD)