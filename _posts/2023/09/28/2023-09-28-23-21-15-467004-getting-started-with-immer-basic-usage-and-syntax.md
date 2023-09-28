---
layout: post
title: "Getting started with Immer: basic usage and syntax"
description: " "
date: 2023-09-28
tags: [hashtags, Immer]
comments: true
share: true
---

Immer is a popular library in the JavaScript ecosystem that enables **immutable data updates** in a more **convenient and declarative way**. It provides a simple API for working with immutable data structures, making it easier to handle state management in complex applications.

## Installation

To get started with Immer, you first need to install it as a dependency in your project. Open your terminal and run the following command:

```bash
npm install immer
```

## Basic Usage

Once Immer is installed, you can import it into your project using the `import` statement.

```javascript
import produce from "immer";
```

The `produce` function is the main API that Immer provides. It takes two arguments: a **base state** and a **modifier function**. The modifier function receives a **draft state** that you can safely mutate, and any changes made to the draft will be automatically applied to the base state.

Here's an example of how to use Immer to update an object state:

```javascript
const state = {
  name: "John",
  age: 30
};

const nextState = produce(state, (draft) => {
  draft.age += 1;
});

console.log(nextState);
```

In the code above, we start with a `state` object containing a `name` and `age` property. We then use the `produce` function to create a `nextState` by applying changes to the draft state. In this case, we increment the `age` property by 1.

When running the code, we expect the `console.log` statement to output the updated state:

```bash
{ name: "John", age: 31 }
```

## Immer Proxies and Syntax

Immer internally uses ES6 **Proxies** to track changes made to the draft state. This enables a **syntax** that is very similar to working with mutable state. You can read and write properties on the draft state as if it were a normal mutable object.

For example:

```javascript
const nextState = produce(state, (draft) => {
  draft.age += 1;
  draft.name = "Jane";
});
```

In the code above, we increment the `age` property by 1 and simultaneously change the `name` property to "Jane". The changes made inside the modifier function are automatically applied to the draft state.

Additionally, Immer provides a **"curried" version** of the `produce` function, which allows you to create a partially applied producer function for later use. This can be helpful in cases where you want to reuse the same modifier function across different states.

```javascript
const incrementAge = produce((draft) => {
  draft.age += 1;
});

const nextState = incrementAge(state);
```

In the code above, we create an `incrementAge` function using `produce`. This will return a partially applied producer function that increments the `age` property. We can then apply this function to different states to get the desired outcome.

## Conclusion

In this article, we covered the basics of getting started with Immer. We explored its installation process, basic usage, and syntax. Immer simplifies and improves the way we work with immutable data in JavaScript, providing cleaner and more concise code for state management. Start using Immer today to enhance your application's state management capabilities.

#hashtags: #Immer #JavaScript