---
layout: post
title: "Using Immer with Angular Universal: integrating Immer into an Angular Universal project"
description: " "
date: 2023-09-28
tags: [angularuniversal, immer]
comments: true
share: true
---

Angular Universal is a server-side rendering solution that allows Angular applications to be rendered on the server before being sent to the client. It provides significant performance benefits and improves SEO by generating static HTML pages for search engine crawlers.

Immer is a popular immutable state management library that allows developers to work with immutable data structures in a more intuitive way. It simplifies the process of updating complex data structures by leveraging a copy-on-write mechanism.

In this article, we will explore how to integrate Immer into an Angular Universal project, enabling us to take advantage of its simplicity and expressiveness when working with immutable state.

## Step 1: Install Immer

Before we can integrate Immer into our Angular Universal project, we need to install it. Open a terminal or command prompt, navigate to your project's root directory, and run the following command:

```bash
npm install immer
```

## Step 2: Import Immer into your Angular Universal application

Next, we need to import Immer into our Angular Universal application. Open the file where your application's state is defined, typically in a service or a store.

```typescript
import { produce } from 'immer';

// Define your initial state
const initialState = {
  // ...
};

// Use Immer's produce function to create a mutable draft of the state
const newState = produce(initialState, draft => {
  // Make changes to the draft
  draft.someProperty = 'new value';
});

// Export the final state
export const state = newState;
```

In the above example, we import the `produce` function from Immer and use it to create a mutable draft of our initial state. Within the `produce` function, we can make changes to the draft as if it were mutable. Immer then takes care of creating a new immutable state based on our changes.

## Step 3: Update your Angular Universal components

Once we have integrated Immer into our state management, we can update our Angular Universal components to consume the new immutable state.

```typescript
import { Component } from '@angular/core';
import { state } from './state'; // Import your state

@Component({
  selector: 'app-root',
  template: `
    <div>
      <p>State: {{ state | json }}</p>
      <button (click)="updateState()">Update State</button>
    </div>
  `
})
export class AppComponent {
  state = state; // Assign the state to a component property

  updateState() {
    const newState = produce(this.state, draft => {
      // Make changes to the draft
      draft.someProperty = 'updated value';
    });

    this.state = newState; // Assign the new state to the component property
  }
}
```

In the above example, we import the state from our state management module and assign it to a component property. When the "Update State" button is clicked, we create a new mutable draft of our state using Immer's `produce` function. We can then make changes to the draft and assign the resulting immutable state back to the component property.

By following these steps, we have successfully integrated Immer into our Angular Universal project and can now take advantage of its simplified immutable state management. This allows us to work with complex data structures in a more intuitive way, improving the maintainability and performance of our application.

#angularuniversal #immer