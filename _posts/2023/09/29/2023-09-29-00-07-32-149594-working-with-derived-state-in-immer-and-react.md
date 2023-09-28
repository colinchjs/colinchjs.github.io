---
layout: post
title: "Working with derived state in Immer and React"
description: " "
date: 2023-09-29
tags: [Immer, React]
comments: true
share: true
---

Derived state is a concept in React where you compute a value based on the current state or props of a component. It can be useful when you need to manipulate or transform the data before using it in your component.

Immer is a library that makes working with immutable data structures in JavaScript much easier. It allows you to create a "draft" of your state, make changes to it in a mutable way, and then produce an updated immutable state. This can be especially handy when dealing with derived state.

In this blog post, we will explore how to work with derived state using Immer and React.

## Setting up the project

First, let's create a new React project using Create React App. Open your terminal and run the following command:
```
npx create-react-app derived-state-example
```

Once the project is created, navigate to the project directory:
```
cd derived-state-example
```

Next, we need to install Immer. Run the following command to install it as a dependency:
```
npm install immer
```

## Adding derived state to a component

Let's assume we have a component called `UserList` that displays a list of users fetched from an API. The original state of the component is an empty array, and we want to calculate the total number of users in the list as a derived state.

To handle derived state, we will be using the `produce` function from Immer. The `produce` function takes a function as an argument, which receives the draft state and allows you to make changes to it.

```jsx
import React, { useState } from 'react';
import produce from 'immer';

const UserList = () => {
  const [users, setUsers] = useState([]);
  const [userCount, setUserCount] = useState(0);

  useEffect(() => {
    // Fetch users from API and update state
  }, []);

  useEffect(() => {
    // Calculate user count as derived state
    const count = produce(users, draft => {
      draft.length = draft.length;
    });

    setUserCount(count);
  }, [users]);

  return (
    <div>
      <h2>User List</h2>
      <p>Total users: {userCount}</p>
      {/* Render user list */}
    </div>
  );
};

export default UserList;
```

In the above code, we first import the `produce` function from Immer. We then set up two hooks: `users`, which holds the array of users fetched from the API, and `userCount`, which will hold the derived state of the total number of users.

The first `useEffect` hook is responsible for fetching the users from the API and updating the `users` state.

The second `useEffect` hook is where we calculate the derived state of `userCount`. We use the `produce` function to create a draft copy of the `users` array. By assigning the current length of the draft to itself, we effectively update the length property. We then set the derived `count` as the new value of `userCount` state.

In the component's JSX, we display the derived state of `userCount` and render the list of users.

## Conclusion

Working with derived state can be made easier with the use of Immer in React. By using the `produce` function, we can manipulate the state in an immutable way and compute derived values based on the current state. This allows for more efficient and cleaner code.

By following the steps outlined in this blog post, you should now have a better understanding of how to work with derived state in Immer and React.

#Immer #React