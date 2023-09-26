---
layout: post
title: "Prototypal inheritance vs classical inheritance and context in JavaScript"
description: " "
date: 2023-09-26
tags: [JavaScript, Inheritance]
comments: true
share: true
---

JavaScript is a versatile programming language that allows you to implement inheritance using different approaches. Two popular approaches are prototypal inheritance and classical inheritance.

## Prototypal Inheritance
Prototypal inheritance is a type of inheritance model in JavaScript where objects directly inherit properties and methods from other objects. Every object in JavaScript has an associated prototype object. When a property or method is accessed on an object, JavaScript first checks the object itself for that property or method. If it can't find it, it looks up the prototype chain until it either finds the property or reaches the end of the chain.

To create an object with prototypal inheritance in JavaScript, you can use the `Object.create()` method, passing the desired prototype object as an argument. Here's an example:

```javascript
const animal = {
  eat: function() {
    console.log('Eating...');
  }
};

const dog = Object.create(animal);
dog.bark = function() {
  console.log('Barking...');
};

dog.eat(); // Output: Eating...
dog.bark(); // Output: Barking...
```

In the above example, the `dog` object is created with `animal` as its prototype. This allows the `dog` object to inherit the `eat()` method from the `animal` object.

## Classical Inheritance
Classical inheritance is a more traditional approach to inheritance, commonly found in languages like Java or C++. In JavaScript, classical inheritance can be achieved using constructor functions and the `new` keyword.

Here's an example of classical inheritance in JavaScript:

```javascript
function Animal() {
  this.eat = function() {
    console.log('Eating...');
  };
}

function Dog() {
  Animal.call(this); // "Call" the Animal constructor to inherit its properties and methods
  this.bark = function() {
    console.log('Barking...');
  };
}

const dog = new Dog();
dog.eat(); // Output: Eating...
dog.bark(); // Output: Barking...
```

In the above example, the `Dog` constructor function is used to create a new object with the properties and methods of the `Animal` constructor function. The `call()` method is used to invoke the `Animal` constructor within the `Dog` constructor, allowing the `Dog` object to inherit the `eat()` method.

## Context in JavaScript
Context refers to the value of the `this` keyword within a function. In JavaScript, the context of a function can be influenced by how the function is called.

For example:

```javascript
const obj = {
  name: 'John',
  sayHello: function() {
    console.log('Hello, ' + this.name);
  }
};

const greet = obj.sayHello;
greet(); // Output: Hello, undefined
```

In the above code, when the `sayHello` function is assigned to the `greet` variable, the context of the function changes. The `this` keyword inside `greet` no longer refers to the `obj` object, resulting in undefined output.

To bind a specific context to a function, JavaScript provides the `bind()` method, which returns a new function with the context permanently set:

```javascript
const obj = {
  name: 'John',
  sayHello: function() {
    console.log('Hello, ' + this.name);
  }
};

const greet = obj.sayHello.bind(obj);
greet(); // Output: Hello, John
```

In the above example, the `bind()` method is used to bind the `obj` context to the `sayHello` function, ensuring that `this` always refers to the `obj` object.

## Conclusion
Both prototypal inheritance and classical inheritance have their use cases and trade-offs in JavaScript. Understanding these concepts and how context works in JavaScript can help you write clean and efficient code when implementing inheritance in your projects.

#JavaScript #Inheritance