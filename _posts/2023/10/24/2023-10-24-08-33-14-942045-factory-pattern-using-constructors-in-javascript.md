---
layout: post
title: "Factory pattern using constructors in JavaScript"
description: " "
date: 2023-10-24
tags: [references]
comments: true
share: true
---

In JavaScript, the Factory Pattern is a creational design pattern that provides a way to create objects without specifying their exact class. It delegates the responsibility of object instantiation to a factory function or constructor. In this blog post, we will explore how to implement the Factory Pattern using constructors in JavaScript.

## Table of Contents
- [Introduction](#introduction)
- [The Factory Pattern](#the-factory-pattern)
- [Implementation](#implementation)
  - [Factory Function](#factory-function)
  - [Constructor Function](#constructor-function)
- [Usage Example](#usage-example)
- [Advantages of Factory Pattern](#advantages-of-factory-pattern)
- [Conclusion](#conclusion)

## Introduction
The Factory Pattern is useful when we want to create multiple objects with similar properties and behaviors. Instead of manually instantiating each object, we can use a factory function or constructor to handle the instantiation process in a centralized manner.

## The Factory Pattern
The Factory Pattern involves the creation of an interface (often an abstract class) that declares the method for creating objects. Concrete classes or functions, implementing the interface, are responsible for creating objects based on the specific requirements.

## Implementation
We can implement the Factory Pattern in JavaScript using either a factory function or a constructor function. Let's look at both approaches.

### Factory Function
A factory function is a regular JavaScript function that returns a new object. It encapsulates the object creation process and can be customized based on certain parameters.

```javascript
function createCar(make, model, year) {
  return {
    make,
    model,
    year,
    start() {
      console.log(`Starting ${make} ${model} (${year})...`);
    }
  };
}
```

### Constructor Function
A constructor function, when used with the `new` keyword, creates a new object and sets its initial properties by default. We can define common behaviors using prototype methods.

```javascript
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

Car.prototype.start = function() {
  console.log(`Starting ${this.make} ${this.model} (${this.year})...`);
};
```

## Usage Example
To create objects using the factory pattern, we simply need to invoke the factory function or constructor function with the desired parameters.

```javascript
const car1 = createCar('Toyota', 'Camry', 2021);
car1.start();  // Output: Starting Toyota Camry (2021)...

const car2 = new Car('Honda', 'Civic', 2022);
car2.start();  // Output: Starting Honda Civic (2022)...
```

## Advantages of Factory Pattern
- Provides a centralized place for object creation, making code maintenance easier.
- Encapsulates the object creation process, making it more flexible to change the creation logic without affecting the client code.
- Enables the creation of objects with different configurations based on parameters.

## Conclusion
The Factory Pattern allows for more flexible and maintainable object creation by delegating the responsibility to a factory function or constructor. In JavaScript, we can implement the Factory Pattern using either a factory function or a constructor function, providing us with the ability to create objects with common properties and behaviors. By utilizing this pattern, we can write more modular and reusable code.

#references #javascript