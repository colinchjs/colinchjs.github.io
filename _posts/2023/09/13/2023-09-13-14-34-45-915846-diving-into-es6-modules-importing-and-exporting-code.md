---
layout: post
title: "Diving into ES6 Modules: Importing and Exporting Code"
description: " "
date: 2023-09-13
tags: [modules, import, export]
comments: true
share: true
---

With the release of ECMAScript 6 (ES6), JavaScript introduced a new module syntax that allows developers to easily import and export code between different files and projects. This new module system brings several benefits, including improved organization, code reusability, and better encapsulation.

## Importing Modules

To import code from another module, you can use the `import` keyword followed by the module name and the specific elements you want to import. Let's start by importing a single named export:

```javascript
import { functionName } from './module';
```

In this example, we are importing the `functionName` exported by the `module.js` file into our current module. The relative path to the module file is specified using the `./` notation.

You can also import multiple named exports by separating them with commas:

```javascript
import { functionName1, functionName2 } from './module';
```

If the module exports a default export, you can import it using the `import` keyword followed by a name of your choice. Typically, you use the same name as the exported module, but it is not mandatory:

```javascript
import customName from './module';
```

## Exporting Modules

In order to make functions, variables, or classes available for use in other modules, you need to export them. There are two common ways to export code from a module: named exports and default exports.

### Named Exports

Named exports allow you to export multiple functions, variables, or classes from a module. You can export them individually or group them together using the `export` keyword:

```javascript
export function functionName1() {
  // Function implementation
}

export const variableName = 'value';

export class ClassName {
  // Class implementation
}
```

When importing named exports from another module, you need to use the brackets `{}` syntax to specify the names of the elements you want to import.

### Default Export

Default exports allow you to export a single element as the default export of a module. Typically, this element is the main entity or functionality of the module. You can define the default export using the `export default` syntax:

```javascript
const mainFunction = () => {
  // Function implementation
}

export default mainFunction;
```

When importing a default export from another module, you can choose any name for it:

```javascript
import customName from './module';
```

## Conclusion

ES6 modules provide a powerful way to organize and modularize your JavaScript code. By utilizing `import` and `export`, you can easily share and reuse code across different files and projects, making your development process more efficient and maintainable.

#javascript #ES6 #modules #import #export