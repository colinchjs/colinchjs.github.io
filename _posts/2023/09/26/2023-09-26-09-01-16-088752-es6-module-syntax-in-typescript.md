---
layout: post
title: "ES6 module syntax in TypeScript"
description: " "
date: 2023-09-26
tags: [typescript, ES6modules]
comments: true
share: true
---

TypeScript is a superset of JavaScript that brings static typing to the JavaScript ecosystem. It also supports ES6 module syntax, which allows you to write modular and reusable code. In this blog post, we will explore how to use ES6 module syntax in TypeScript.

## Importing modules

To import a module in TypeScript, you can use the `import` keyword followed by the module path. For example, if you have a module named `calculator` with a function named `add`, you can import it as follows:

```typescript
import { add } from './calculator';
```

The `add` function is now accessible in your current file, and you can use it like any other JavaScript function.

## Exporting modules

To export a module in TypeScript, you can use the `export` keyword. You can export multiple variables, functions, or classes from a single module.

```typescript
export function add(a: number, b: number) {
  return a + b;
}

export function subtract(a: number, b: number) {
  return a - b;
}

export class Calculator {
  constructor(private a: number, private b: number) {}

  multiply() {
    return this.a * this.b;
  }
}
```

Now, other files can import the `add`, `subtract`, and `Calculator` from this module.

## Default exports

In addition to named exports, TypeScript also supports default exports. A default export represents the main object or function in a module.

```typescript
export default function greet(name: string) {
  console.log(`Hello, ${name}!`);
}
```

To import a default export, you can use any name of your choice:

```typescript
import sayHello from './greeting';
```

Here, the `sayHello` function is the default export from the `greeting` module.

## Conclusion

ES6 module syntax provides a clean and organized way to structure your code. With TypeScript, you get the benefits of static typing and module imports/exports. By using the `import` and `export` keywords, you can write modular and reusable code and improve the maintainability of your TypeScript projects.

#typescript #ES6modules