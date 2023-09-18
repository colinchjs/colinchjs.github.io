---
layout: post
title: "How to handle errors and fallbacks in JavaScript Module Federation with Webpack 5"
description: " "
date: 2023-09-18
tags: [JavaScript, ModuleFederation]
comments: true
share: true
---

In modern web development, **JavaScript Module Federation** has taken center stage as a powerful technique for building microfrontend architectures. With the release of **Webpack 5**, the concept of Module Federation has become even more robust and flexible. However, when working with distributed and federated modules, it is crucial to handle errors and fallbacks effectively to ensure a seamless user experience. In this blog post, we will explore how to handle errors and implement fallbacks in JavaScript Module Federation with Webpack 5.

## Error Handling in Module Federation

When modules are distributed across different microfrontends, errors can occur during module loading or script execution. Handling these errors gracefully is essential in order to provide a better user experience and prevent the entire application from breaking down.

Webpack 5 introduces two new approaches for handling errors in Module Federation:

### 1. Module Load Error Handling

To handle errors during module loading, we can utilize the `remoteEntry` config option's `error` callback. This callback is invoked when there is an error loading a remote module. Inside the callback, we can implement custom error handling logic, such as displaying an error message or fallback UI.

Here's an example of how to handle module loading errors:

```javascript
// webpack.config.js of host application

module.exports = {
  // ... other webpack config options
  experiments: {
    topLevelAwait: true,
  },
  plugins: [
    new ModuleFederationPlugin({
      // ... other module federation options
      remotes: {
        remoteApp: "remoteApp@http://remoteappurl/remoteEntry.js",
      },
      error: (err) => {
        // Handle module load error here
      },
    }),
  ],
};
```

### 2. Script Execution Error Handling

Sometimes, errors can occur in the remote module's script execution itself. To handle such errors, we can wrap the remote module's script in a `try-catch` block and provide a fallback implementation or error message.

Here's an example of how to handle script execution errors:

```javascript
// index.js of remote module

try {
  // Code that might throw an error
} catch (error) {
  // Fallback implementation or error message
}
```

## Fallbacks in Module Federation

Fallbacks are vital to ensure that our distributed modules can gracefully handle scenarios where a remote module is not available or fails to load. By providing fallback implementations, we can prevent the entire application from breaking down due to unavailability of a specific module.

Webpack 5 offers two techniques to implement fallbacks in Module Federation:

### 1. localFallback

The `localFallback` option in the Module Federation configuration allows us to define a fallback module when a remote module fails to load. This fallback module will be used in place of the remote module, ensuring that the application continues to function correctly.

```javascript
// webpack.config.js of host application

module.exports = {
  // ... other webpack config options
  plugins: [
    new ModuleFederationPlugin({
      // ... other module federation options
      remotes: {
        remoteApp: "remoteApp@http://remoteappurl/remoteEntry.js",
      },
      fallback: {
        remoteApp: "fallbackRemoteApp",
      },
    }),
  ],
};
```

### 2. Runtime Fallback

The runtime fallback allows us to programmatically handle fallback scenarios. We can use the `fallback` function provided by the `webpack/container` module to implement custom fallback logic based on specific conditions, such as network errors or unavailable remote modules.

```javascript
// index.js of host application

import { fallback } from "webpack/container";

// Load the remote module with fallback handling
const remoteAppContainer = fallback(await import("remoteApp"));

// Use the remote module or fallback implementation
const App = remoteAppContainer?.App || FallbackComponent;
```

## Conclusion

With JavaScript Module Federation and Webpack 5, we can build powerful microfrontend architectures. Handling errors and implementing fallbacks is crucial to provide a seamless user experience and prevent the entire application from breaking down due to a failure in a specific module. By utilizing the new error handling features in Webpack 5 and the flexibility of Module Federation, we can create robust applications that gracefully handle errors and fallback scenarios. Happy coding!

## #JavaScript #ModuleFederation