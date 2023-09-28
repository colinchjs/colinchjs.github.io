---
layout: post
title: "Understanding the draft state concept in Immer"
description: " "
date: 2023-09-28
tags: [Immer, JavaScript]
comments: true
share: true
---

## What is the draft state?

In Immer, the draft state refers to a mutable copy of your original data. It is created using the `produce` function provided by Immer. This function takes the original state and a callback function, where you can make your desired changes to the draft state.

Here is an example to illustrate the concept:

```javascript
import produce from 'immer';

const originalState = {
  counter: 0,
};

// Using the produce function to create a draft state
const newState = produce(originalState, (draftState) => {
  draftState.counter += 1;
});

console.log(originalState.counter); // Output: 0
console.log(newState.counter); // Output: 1
```

In the above example, we create a new draft state by passing the original state and a callback function to the `produce` function. Inside the callback function, we can make changes to the draft state as if it were mutable. In this case, we increment the `counter` property by 1.

## Modifying the draft state

Once we have the draft state, we can modify it just like we would with mutable data. Immer keeps track of all the changes made to the draft state and creates a new immutable state based on those changes.

If we want to update nested properties in the draft state, we can simply access and modify them like regular JavaScript objects. Here's an example:

```javascript
const originalState = {
  user: {
    name: 'John',
    age: 30,
  },
};

const newState = produce(originalState, (draftState) => {
  draftState.user.age += 1;
});

console.log(originalState.user.age); // Output: 30
console.log(newState.user.age); // Output: 31
```

In the above example, we access the `age` property of the `user` object in the draft state and increment it by 1.

## Performance benefits

One of the advantages of using the draft state concept in Immer is its optimizations for performance. Immer uses a technique called "structural sharing", where it only creates new objects for the parts of the state that have been modified. The unchanged parts of the state are shared between the original and new state, reducing unnecessary memory allocations and improving performance.

## Conclusion

Understanding the draft state concept in Immer is crucial for efficiently working with immutable data in a mutable way. By using the `produce` function and the draft state, you can make changes to your data while ensuring immutability. This not only helps in managing state in large applications but also provides significant performance benefits. Give Immer a try in your next JavaScript project to simplify your state management. #Immer #JavaScript