---
layout: post
title: "Private and public properties in constructor functions in JavaScript"
description: " "
date: 2023-10-24
tags: []
comments: true
share: true
---

When working with constructor functions in JavaScript, we often encounter the need to define private and public properties. Private properties are those that are only accessible within the constructor function itself, while public properties can be accessed and modified from outside the constructor function. 

In this article, we will explore how to define both private and public properties within constructor functions in JavaScript, using the concept of closures.

## Defining Private Properties

To define a private property in a constructor function, we can make use of a closure. A closure is a function that remembers the variables in its outer scope, even if that function is invoked outside its lexical scope.

Here's an example:

```javascript
function Person(name) {
  const privateAge = 30;

  this.getName = function() {
    return name;
  };

  this.getAge = function() {
    return privateAge;
  };
}

const person = new Person('John');
console.log(person.getName()); // Output: John
console.log(person.privateAge); // Output: undefined
console.log(person.getAge()); // Output: 30
```

In the above example, we define a private property `privateAge` within the `Person` constructor function. This property is only accessible within the scope of the constructor function. We can access the private property using the `getAge` method defined within the constructor function. However, trying to directly access `privateAge` will result in `undefined`.

## Defining Public Properties

To define public properties in a constructor function, we can simply assign them directly to the `this` keyword. These properties will be accessible outside the constructor function.

Here's an example:

```javascript
function Person(name) {
  this.name = name;
  this.age = 30;
}

const person = new Person('John');
console.log(person.name); // Output: John
console.log(person.age); // Output: 30
```

In the above example, we define two public properties `name` and `age` within the `Person` constructor function. These properties can be accessed and modified directly from outside the constructor function.

## Conclusion

In JavaScript, we can define private properties within constructor functions using closures, while public properties can be defined by assigning them directly to the `this` keyword. Understanding the distinction between private and public properties allows us to encapsulate data and control its accessibility within our code.

By using private and public properties effectively, we can achieve better encapsulation and maintainability in our JavaScript applications.

**References:**
- [MDN Web Docs - Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)