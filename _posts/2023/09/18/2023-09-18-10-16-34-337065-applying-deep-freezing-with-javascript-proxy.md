---
layout: post
title: "Applying deep freezing with JavaScript Proxy"
description: " "
date: 2023-09-18
tags: [javascript, programming]
comments: true
share: true
---

In JavaScript, the `Proxy` object is a powerful feature that allows us to create a customizable wrapper around another object. This wrapper object can intercept and handle various operations performed on the target object, including accessing and modifying its properties.

One interesting use case of `Proxy` is to implement deep freezing of objects. Freezing an object prevents any modifications to its properties, making it effectively read-only. However, by default, JavaScript's `Object.freeze()` method only freezes the top-level properties of an object. Any nested objects can still be modified. This is where `Proxy` comes in handy.

Here's an example of how to apply deep freezing using `Proxy`:

```javascript
function deepFreeze(obj) {
  const handler = {
    get(target, prop) {
      const value = Reflect.get(target, prop);
      if (typeof value === "object" && value !== null) {
        return deepFreeze(value);
      }
      return value;
    },
    set() {
      throw new Error("Cannot modify a frozen object");
    },
    deleteProperty() {
      throw new Error("Cannot delete a property from a frozen object");
    },
  };

  return new Proxy(obj, handler);
}

// Usage example
const user = deepFreeze({
  name: "John Doe",
  age: 30,
  address: {
    street: "123 Main St",
    city: "New York",
  },
});

user.name = "Jane Smith"; // Throws an error
user.address.city = "San Francisco"; // Throws an error
delete user.age; // Throws an error
```

In the code above, we define a `deepFreeze` function that accepts an object as a parameter and returns a frozen version of it using `Proxy`. The `handler` object contains traps for `get`, `set`, and `deleteProperty` operations. By throwing an error in those traps, we prevent any modifications to the frozen object.

When a property is accessed using the `get` trap, we recursively apply the `deepFreeze` function to any nested objects. This ensures that all levels of the object hierarchy are frozen.

When using the `deepFreeze` function, any attempts to modify properties or delete them will result in an error being thrown, preventing any unintended changes to the frozen object.

By leveraging the `Proxy` object, we can implement deep freezing in JavaScript and have complete control over the immutability of an object and its nested properties.

#javascript #programming