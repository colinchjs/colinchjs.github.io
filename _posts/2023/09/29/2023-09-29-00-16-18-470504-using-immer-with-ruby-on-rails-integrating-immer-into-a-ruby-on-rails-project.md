---
layout: post
title: "Using Immer with Ruby on Rails: integrating Immer into a Ruby on Rails project"
description: " "
date: 2023-09-29
tags: [Immer, RubyOnRails]
comments: true
share: true
---

As a Ruby on Rails developer, you may be familiar with the challenges of managing complex state in your applications. **Immer** is a powerful library that can help simplify state management by providing a convenient way to work with immutable data structures.

In this blog post, we will explore how to integrate Immer into a Ruby on Rails project and discuss the benefits it offers for managing application state.

## What is Immer?

**Immer** is a JavaScript library that allows you to work with immutable state in a more convenient and intuitive way. It provides a simple API that makes it easy to create and update immutable data structures, reducing the boilerplate code required for state management.

Immer achieves this by using a concept called "structural sharing." When you make changes to an immutable data structure, Immer creates a new version of the structure with only the modified parts, sharing as much data as possible with the original structure. This makes updates efficient and ensures that your application performs well even with large and complex state objects.

## Installing Immer in your Ruby on Rails project

To get started with Immer in a Ruby on Rails project, follow these steps:

1. Open your Gemfile and add the `immer-rails` gem:

    ```ruby
    gem 'immer-rails'
    ```

2. Run the bundle install command to install the gem:

    ```bash
    $ bundle install
    ```

3. In your JavaScript manifest file (`app/assets/javascripts/application.js`), require the Immer library:

    ```javascript
    //= require immer
    ```

## Using Immer in Ruby on Rails

Now that you have Immer installed in your Ruby on Rails project, let's see how you can leverage its features for state management.

### Creating an immutable state

To create an immutable state object using Immer, you can use the `produce` function provided by Immer. This function takes an initial state object and a "recipe" function, which defines how you want to modify the state. The recipe function receives a "draft state" object that you can freely modify, and your changes will be automatically applied to the new state object returned by `produce`.

Here's an example:

```javascript
const initialState = {
  counter: 0,
};

const newState = Immer.produce(initialState, draft => {
  draft.counter++;
});
```

In this example, we start with an initial state object containing a `counter` property. The `produce` function allows us to modify the state by incrementing the `counter` property. The result is a new state object with the updated value.

### Updating immutable state

Immer provides a convenient and intuitive way to update immutable state using the "draft state" object. Instead of directly modifying the state object, you can update it in a more familiar imperative style.

Here's an example:

```javascript
const newState = Immer.produce(currentState, draft => {
  draft.counter++;
  draft.completed = true;
});
```

In this example, we increment the `counter` property and set the `completed` property to `true` using the draft state object. Immer takes care of creating the new state object with the updated changes.

### Using Immer with Redux

If you're using Redux in your Ruby on Rails project, integrating Immer is even easier. You can simply replace the `redux` npm package with `immer` and use the same store and reducer setup. The only difference is that you can now update the state more conveniently using the Immer's `produce` function within the reducer.

```javascript
import Immer from 'immer';

const reducer = (state = initialState, action) => {
  return Immer.produce(state, draft => {
    // update draft state based on action
  });
};
```

## Conclusion

Integrating Immer into your Ruby on Rails project can greatly simplify state management and make your code more maintainable. By leveraging Immer's convenient API for working with immutable data structures, you can reduce the complexity of state updates and eliminate potential bugs caused by mutable state.

While there might be a slight learning curve at the beginning, the benefits of using Immer will quickly become apparent as your application grows in size and complexity.

Give Immer a try in your Ruby on Rails projects and experience the power of immutability in state management! #Immer #RubyOnRails