---
layout: post
title: "Call method in JavaScript"
description: " "
date: 2023-09-26
tags: [JavaScript, MethodCall]
comments: true
share: true
---

In JavaScript, a method is a function that's associated with an object. When you want to call a method in JavaScript, you need to follow a specific syntax. In this blog post, we will walk through the steps to call a method in JavaScript.

## Step 1: Create an Object

First, you need to create an object that contains the method you want to call. For example, let's create an object named `person` with a method called `sayHello`:

```javascript
const person = {
  name: "John",
  age: 25,
  sayHello: function() {
    console.log(`Hello, my name is ${this.name} and I'm ${this.age} years old.`);
  }
};
```

In the above code, we define the `person` object with properties `name` and `age`, and a method `sayHello` which logs a greeting message with the person's name and age.

## Step 2: Call the Method

Once you have the object with the method, you can call it using the dot notation. In our example, to call the `sayHello` method on the `person` object, you would write:

```javascript
person.sayHello();
```

The above code will invoke the `sayHello` method and print the following message to the console:

```
Hello, my name is John and I'm 25 years old.
```

## Conclusion

Calling a method in JavaScript requires creating an object and using the dot notation to invoke the method. By following the steps outlined in this blog post, you can successfully call methods within your JavaScript code.

#JavaScript #MethodCall