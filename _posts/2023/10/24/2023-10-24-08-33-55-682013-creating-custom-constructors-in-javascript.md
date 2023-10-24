---
layout: post
title: "Creating custom constructors in JavaScript"
description: " "
date: 2023-10-24
tags: [References, constructor]
comments: true
share: true
---

Constructors in JavaScript are functions that are used to create objects based on a blueprint or a class. They are used to initialize object properties and methods. By default, JavaScript provides a default constructor for every object. However, you can also create custom constructors to define your own properties and behaviors.

## Constructor Functions

A constructor function is a conventional way to create objects in JavaScript. It is defined using the `function` keyword and should start with an uppercase letter to differentiate it from regular functions. Here's an example:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Creating an object using the constructor
let john = new Person("John Doe", 25);
console.log(john.name); // Output: "John Doe"
console.log(john.age); // Output: 25
```

In the above example, we create a `Person` constructor function that takes `name` and `age` as parameters. Inside the constructor, we use the `this` keyword to set the values of `name` and `age` for the created object.

To create an object using the constructor, we use the `new` keyword followed by the constructor name and pass the required arguments. This creates a new instance of the object with the specified properties.

## Adding Methods to Constructors

Constructors can have methods just like regular objects. These methods can be added to the constructor function's prototype property. Here's an example:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Adding a method to the Person constructor
Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
};

let john = new Person("John Doe", 25);
john.greet(); // Output: "Hello, my name is John Doe and I'm 25 years old."
```

In the above example, we add a `greet` method to the `Person` constructor's prototype. This method can be accessed by all instances of the `Person` object created using the constructor.

## Inheritance with Custom Constructors

Custom constructors can also be used to implement inheritance in JavaScript. By setting the prototype of a child constructor to an instance of a parent constructor, the child objects inherit the properties and methods of the parent. Here's an example:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
};

function Employee(name, age, company) {
  Person.call(this, name, age);
  this.company = company;
}

Employee.prototype = Object.create(Person.prototype);
Employee.prototype.constructor = Employee;

let john = new Employee("John Doe", 25, "Acme Corp");
john.greet(); // Output: "Hello, my name is John Doe and I'm 25 years old."
console.log(john.company); // Output: "Acme Corp"
```

In the above example, we create an `Employee` constructor that extends the `Person` constructor. We use `Object.create` to set the `Employee` prototype as an instance of the `Person` prototype. By calling `Person.call(this, name, age)`, we ensure that the `name` and `age` properties are set for the `Employee` object.

## Conclusion

Custom constructors allow you to create objects with your own set of properties and behaviors. They provide a way to define blueprint-like structures in JavaScript and enable inheritance. Understanding constructors is crucial for developing robust and scalable JavaScript applications.

#References
- [MDN Web Docs: Constructors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects#constructor_functions)