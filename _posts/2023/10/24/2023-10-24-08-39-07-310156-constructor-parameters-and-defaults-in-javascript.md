---
layout: post
title: "Constructor parameters and defaults in JavaScript"
description: " "
date: 2023-10-24
tags: []
comments: true
share: true
---

When working with object-oriented programming in JavaScript, constructor functions play a crucial role in creating new instances of objects. In JavaScript, we can define constructor functions using the `function` keyword and the name of the function starting with an uppercase letter.

Constructor functions can have parameters that allow us to pass values during object instantiation. These parameters are defined within the parentheses after the constructor function's name. 

Let's take a look at an example:

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const john = new Person("John", 30);
console.log(john.name); // Output: John
console.log(john.age); // Output: 30
```

In the above example, `Person` is a constructor function that takes two parameters: `name` and `age`. When we create a new instance of the `Person` object using the `new` keyword and provide values for the parameters, those values get assigned to the respective properties of the object.

## Default Parameter Values

In JavaScript, we can specify default values for constructor parameters, which will be used if no value is provided during object instantiation. Default parameter values come in handy when we want to set some initial values for properties without explicitly providing them while creating objects.

Here's an example:

```javascript
function Person(name = "Unknown", age = 0) {
  this.name = name;
  this.age = age;
}

const john = new Person("John", 30);
console.log(john.name); // Output: John
console.log(john.age); // Output: 30

const mary = new Person();
console.log(mary.name); // Output: Unknown
console.log(mary.age); // Output: 0
```

In the above example, the `Person` constructor function sets default values for `name` and `age` parameters. If no values are provided during object instantiation, the default values ("Unknown" and 0) will be used instead.

Constructor parameters and default values enhance the flexibility and usability of constructor functions in JavaScript. They allow us to create objects with varying initial property values and provide fallback values when necessary.

By using constructor parameters and defaults effectively, we can create more robust and customizable JavaScript objects within our applications.

> References:
> 
> - [MDN Web Docs: Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions)
> - [MDN Web Docs: Constructors](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/constructor)