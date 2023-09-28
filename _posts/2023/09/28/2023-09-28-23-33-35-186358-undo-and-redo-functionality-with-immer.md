---
layout: post
title: "Undo and redo functionality with Immer"
description: " "
date: 2023-09-28
tags: []
comments: true
share: true
---

In many applications, especially those involving complex state management, having the ability to undo and redo actions is crucial. Undo and redo functionality allows users to revert back to previous states of the application, providing a sense of control and flexibility.

`Immer` is a library that simplifies immutable state updates in JavaScript applications. It allows you to work with immutable data structures in a more intuitive and convenient way. In this blog post, we'll explore how to implement undo and redo functionality using `Immer`.

## Installing Immer

To get started, you'll need to install `Immer` in your project. You can do this by running the following command:

```bash
npm install immer
```

## Setting Up the State

To implement undo and redo functionality, we need to keep track of the state history. We can achieve this by maintaining an array of state snapshots. Whenever an action is performed, we'll create a new snapshot of the state and push it into the array.

Here's an example of how you can set up the state and the state history:

```javascript
import produce from 'immer';

// Initial state
const initialState = {
  counter: 0
};

// State history
const stateHistory = [];

// Reducer function using Immer
const reducer = produce((draft, action) => {
  switch (action.type) {
    case 'INCREMENT':
      draft.counter++;
      break;
    case 'DECREMENT':
      draft.counter--;
      break;
    // Add more actions here
    default:
      break;
  }
});

// Initial state snapshot
stateHistory.push(initialState);
```

## Adding Undo and Redo Functionality

Now that we have our state and state history set up, we can add the undo and redo functionality.

To undo an action, we'll simply pop the last state snapshot from the state history and make it the current state. To redo an action, we'll push a new state snapshot into the state history based on the current state.

Here's an example of how you can implement the undo and redo functionality:

```javascript
// Undo action
function undo() {
  if (stateHistory.length > 1) {
    stateHistory.pop();
  }
}

// Redo action
function redo() {
  if (currentState !== stateHistory[stateHistory.length - 1]) {
    const nextState = reducer(currentState, { type: 'NOOP' });
    stateHistory.push(nextState);
  }
}
```

## Updating the UI

Finally, we need to update the UI to reflect the current state. Whenever the state changes, we can render the updated state on the screen.

```javascript
function render() {
  const currentState = stateHistory[stateHistory.length - 1];
  // Render the UI with the current state
  console.log(currentState);
}

// Call the render function whenever the state changes
render();
```

## Conclusion

By using `Immer`, we can easily implement undo and redo functionality in our JavaScript applications. With state history management and the power of immutable updates, users can navigate between different application states, providing a seamless user experience.

Remember to install `Immer` in your project, set up the state and state history, and implement the undo and redo functionality accordingly.