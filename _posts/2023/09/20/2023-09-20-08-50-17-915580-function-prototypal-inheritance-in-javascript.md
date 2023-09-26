---
layout: post
title: "Function Prototypal Inheritance in JavaScript"
description: " "
date: 2023-09-20
tags: [PrototypalInheritance]
comments: true
share: true
---

Do you want to learn about prototypal inheritance in JavaScript? In this blog post, we will explore how to achieve inheritance using function prototypes.

## Understanding Prototypal Inheritance

Prototypal inheritance is a way to create a relationship between objects in JavaScript. It allows an object to inherit properties and methods from another object, known as the parent or prototype.

## The Prototype Chain

In JavaScript, each object has an internal property called `[[Prototype]]`, which refers to its parent prototype. When a property or method is accessed on an object, JavaScript first checks if the object itself contains the property. If not, it looks into its prototype object. This process happens recursively until it finds the property or reaches the end of the prototype chain.

## Creating Inherited Objects

To create an object that inherits from another object, we can use function prototypes. Let's see an example:

```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.sound = function() {
  console.log("Animal sound");
};

function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
Dog.prototype.bark = function() {
  console.log("Woof woof!");
};
```

In this example, we have an `Animal` constructor function with a `sound` method. We then define a `Dog` constructor function that calls the `Animal` function using `call` to set up the properties inherited from `Animal`. Next, we use `Object.create` to create a new object with the prototype of `Animal` and assign it to `Dog.prototype`. Finally, we set the `constructor` property of `Dog` back to `Dog` to ensure the correct constructor.

## Inheritance in Action

Now, let's create instances of `Dog` and see how they inherit properties and methods from `Animal`:

```javascript
const myDog = new Dog("Max", "Labrador");
myDog.sound(); // Output: "Animal sound"
myDog.bark(); // Output: "Woof woof!"
console.log(myDog.name); // Output: "Max"
```

As you can see, the `myDog` instance has access to the `sound` method defined in `Animal`, as well as the `bark` method defined in `Dog`. It also inherits the `name` property from `Animal`.

## Conclusion

Prototypal inheritance is a fundamental concept in JavaScript. By understanding how to use function prototypes, you can leverage this powerful feature to create object hierarchies and reuse code effectively. **#JavaScript #PrototypalInheritance**

I hope this blog post has shed some light on function prototypal inheritance in JavaScript. Happy coding!