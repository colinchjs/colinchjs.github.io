---
layout: post
title: "Working with nested arrays immutably in Immer"
description: " "
date: 2023-09-28
tags: [Immer]
comments: true
share: true
---

Immer is a JavaScript library that allows you to work with immutable data in a much simpler way. It provides a convenient API for creating draft copies of your data, making changes to them, and then producing immutable copies.

When it comes to dealing with nested arrays in Immer, you can achieve immutability by creating draft copies of the outer array and the nested arrays. This allows you to make changes to the nested arrays while keeping the original array intact.

## Creating an Immutable Copy with Nested Arrays

To work with nested arrays immutably in Immer, you can follow these steps:

1. Import the `produce` function from the Immer library:

```javascript
import produce from "immer";
```

2. Create an initial state with nested arrays:

```javascript
const state = {
  data: [ [1, 2, 3], [4, 5, 6], [7, 8, 9] ]
};
```

3. Use the `produce` function to create an immutable draft copy of the state:

```javascript
const nextState = produce(state, (draftState) => {
  // Make changes to the draftState here
});
```

4. Modify the nested array within the draftState:

```javascript
const nextState = produce(state, (draftState) => {
  draftState.data[1][0] = 10;
});
```

This will update the value at the specified index of the nested array while maintaining immutability.

## Working with Nested Arrays in Draft Copies

To make changes to the nested arrays in the draft copy, you can access and modify them directly using standard JavaScript array methods, such as `push`, `pop`, `splice`, etc.

```javascript
const nextState = produce(state, (draftState) => {
  draftState.data[0].push(4);
  draftState.data[1].splice(1, 1, 20);
});
```

In the above example, the `push` method is used to add an element to the first nested array, and the `splice` method is used to replace an element in the second nested array.

After making the required changes, the `nextState` will be a new immutable version of the original state.

## Conclusion

Working with nested arrays immutably in Immer is straightforward. By creating draft copies of the outer arrays and then modifying the nested arrays within those drafts, you can achieve immutability without much hassle. Immer simplifies the process and provides an intuitive API for working with immutable data structures in JavaScript.

#Immer #JavaScript