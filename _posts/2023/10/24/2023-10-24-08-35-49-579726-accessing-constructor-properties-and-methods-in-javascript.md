---
layout: post
title: "Accessing constructor properties and methods in JavaScript"
description: " "
date: 2023-10-24
tags: []
comments: true
share: true
---

When working with JavaScript, it is common to use constructor functions to create objects. Constructor functions are used to initialize object properties and set up methods that can be accessed by instances of the object.

To access properties and methods defined in a constructor function, we need to create an instance of the object using the `new` keyword. Let's look at an example:

## Example

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;

  this.greet = function() {
    console.log(`Hello, my name is ${this.name}`);
  };
}

// Creating an instance of the Person object
var john = new Person("John", 30);

// Accessing properties
console.log(john.name); // Output: John
console.log(john.age); // Output: 30

// Accessing methods
john.greet(); // Output: Hello, my name is John
```

In the example above, we have a constructor function `Person` that takes two parameters `name` and `age`. Inside the constructor function, we set the `name` and `age` properties of the object using `this.name` and `this.age`.

We also define a `greet` method that can be accessed by instances of the `Person` object. It uses the `this.name` property to greet the person by name.

To create an instance of the `Person` object, we use the `new` keyword followed by the name of the constructor function and pass the required parameters.

We can then access the properties and methods of the instance using dot notation. In the example, we access the `name` and `age` properties using `john.name` and `john.age`, and we call the `greet` method using `john.greet()`.

By using the `new` keyword to create instances of a constructor function, we can access the properties and methods defined in the constructor. This allows us to create reusable objects with shared behavior and attributes.