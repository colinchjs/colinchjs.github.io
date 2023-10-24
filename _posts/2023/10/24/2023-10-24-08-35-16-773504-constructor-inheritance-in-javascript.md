---
layout: post
title: "Constructor inheritance in JavaScript"
description: " "
date: 2023-10-24
tags: []
comments: true
share: true
---

In JavaScript, constructor inheritance allows us to create a relationship between two classes where one class inherits the properties and methods from another class. This is often referred to as class inheritance or prototypal inheritance.

## Table of Contents
- [Introduction](#introduction)
- [Constructor Functions](#constructor-functions)
- [Inheriting Properties and Methods](#inheriting-properties-and-methods)
- [Calling Superclass Constructor](#calling-superclass-constructor)
- [Overriding Superclass Methods](#overriding-superclass-methods)
- [Conclusion](#conclusion)

## Introduction

In JavaScript, we can create classes using constructor functions. The constructor function serves as a blueprint for creating objects of that class. We can define properties and methods within the constructor function, which are then shared among all instances (objects) created from that constructor function.

Constructor inheritance allows us to extend the functionality of a class by creating a new class that inherits properties and methods from a superclass. The new class, also known as a subclass, can add additional properties and methods or override existing ones as needed.

## Constructor Functions

In JavaScript, constructor functions are defined using the `function` keyword and are named with an initial capital letter, by convention. Here's an example of a simple constructor function:

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function() {
  console.log(`The ${this.name} says hello!`);
};

const dog = new Animal('Dog');
dog.speak(); // Output: The Dog says hello!
```

## Inheriting Properties and Methods

To inherit the properties and methods of a superclass, we can use the `Object.create()` method along with the `prototype` property. The `Object.create()` method creates a new object with the prototype set to a specified object.

```javascript
function Cat(name, color) {
  Animal.call(this, name); // Call the superclass constructor
  this.color = color;
}

Cat.prototype = Object.create(Animal.prototype);

const cat = new Cat('Cat', 'Brown');
cat.speak(); // Output: The Cat says hello!
console.log(cat.color); // Output: Brown
```

In the code above, we created a new `Cat` class that extends the `Animal` class. We used the `Animal.call(this, name)` statement to call the `Animal` constructor and set the `name` property of the `Cat` class. We then used `Object.create(Animal.prototype)` to inherit the `speak()` method from the `Animal` class.

## Calling Superclass Constructor

When inheriting from a superclass, it's necessary to call the superclass constructor within the subclass. This ensures that the superclass initializes its own properties and performs any necessary setup.

```javascript
function Shape(color) {
  this.color = color;
}

Shape.prototype.getArea = function() {
  // Some logic here
};

function Circle(radius, color) {
  Shape.call(this, color); // Call the superclass constructor
  this.radius = radius;
}

Circle.prototype = Object.create(Shape.prototype);

const circle = new Circle(5, 'Red');
console.log(circle.color); // Output: Red
console.log(circle.radius); // Output: 5
```

In the above example, the `Circle` class inherits from the `Shape` class. We call `Shape.call(this, color)` within the `Circle` constructor to initialize the `color` property of the `Shape` class before setting the `radius` property of the `Circle` class.

## Overriding Superclass Methods

In some cases, we may want to override a method defined in the superclass with a different implementation in the subclass. To achieve this, we can simply define the method in the subclass, and when the method is called, the implementation in the subclass will be used instead of the one in the superclass.

```javascript
function Vehicle() {}

Vehicle.prototype.drive = function() {
  console.log('Driving!');
};

function Car() {}

Car.prototype = Object.create(Vehicle.prototype);

Car.prototype.drive = function() {
  console.log('Driving a car!');
};

const vehicle = new Vehicle();
const car = new Car();

vehicle.drive(); // Output: Driving!
car.drive(); // Output: Driving a car!
```

In the example above, the `Car` class overrides the `drive()` method inherited from the `Vehicle` class. When `car.drive()` is called, the subclass implementation is used, resulting in the output, "Driving a car!".

## Conclusion

Constructor inheritance in JavaScript allows us to create a hierarchy of classes, where each subclass inherits properties and methods from its superclass. By leveraging constructor inheritance, we can create more modular and reusable code by extending existing classes and adding additional functionality as needed.

By using constructor inheritance, we can easily create relationships between classes and build complex applications with clean and organized code.

Inheritance, whether in JavaScript or any other programming language, is a powerful concept that enables code reuse and promotes a logical and structured approach to building software systems.

---

**Note**: It is recommended to understand the basic concepts of JavaScript, including constructor functions and the prototype chain, before diving into constructor inheritance. References like the [MDN web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) can provide more in-depth information.