---
layout: post
title: "Working with derived state in Immer"
description: " "
date: 2023-09-28
tags: [Tech]
comments: true
share: true
---

Immer is a powerful JavaScript library that allows us to work with immutable data structures in a more convenient and intuitive way. One of the key features of Immer is the ability to create derived state, which allows us to calculate values based on the original state.

Derived state is useful when we need to compute some value based on the current state, but we don't want to mutate the original state. Instead, we want to create a new state object that includes the derived value.

Let's say we have a simple state object representing a shopping cart:

```javascript
const cart = {
  items: ['apple', 'banana', 'orange'],
  count: 3
};
```

Now, let's imagine we want to calculate the total price of all the items in the cart. Normally, we would have to manually iterate over the items array and calculate the total price. With Immer, we can use derived state to make this process easier.

Here's how we can achieve this using Immer:

```javascript
import produce from 'immer';

const cart = {
  items: ['apple', 'banana', 'orange'],
  count: 3
};

const stateWithTotalPrice = produce(cart, (draft) => {
  draft.totalPrice = draft.items.reduce((acc, item) => {
    return acc + calculatePrice(item);
  }, 0);
});

console.log(stateWithTotalPrice);
```

In the code above, we use the `produce` function from Immer to create a new state object (`stateWithTotalPrice`). Inside the callback function, we can access and modify the `draft` object, which is a mutable copy of the original state. We then calculate the total price by iterating over the items array and use `reduce` function to accumulate the sum.

With derived state, we don't have to worry about mutating the original state. Immer takes care of creating a new state object with the desired derived value. This makes our code more readable and less error-prone.

# Conclusion

Derived state is a powerful feature provided by Immer that allows us to calculate values based on the original state without mutating it. By using `produce` function from Immer, we can create new state objects with derived values easily and efficiently. This improves the readability and maintainability of our code.

#Tech #JavaScript