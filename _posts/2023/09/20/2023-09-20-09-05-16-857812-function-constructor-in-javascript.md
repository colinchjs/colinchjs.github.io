---
layout: post
title: "Function Constructor in JavaScript"
description: " "
date: 2023-09-20
tags: []
comments: true
share: true
---

JavaScript is a versatile programming language that allows for the creation of various objects and functions. One of the ways to define functions in JavaScript is by using a function constructor.

A function constructor is a function that is used to create objects with a predefined structure and behavior. It is similar to a blueprint or a template for creating objects. By using a function constructor, you can create multiple objects with the same properties and methods.

To define a function constructor in JavaScript, you can use the `function` keyword followed by the constructor name. Inside the constructor function, you can define the properties and methods for the objects created using the constructor.

## Syntax

The syntax for a function constructor in JavaScript is as follows:

```javascript
function ConstructorName(prop1, prop2) {
    this.property1 = prop1;
    this.property2 = prop2;

    this.method1 = function() {
        // method code here
    };

    this.method2 = function() {
        // method code here
    };
}
```

In the above example, `ConstructorName` is the name of the constructor function. The `prop1` and `prop2` are the parameters that are used to initialize the properties of the created object. Inside the constructor function, `this` refers to the object being created.

You can define properties and methods using the `this` keyword followed by the property or method name. The properties are initialized using the provided parameters, while the methods are defined as functions within the constructor.

## Creating Objects with Function Constructor

To create objects using a function constructor, you can use the `new` keyword followed by the constructor name and the required parameters. This will create a new object based on the constructor's blueprint.

```javascript
const newObj = new ConstructorName(prop1Value, prop2Value);
```

In the above example, `newObj` is the newly created object based on the `ConstructorName` function constructor. The `prop1Value` and `prop2Value` are the values passed as arguments to initialize the properties of the object.

## Example

Let's consider an example where we create a function constructor for a Person object with name and age properties:

```javascript
function Person(name, age) {
    this.name = name;
    this.age = age;

    this.greet = function() {
        console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
    };
}

const john = new Person('John', 30);
john.greet();
```

In this example, we define a function constructor `Person` with two properties: `name` and `age`. We also define a `greet` method that logs a greeting message to the console. We then create a new `Person` object, `john`, with the name "John" and age 30. Finally, we call the `greet` method on the `john` object, which logs the greeting message.

Function constructors in JavaScript provide a way to create objects with a consistent structure and behavior. They are useful when you need to create multiple objects with similar properties and methods.