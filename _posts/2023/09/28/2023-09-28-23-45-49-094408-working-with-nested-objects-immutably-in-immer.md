---
layout: post
title: "Working with nested objects immutably in Immer"
description: " "
date: 2023-09-28
tags: [immutable, nested]
comments: true
share: true
---

Immer is a popular JavaScript library that allows you to work with immutable data structures in an intuitive way. One common use case is working with nested objects, where you need to update specific properties without mutating the original object. In this blog post, we'll explore how to work with nested objects immutably using Immer.

## Installing Immer

Before we begin, make sure you have Immer installed in your project. You can install it via npm by running the following command:

```
npm install immer
```

## Updating nested properties

Let's say we have an object `myObject` with the following structure:

```javascript
const myObject = {
  foo: {
    bar: {
      value: 10
    }
  }
};
```

Now, we want to update the `value` property inside the `bar` object, without mutating `myObject`. We can achieve this using Immer's `produce` function:

```javascript
import produce from 'immer';

const updatedObject = produce(myObject, draft => {
  draft.foo.bar.value = 20;
});
```

In this code snippet, `produce` takes the original object (`myObject`) and a callback function that allows us to make modifications to a **draft** of the object. The `draft` behaves like a mutable copy of the original object, but behind the scenes, Immer tracks and applies the changes immutably.

## Updating nested properties using nested callbacks

In case the nesting of the object is deeper, Immer provides us with a convenient way to update multiple nested properties using multiple callbacks. Let's consider an example with a more complex object structure:

```javascript
const myObject = {
  foo: {
    bar: {
      value: 10
    },
    baz: {
      value: 5
    }
  }
};
```

To update both `value` properties in `bar` and `baz`, we can nest the callbacks:

```javascript
const updatedObject = produce(myObject, draft => {
  draft.foo.bar.value = 20;
  draft.foo.baz.value = 15;
});
```

## Conclusion

Immer is a powerful library that simplifies working with nested objects immutably in JavaScript. By using the `produce` function and draft objects, you can update specific properties without mutating the original object. This approach enhances code maintainability and helps prevent unexpected bugs.

Remember to install Immer in your project and start leveraging its immutability capabilities for working with nested objects effectively.

#immutable #nested-objects