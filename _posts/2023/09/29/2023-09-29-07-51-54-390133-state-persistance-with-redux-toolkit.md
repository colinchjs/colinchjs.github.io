---
layout: post
title: "State persistance with Redux Toolkit"
description: " "
date: 2023-09-29
tags: [redux, persist]
comments: true
share: true
---

In Redux applications, managing the state and its persistence across sessions is a crucial aspect. Redux Toolkit provides a straightforward way to handle state persistence using middleware and local storage. In this blog post, we will explore how to persist the state in a Redux Toolkit application.

## Setting Up Redux Toolkit

To get started, make sure you have an existing Redux Toolkit setup or create a new one using the `@reduxjs/toolkit` package. The Redux Toolkit provides a simplified way to configure the Redux store and handle actions and reducers.

## Adding Redux Persist Middleware

To enable state persistence, we need to install the `redux-persist` library:

```shell
npm install redux-persist
```

Next, import the necessary functions from `redux-persist` and create a `persistMiddleware`:

```javascript
import { persistStore, persistReducer } from 'redux-persist';
import storage from 'redux-persist/lib/storage';

// ...

const persistConfig = {
  key: 'root',
  storage,
};

const persistedReducer = persistReducer(persistConfig, rootReducer);
const store = configureStore({
  reducer: persistedReducer,
  middleware: [/* other middleware */, persistMiddleware],
});

persistStore(store);
```

In the above code, we define a `persistConfig` object that specifies the key for the root of the state and the storage method. We use the `storage` function from `redux-persist/lib/storage` to persist the state in the local storage of the browser.

After defining the `persistConfig`, we create a persisted reducer by calling `persistReducer(persistConfig, rootReducer)` and assign it to the `reducer` property of the store's configuration.

Finally, we call `persistStore(store)` to initialize state persistence.

## Adding Auto Rehydrate

By default, Redux Toolkit doesn't provide auto rehydration, which means the app state won't be automatically loaded back from local storage on page refresh. To enable auto rehydration, we can make use of the `redux-persist-autohydrate` package.

First, install the package:

```shell
npm install redux-persist-autohydrate
```

Once installed, add the following code after the `persistStore(store)` line:

```javascript
import { autoRehydrate } from 'redux-persist-autohydrate';

// ...

const store = configureStore({
  // ...
  enhancers: [autoRehydrate()],
});

persistStore(store);
```

Now, the application state will be automatically rehydrated on page refresh, ensuring a seamless experience for the user.

## Conclusion

With the help of Redux Toolkit and the `redux-persist` library, we can easily persist and rehydrate the state in a Redux application. By configuring the `persistConfig` object and adding the necessary middleware, we can ensure that the state is preserved across sessions, providing a more user-friendly experience.

#redux #persist #state #persistence