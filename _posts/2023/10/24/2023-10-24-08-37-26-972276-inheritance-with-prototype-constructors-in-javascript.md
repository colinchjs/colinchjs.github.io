---
layout: post
title: "Inheritance with prototype constructors in JavaScript"
description: " "
date: 2023-10-24
tags: [inheritance]
comments: true
share: true
---

In JavaScript, inheritance is a powerful feature that allows us to create new objects based on existing objects. One way to achieve inheritance is by using prototype constructors. Prototype constructors function as blueprints for creating objects with shared properties and methods.

## Understanding Prototype Constructors

Prototype constructors are functions that serve as constructors for creating objects. They define the shared properties and methods that will be inherited by the objects created from them. 

Let's consider an example of a `Person` prototype constructor that defines properties and methods for creating person objects:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name} and I am ${this.age} years old.`);
}
```

In the above code, the `Person` prototype constructor takes two parameters, `name` and `age`, and assigns them as properties to any person object created from it. The `greet` method is added to the prototype of the `Person` constructor, which means it will be shared by all objects created from it.

## Inheriting from a Prototype Constructor

To create a new constructor that inherits from a prototype constructor, we can use the `Object.create()` method. This method takes an existing object and creates a new object that inherits from it.

Let's say we want to create a `Student` constructor that inherits from the `Person` prototype constructor:

```javascript
function Student(name, age, grade) {
  Person.call(this, name, age);
  this.grade = grade;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;

Student.prototype.displayGrade = function() {
  console.log(`I am a student in grade ${this.grade}.`);
}
```

In the above code, we first call the `Person` constructor using `call()` within the `Student` constructor to set the name and age properties for the student object.

Next, we use `Object.create()` to create a new object that inherits from the `Person.prototype` object. This ensures that the new `Student` object will have all the properties and methods defined in `Person` prototype.

Finally, we set the `constructor` property of the `Student.prototype` object back to `Student`, as it gets overwritten when we assign it the value of `Person.prototype`.

## Using Inherited Properties and Methods

Now that we have created the `Student` constructor, we can create student objects and use both the inherited properties and methods from `Person`, as well as the specific properties and methods of `Student`.

```javascript
const john = new Student("John", 18, 12);

john.greet(); // Outputs: Hello, my name is John and I am 18 years old.
john.displayGrade(); // Outputs: I am a student in grade 12.
```

In the above code, we create a new `Student` object named `john` with specific properties for name, age, and grade. Then, we call the `greet()` method inherited from the `Person` prototype, as well as the `displayGrade()` method defined in the `Student` prototype.

## Conclusion

Inheritance through prototype constructors allows us to create objects that inherit shared properties and methods from existing objects. By using the `Object.create()` method, we can easily create new constructors that inherit from prototype constructors. This approach promotes code reuse and simplifies the process of creating related objects in JavaScript.

References:
- [MDN Web Docs: Inheritance and the prototype chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain) #javascript #inheritance