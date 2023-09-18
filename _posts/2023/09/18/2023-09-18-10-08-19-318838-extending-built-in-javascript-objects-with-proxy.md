---
layout: post
title: "Extending built-in JavaScript objects with Proxy"
description: " "
date: 2023-09-18
tags: []
comments: true
share: true
---

JavaScript is a versatile language that allows developers to extend its built-in objects to add custom behaviors. One way to achieve this is by using the `Proxy` object.

## What is a Proxy?

A `Proxy` is an object that wraps another object and intercepts its operations. It allows you to define custom behavior for various operations such as property access, assignment, and function invocation. By leveraging the power of proxies, you can modify the behavior of built-in JavaScript objects according to your needs.

## Example: Extending Array with a Proxy

Let's say you want to extend the built-in `Array` object with a custom behavior that logs a message whenever a new element is added to the array. Here's an example of how you can achieve this using a `Proxy`:

```javascript
const proxiedArrayHandler = {
  set: function(target, property, value, receiver) {
    console.log(`Added element '${value}' to the array`);
    return Reflect.set(target, property, value, receiver);
  }
};

const proxiedArray = new Proxy([], proxiedArrayHandler);

proxiedArray.push("Element 1"); // Output: Added element 'Element 1' to the array
proxiedArray.push("Element 2"); // Output: Added element 'Element 2' to the array
```

In the above code, we define a `proxiedArrayHandler` object that contains a `set` trap. This trap intercepts any assignment to the array and logs a message before delegating the operation to the actual array using `Reflect.set()`. We then create a new `Proxy` object, `proxiedArray`, that wraps an empty array and uses our custom `proxiedArrayHandler` for its operations. When we call `push()` on `proxiedArray`, our custom behavior kicks in and logs a message before adding the element to the array.

## Conclusion

Using the `Proxy` object in JavaScript allows you to extend the behavior of built-in objects and add custom functionality. It gives you fine-grained control over various operations and enables you to modify the behavior of objects according to your requirements. However, it's important to use proxies judiciously and avoid unnecessary complexity.