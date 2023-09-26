---
layout: post
title: "Pass by reference and context in JavaScript"
description: " "
date: 2023-09-26
tags: [JavaScript, Programming]
comments: true
share: true
---

When working with JavaScript, it's important to understand how values are passed and how the execution context is managed. Two concepts that are commonly encountered are "pass by reference" and "context."

## Pass by Reference
In JavaScript, all objects (arrays, functions, and non-primitive types) are passed by reference. This means that when you pass an object as a parameter to a function, you are actually passing a reference to the object.

```javascript
let obj1 = {
    name: "John"
};

function changeName(obj) {
    obj.name = "Jane";
}

changeName(obj1);
console.log(obj1.name); // Output: "Jane"
```

In the above example, we have an object `obj1` with a property `name`. When `obj1` is passed to the `changeName` function, the function receives a reference to `obj1`. Consequently, any changes made to the object within the function will also affect the original object.

## Context
The execution context refers to the environment in which code is executed. In JavaScript, every function has its own execution context, which includes the value of the `this` keyword.

The value of `this` within a function depends on how the function is invoked. There are four ways to call a function in JavaScript, each of which has a different context:

1. **Global scope**: When a function is invoked in the global scope, `this` refers to the global object (usually `window` in browsers).

2. **Function context**: When a function is called as a method of an object, `this` refers to the object itself.

3. **Constructor context**: When a function is used as a constructor with the `new` keyword, `this` refers to the new instance being created.

4. **Explicit context**: When using methods like `call` or `apply`, `this` is explicitly set to a specific value.

```javascript
function Person(name) {
    this.name = name;
    this.sayHello = function() {
        console.log("Hello, " + this.name);
    };
}

let person1 = new Person("John");
person1.sayHello(); // Output: "Hello, John"

let person2 = {
    name: "Jane"
};

person1.sayHello.call(person2); // Output: "Hello, Jane"
```

In the above example, we define a constructor function `Person`. When a new instance of `Person` is created using the `new` keyword, the value of `this` is set to the newly created object. However, when we use `call` to explicitly invoke the `sayHello` function with `person2` as the context, `this` is set to `person2`.

## Conclusion
Understanding pass by reference and context in JavaScript is essential for writing efficient and robust code. By grasping these concepts, you'll be better equipped to work with objects, modify their properties, and manage the execution context of your functions. #JavaScript #Programming