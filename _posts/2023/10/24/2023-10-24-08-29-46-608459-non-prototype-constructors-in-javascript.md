---
layout: post
title: "Non-prototype constructors in JavaScript"
description: " "
date: 2023-10-24
tags: [objectorientedprogramming]
comments: true
share: true
---

JavaScript is a versatile programming language that allows developers to create objects in a variety of ways. One common method is by using constructor functions. In JavaScript, constructor functions are used to create objects with specific properties and methods. Typically, these constructor functions are defined on the prototype of the object. However, it is also possible to create objects without using the prototype.

## Using Prototype Constructors

When using prototype constructors in JavaScript, the constructor function is defined on the prototype of the object. This means that all instances of the object share the same constructor function. Here is an example:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.sayHello = function() {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
}

var john = new Person("John Doe", 25);
john.sayHello(); // Output: Hello, my name is John Doe and I am 25 years old.
```

In this example, `Person` is the constructor function and `sayHello` is a method defined on the prototype. The `new` keyword is used to create a new instance of `Person` and bind the constructor function to the instance.

## Non-Prototype Constructors

Alternatively, it is also possible to create objects without using the prototype. In this approach, each instance has its own copy of the defined properties and methods. Here is an example:

```javascript
function Car(make, model) {
  var self = {};

  self.make = make;
  self.model = model;

  self.start = function() {
    console.log(`Starting the ${this.make} ${this.model}.`);
  }

  return self;
}

var myCar = new Car("Tesla", "Model 3");
myCar.start(); // Output: Starting the Tesla Model 3.
```

In this example, `Car` is the constructor function, and instead of defining properties and methods on the prototype, they are defined directly on the `self` object, which is then returned from the constructor function. Each instance of `Car` will have its own separate `self` object, resulting in separate copies of the properties and methods.

## Choosing between Prototype and Non-Prototype Constructors

The choice between prototype constructors and non-prototype constructors depends on the specific requirements of your project. Here are some factors to consider:

- **Performance**: Prototype constructors can be more memory-efficient as shared methods are stored in the prototype and not replicated for each instance.

- **Flexibility**: Non-prototype constructors allow for more flexibility as each instance has its own copy of the properties and methods.

- **Inheritance**: Prototype constructors lend themselves better to prototypal inheritance as methods can be added or modified on the prototype, affecting all instances.

- **Encapsulation**: Non-prototype constructors provide a way to achieve encapsulation by keeping properties and methods private within the constructor function.

In conclusion, both prototype constructors and non-prototype constructors have their own advantages and use cases. Understanding the differences and choosing the right approach will depend on the specific needs of your project.

**#javascript #objectorientedprogramming**