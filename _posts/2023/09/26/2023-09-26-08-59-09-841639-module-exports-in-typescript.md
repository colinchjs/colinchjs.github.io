---
layout: post
title: "Module exports in TypeScript"
description: " "
date: 2023-09-26
tags: [TypeScript, ModuleExports]
comments: true
share: true
---

In TypeScript, you can use module exports to make your code more modular and reusable. Module exports allow you to define which parts of a file can be accessed by other files in your project.

## Exporting a Single Value

To export a single value from a TypeScript module, you can use the `export` keyword followed by the value you want to export. Here's an example:

```typescript
// mathUtils.ts

export function add(a: number, b: number): number {
    return a + b;
}

export const PI = 3.14159;
```

In the above example, we export a function `add` and a constant `PI` from the `mathUtils.ts` file. These exports can now be used in other files by importing them.

## Exporting Multiple Values

If you have multiple values that you want to export from a module, you can use the `export` keyword before each value declaration. Here's an example:

```typescript
// utils.ts

export function capitalize(str: string): string {
    return str.charAt(0).toUpperCase() + str.slice(1);
}

export function reverse(str: string): string {
    return str.split("").reverse().join("");
}
```

In the above example, we export two functions `capitalize` and `reverse` from the `utils.ts` file. These functions can be imported and used in other files.

## Default Export

In addition to named exports, TypeScript also supports default exports. A default export is used when you want to export a single value as the default export of a module. Here's an example:

```typescript
// logger.ts

export default function log(message: string): void {
    console.log(message);
}
```

In the above example, we export a single function `log` as the default export of the `logger.ts` file. When importing a default export, you can give it any name you want.

## Importing Exported Values

To use exported values from a module in another file, you need to import them. Here's an example of importing the previously exported functions:

```typescript
// app.ts

import { add, PI } from './mathUtils';
import { capitalize, reverse } from './utils';
import log from './logger';

console.log(add(2, 3)); // Output: 5
console.log(PI); // Output: 3.14159
console.log(capitalize('hello')); // Output: Hello
console.log(reverse('world')); // Output: dlrow
log('Hello, logger!'); // Output: Hello, logger!
```

In the above example, we import the `add` function and the `PI` constant from the `mathUtils.ts` file, the `capitalize` and `reverse` functions from the `utils.ts` file, and the `log` function as the default export from the `logger.ts` file.

By using module exports in TypeScript, you can create more organized and modular codebases, making it easier to reuse and maintain your code. 

#TypeScript #ModuleExports