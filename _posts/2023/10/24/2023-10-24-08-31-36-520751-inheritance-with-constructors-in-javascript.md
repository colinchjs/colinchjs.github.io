---
layout: post
title: "Inheritance with constructors in JavaScript"
description: " "
date: 2023-10-24
tags: [inheritance]
comments: true
share: true
---

Inheritance is a fundamental concept in object-oriented programming that allows us to create a hierarchy of classes, where child classes inherit properties and methods from parent classes. JavaScript, being a prototype-based language, does not have built-in support for classes like traditional object-oriented languages. However, we can still achieve inheritance using constructor functions and prototypes.

### Constructor Functions

In JavaScript, constructor functions are special functions used to create and initialize objects. They are called using the `new` keyword, which creates a new instance of the object and assigns it to `this`. Constructor functions can also accept parameters for configuring the initial state of the object.

```javascript
function Shape(color) {
  this.color = color;
}

Shape.prototype.getColor = function() {
  return this.color;
};
```

In the above example, we have a `Shape` constructor function that takes a `color` parameter and sets it as an instance variable. The `getColor` method is added to the prototype of the `Shape` function, which allows all instances of `Shape` to access this method.

### Inheriting Constructors

To implement inheritance in JavaScript, we can use the `call` method of a constructor function to invoke the parent constructor within the child constructor. This allows the child constructor to inherit properties and initialize them using the parent's logic.

```javascript
function Circle(radius, color) {
  Shape.call(this, color);
  this.radius = radius;
}

Circle.prototype = Object.create(Shape.prototype);
Circle.prototype.constructor = Circle;

Circle.prototype.getRadius = function() {
  return this.radius;
};
```

In the above example, we have a `Circle` constructor function that inherits from the `Shape` constructor. Inside the `Circle` constructor, we use `Shape.call(this, color)` to invoke the `Shape` constructor with the appropriate `color` parameter. This sets the `color` property on the `Circle` instance. 

Then, we set the `Circle.prototype` to a new object created with `Object.create(Shape.prototype)`. This establishes the prototype chain and allows the `Circle` instances to access methods defined in `Shape.prototype`.

Finally, we define a `getRadius` method specific to `Circle` on its prototype.

### Testing the Inheritance

```javascript
const myShape = new Shape('red');
console.log(myShape.getColor()); // Output: red

const myCircle = new Circle(5, 'blue');
console.log(myCircle.getColor()); // Output: blue
console.log(myCircle.getRadius()); // Output: 5
```

In the test code, we create instances of both `Shape` and `Circle`. The `myShape` instance calls the inherited `getColor` method and displays the `color` property, while the `myCircle` instance calls both the inherited `getColor` method and its own `getRadius` method.

### Conclusion

In JavaScript, inheritance can be achieved using constructor functions and prototypes. By calling the parent constructor using `call` and establishing the prototype chain, child constructors can inherit properties and methods from parent constructors. This allows us to create complex object hierarchies and create reusable code. Hashtag: #javascript #inheritance