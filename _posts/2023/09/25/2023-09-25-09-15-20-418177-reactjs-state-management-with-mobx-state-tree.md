---
layout: post
title: "React.js state management with MobX State Tree"
description: " "
date: 2023-09-25
tags: [React, MobXStateTree]
comments: true
share: true
---

State management is a crucial aspect of building complex applications in React.js. One popular solution for managing state is MobX State Tree (MST), which provides a straightforward and scalable way to handle application state in React components. In this blog post, we will explore how to use MobX State Tree for state management in React.js applications.

## What is MobX State Tree?

MobX State Tree is a state management library that works well with React.js. It combines the simplicity and clarity of MobX with the structural modeling capabilities of state trees. MST allows you to define a tree-like structure for your application state, making it easy to create, update, and query specific parts of the state.

## Setting Up the Project

To follow along with this tutorial, let's create a new React.js project and install the necessary dependencies.

1. Create a new project using `create-react-app`:
```shell
npx create-react-app my-app
cd my-app
```

2. Install MobX and MobX State Tree as dependencies:
```shell
npm install mobx mobx-react mobx-state-tree
```

## Defining the State Tree

In MobX State Tree, the application state is represented using a tree-like structure. Each object in the tree is called a *model*, and it can have properties, actions, and relationships with other models.

Let's define a simple state tree for a todo application:

```javascript
import { types } from 'mobx-state-tree';

const Todo = types.model({
  id: types.identifier,
  title: types.string,
  completed: types.boolean,
});

const TodoStore = types.model({
  todos: types.array(Todo),
});

const RootStore = types.model({
  todoStore: TodoStore,
});

const rootStore = RootStore.create({
  todoStore: {
    todos: []
  }
});
```

In the example above, we define three models: `Todo`, `TodoStore`, and `RootStore`. The `Todo` model represents an individual todo item with properties like `id`, `title`, and `completed`. The `TodoStore` model contains an array of todos, and the `RootStore` represents the root of our state tree.

## Working with the State

Now that we have our state tree defined, we can start working with the application state in our React components.

To access the state in a component, we can use the `useContext` hook provided by `mobx-react`:

```javascript
import { useContext } from 'react';
import { RootStoreContext } from './store';

const TodoList = () => {
  const rootStore = useContext(RootStoreContext);
  const todos = rootStore.todoStore.todos;

  return (
    <div>
      {todos.map(todo => (
        <TodoItem key={todo.id} todo={todo} />
      ))}
    </div>
  );
};
```

In the example above, we use the `useContext` hook to access the `rootStore` object from the `RootStoreContext`. We can then access the todos array from `rootStore.todoStore.todos` and render each todo item using a `TodoItem` component.

## Modifying the State

To modify the state, we can use *actions* defined on our models. Actions are responsible for updating the state in a consistent and predictable way.

Let's add a new action to toggle the `completed` flag of a todo:

```javascript
// inside the Todo model
.actions(self => ({
  toggleCompleted() {
    self.completed = !self.completed;
  },
}));
```

In the example above, we add an action called `toggleCompleted` that updates the `completed` property by toggling its current value.

To use this action in our components, we can simply call it on a todo object:

```javascript
const TodoItem = ({ todo }) => {
  const rootStore = useContext(RootStoreContext);

  const handleToggleCompleted = () => {
    todo.toggleCompleted();
  };

  return (
    <div>
      <input
        type="checkbox"
        checked={todo.completed}
        onChange={handleToggleCompleted}
      />
      <span>{todo.title}</span>
    </div>
  );
};
```

In the example above, when the checkbox input is toggled, we call the `toggleCompleted` action on the todo object. This will update the state and reflect the changes in the UI.

## Conclusion

MobX State Tree provides a powerful and scalable state management solution for React.js applications. By defining a well-structured state tree and using actions to modify the state, we can easily manage complex application state while keeping code maintainable and understandable.

Throughout this blog post, we learned how to set up a project with MobX State Tree, define a state tree, work with the state in React components, and modify the state using actions. With these concepts in place, you can start building sophisticated applications with efficient state management using MobX State Tree and React.js.

#React #MobXStateTree