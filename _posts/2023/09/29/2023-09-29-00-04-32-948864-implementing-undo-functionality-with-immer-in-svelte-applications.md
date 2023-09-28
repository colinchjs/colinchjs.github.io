---
layout: post
title: "Implementing undo functionality with Immer in Svelte applications"
description: " "
date: 2023-09-29
tags: [sveltejs, Immer]
comments: true
share: true
---

In many applications, having the ability to undo and redo actions is a crucial feature. With Immer, a powerful state management library, you can easily add undo functionality to your Svelte applications. In this blog post, we'll explore the steps to implement undo functionality using Immer.

## Setting up the project

First, let's set up a new Svelte project. Open your terminal and run the following commands:

```bash
npx degit sveltejs/template svelte-immer-undo
cd svelte-immer-undo
npm install
```

## Installing Immer

Next, let's install Immer by running the following command in your project directory:

```bash
npm install immer
```

## Adding undo functionality

To implement undo functionality, we'll use Immer's `produce` function to create a draft of our state and track the history of actions applied to it. Here's an example implementation for a simple counter component:

```javascript
// Counter.svelte
<script>
  import { produce } from 'immer';
  import { writable, get } from 'svelte/store';

  const initialState = { count: 0 };
  const undoHistory = [];
  const redoHistory = [];

  export let count = writable(initialState.count);

  function increment() {
    const currentState = get(count);

    // Create a draft of the state and apply the increment action
    const nextState = produce(currentState, draft => {
      draft.count += 1;
    });

    // Push the current state to the undo history
    undoHistory.push(currentState);

    // Update the count store with the new state
    count.set(nextState);
  }

  function undo() {
    if (undoHistory.length > 0) {
      const previousState = undoHistory.pop();

      // Push the current state to the redo history
      redoHistory.push(get(count));

      // Set the count store to the previous state
      count.set(previousState);
    }
  }

  function redo() {
    if (redoHistory.length > 0) {
      const nextState = redoHistory.pop();

      // Push the current state to the undo history
      undoHistory.push(get(count));

      // Set the count store to the next state
      count.set(nextState);
    }
  }
</script>

<button on:click={increment}>Increment</button>
<p>Count: {$count}</p>
<button on:click={undo}>Undo</button>
<button on:click={redo}>Redo</button>
```

In the example above, we use Svelte's `writable` store to manage the state and keep track of the history of actions. The `undo` function pops the last state from the undo history and sets it as the current state, while the `redo` function does the opposite, allowing us to redo previously undone actions.

## Summary

Adding undo functionality to your Svelte applications can greatly enhance the user experience. With Immer's powerful `produce` function, managing state and tracking action history becomes a breeze. By following the steps outlined in this blog post, you can easily implement undo functionality in your Svelte applications using Immer.

Give it a try and elevate your application to the next level!

#sveltejs #Immer #state-management #undo-functionality