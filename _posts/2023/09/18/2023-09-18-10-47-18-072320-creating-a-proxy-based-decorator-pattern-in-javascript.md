---
layout: post
title: "Creating a proxy-based decorator pattern in JavaScript"
description: " "
date: 2023-09-18
tags: [DecoratorPattern]
comments: true
share: true
---

Decorators are a popular design pattern in JavaScript used to add behavior or modify existing behavior of an object dynamically. In this article, we will explore how to implement a proxy-based decorator pattern in JavaScript.

## What is the Decorator Pattern?

The Decorator pattern allows us to add new functionalities to an object without modifying its original structure. It provides a flexible way to extend the behavior of an object by wrapping it with one or more decorator objects.

## Implementing the Proxy-Based Decorator Pattern

To implement the proxy-based decorator pattern, we will leverage the power of ES6 Proxies. Proxies in JavaScript allow us to create a wrapper object around another object and intercept its operations.

Here's an example of how we can use the proxy-based decorator pattern:

```javascript
class Logger {
  log(message) {
    console.log(`[INFO] ${message}`);
  }
}

class LoggerDecorator {
  constructor(logger) {
    this.logger = logger;
  }
  
  log(message) {
    this.logger.log(`[DECORATOR] ${message}`);
  }
}

// Create an instance of the Logger class
const logger = new Logger();

// Create a proxy object around the logger instance
const decoratedLogger = new Proxy(logger, {
  get(target, prop) {
    if (typeof target[prop] === 'function') {
      return function (...args) {
        console.log('[BEFORE]');
        const result = target[prop].apply(target, args);
        console.log('[AFTER]');
        return result;
      }
    }
    return target[prop];
  }
});

// Use the decorated logger
decoratedLogger.log('Hello, World!');
```

In the above example, we have a `Logger` class that provides a `log` method for logging messages. We also have a `LoggerDecorator` class that wraps around the original logger object and modifies its behavior.

To create a decorated logger, we use a `Proxy` object that intercepts method calls on the logger instance. In the `get` trap, we check if the accessed property is a function. If it is, we execute custom behavior before and after calling the original method.

In this case, before and after calling the `log` method, we print `[BEFORE]` and `[AFTER]` respectively. This allows us to add additional functionality to the original `log` method without modifying the original `Logger` class.

## Conclusion

The proxy-based decorator pattern in JavaScript provides a flexible and non-intrusive way to add behavior to objects dynamically. By using ES6 Proxies, we can intercept method calls and modify their behavior without altering the original object's structure.

By leveraging the power of the decorator pattern, we can easily extend the functionality of existing objects, making our code more modular and maintainable.

#JavaScript #DecoratorPattern