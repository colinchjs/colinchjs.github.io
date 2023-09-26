---
layout: post
title: "Module imports in TypeScript"
description: " "
date: 2023-09-26
tags: [TypeScript, ModuleImports]
comments: true
share: true
---

## 1. Importing a Single Module

To import a single module in TypeScript, we use the `import` statement followed by the module name. Let's say we have a module named `mathUtils` in a file named `utils.ts`:

```typescript
// utils.ts
export function add(a: number, b: number): number {
  return a + b;
}
```

To use the `add` function in another file, we can import it like this:

```typescript
import { add } from './utils';

console.log(add(2, 3)); // Output: 5
```

In the import statement, we specify the curly braces `{}` to destructure the exported functions or variables we want to use. In this case, we only want to import the `add` function.

## 2. Importing Multiple Modules

If we have multiple functions or variables to import from a module, we can list them comma-separated within the curly braces. Let's extend our `utils.ts` module to export more functions:

```typescript
export function subtract(a: number, b: number): number {
  return a - b;
}

export function multiply(a: number, b: number): number {
  return a * b;
}
```

To import both the `add` and `subtract` functions from `utils.ts`, we can do:

```typescript
import { add, subtract } from './utils';

console.log(add(2, 3)); // Output: 5
console.log(subtract(5, 2)); // Output: 3
```

## 3. Importing an Entire Module

Sometimes, we may want to import the entire module and access all its exported functions. We can achieve this using the `* as` syntax. Let's create a new module named `geometry.ts`:

```typescript
// geometry.ts
export function calculateArea(radius: number): number {
  return Math.PI * radius * radius;
}

export function calculateCircumference(radius: number): number {
  return 2 * Math.PI * radius;
}
```

To import all the functions from the `geometry.ts` module, we can do:

```typescript
import * as geometry from './geometry';

console.log(geometry.calculateArea(5)); // Output: 78.53981633974483
console.log(geometry.calculateCircumference(5)); // Output: 31.41592653589793
```

With the `* as` syntax, we assign an alias (`geometry`) to the imported module. We can then access the exported functions using the alias.

## 4. Default Imports

In addition to named exports, TypeScript also supports default exports. A default export can be imported using any name we choose. Let's update our `utils.ts` module to have a default export:

```typescript
// utils.ts
export default function square(x: number): number {
  return x * x;
}
```

To import the default export, we don't need to use curly braces. Instead, we can assign the imported function to any name of our choice:

```typescript
import squareFn from './utils';

console.log(squareFn(5)); // Output: 25
```

In this example, we import the `square` function as `squareFn`, but you can choose any name that makes sense in your codebase.

## Conclusion

In this blog post, we explored different ways of importing modules in TypeScript. Whether it's importing a single module, multiple modules, or importing the entire module, TypeScript provides us with various options to write clean and maintainable code. Using these import techniques, we can effectively manage our project's dependencies and improve code reusability.

#TypeScript #ModuleImports