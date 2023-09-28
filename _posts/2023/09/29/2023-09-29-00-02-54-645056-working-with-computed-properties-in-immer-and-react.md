---
layout: post
title: "Working with computed properties in Immer and React"
description: " "
date: 2023-09-29
tags: [Immer, React]
comments: true
share: true
---

When working with complex state management in React applications, computed properties can be incredibly useful. Computed properties allow us to derive values from existing state, making data manipulation and rendering more efficient.

In this blog post, we will explore how to use computed properties with the Immer library in a React application. Immer is a powerful state management library that allows us to work with immutable state in a more convenient and intuitive way.

## Setting up the project

Before diving into the usage of computed properties, let's set up a basic React project with Immer.

1. Create a new React project using Create React App: `npx create-react-app my-project`.
2. Install Immer as a dependency: 

```bash
npm install immer
```

3. Create a new file called `store.js` in the `src` directory:

```javascript
import produce from 'immer';

export const initialState = {
  counter: 0
};

export const reducer = produce((draft, action) => {
  switch (action.type) {
    case 'INCREMENT':
      draft.counter += 1;
      break;
    case 'DECREMENT':
      draft.counter -= 1;
      break;
    default:
      break;
  }
}, initialState);
```

## Using computed properties with Immer

Now that we have set up our project, let's see how we can leverage computed properties with Immer in a simple counter application.

1. Import the `useImmerReducer` hook from Immer in your `App.js` file:

```javascript
import { useImmerReducer } from 'immer';
```

2. Update the `App` component to use the `useImmerReducer` hook:

```javascript
function App() {
  const [state, dispatch] = useImmerReducer(reducer, initialState);

  // Your component code...

  return (
    <div>
      <h1>Counter: {state.counter}</h1>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
}
```

3. Now, we can define our computed property using a simple function inside the reducer:

```javascript
const reducer = produce((draft, action) => {
  switch (action.type) {
    case 'INCREMENT':
      draft.counter += 1;
      break;
    case 'DECREMENT':
      draft.counter -= 1;
      break;
    default:
      break;
  }

  draft.isPositive = draft.counter > 0; // Computed property

}, initialState);
```

4. Finally, we can render the computed property in our component:

```javascript
return (
    <div>
      <h1>Counter: {state.counter}</h1>
      <h2>{state.isPositive ? 'Positive' : 'Negative'}</h2>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
```

## Conclusion

Computed properties are a powerful tool in managing complex state in React applications. By leveraging the Immer library, we can easily create and update computed properties in an immutable and understandable way.

Using computed properties with Immer not only simplifies our code but also enhances the overall performance of our React application.

Remember to import `produce` from `immer` and use the `useImmerReducer` hook to get started with computed properties in Immer and React.

#Immer #React