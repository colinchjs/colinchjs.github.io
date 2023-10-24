---
layout: post
title: "Constructor patterns for modular code in JavaScript"
description: " "
date: 2023-10-24
tags: [References]
comments: true
share: true
---

When working with JavaScript, it's important to write modular and reusable code to improve maintainability and modularity. One of the common approaches to achieve this is by using constructor patterns. Constructor patterns allow you to create objects with shared properties and methods, providing a way to organize and encapsulate related functionality.

In this blog post, we will explore the two popular constructor patterns in JavaScript: the Prototype Pattern and the Class Pattern.

## Prototype Pattern

The Prototype Pattern in JavaScript is a way to create objects by defining a prototype object which serves as a blueprint for other objects. We can then create new instances of objects based on this prototype.

```javascript
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

Car.prototype.start = function() {
  console.log('Engine started!');
};

var myCar = new Car('Tesla', 'Model S', 2022);
myCar.start(); // Output: Engine started!
```

In the above example, we define a constructor function `Car` with `make`, `model`, and `year` properties. The `start` method is added to the `Car.prototype` object, which ensures that all instances of `Car` share the same `start` method.

## Class Pattern

Since ES6, JavaScript introduced the class syntax, which allows us to write object-oriented code in a more familiar way. The Class Pattern provides a cleaner syntax for creating objects with shared properties and methods.

```javascript
class Car {
  constructor(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
  }

  start() {
    console.log('Engine started!');
  }
}

let myCar = new Car('Tesla', 'Model S', 2022);
myCar.start(); // Output: Engine started!
```

The above code demonstrates the use of the Class Pattern in JavaScript. We define a class `Car` with a constructor and the `start` method. When creating a new instance of `Car`, we use the `new` keyword to instantiate the object.

## Conclusion

Both the Prototype Pattern and the Class Pattern provide ways to create modular and reusable code in JavaScript. The Prototype Pattern is the traditional way, while the Class Pattern introduced a more concise syntax in ES6.

Using constructor patterns helps organize your code, separate concerns, and promote code reusability. Depending on your preference and the JavaScript version you target, you can choose either the Prototype Pattern or the Class Pattern to create modular code.

#References

- [MDN web docs: Object-oriented JavaScript for beginners](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object-oriented_JS)
- [The Constructor Pattern in JavaScript](https://blog.bitsrc.io/understanding-constructor-pattern-in-javascript-1342ece8ead4)
- [The Class pattern in JavaScript](https://medium.com/jspoint/javascript-classes-understand-the-class-pattern-5e320ec11e24)