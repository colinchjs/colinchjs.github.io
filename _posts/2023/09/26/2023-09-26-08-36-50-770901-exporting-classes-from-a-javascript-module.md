---
layout: post
title: "Exporting classes from a JavaScript module"
description: " "
date: 2023-09-26
tags: [JavaScript, Modules]
comments: true
share: true
---

To export a class from a JavaScript module, you need to use the `export` keyword. Here's an example:

```javascript
// In module.js

// Exporting a single class
export class MyClass {
  constructor() {
    // Constructor logic
  }

  // Class methods
  method1() {
    // Method logic
  }

  method2() {
    // Method logic
  }
}

// Exporting multiple classes
export class OtherClass {
  constructor() {
    // Constructor logic
  }

  // Class methods
  method1() {
    // Method logic
  }

  method2() {
    // Method logic
  }
}
```

In the above code snippet, we have defined two classes: `MyClass` and `OtherClass`. Each class is exported using the `export` keyword. This makes these classes accessible to other modules that import this module. 

To import and use these exported classes in another module, you can use the `import` statement. Here's an example:

```javascript
// In main.js

// Importing a single class
import { MyClass } from './module.js';

const instance = new MyClass();
instance.method1();

// Importing multiple classes
import { MyClass, OtherClass } from './module.js';

const instance1 = new MyClass();
const instance2 = new OtherClass();

instance1.method1();
instance2.method2();
```

In the above code snippet, we import the exported classes `MyClass` and `OtherClass` from the `module.js` file. We can then create instances of these classes and call their methods as needed.

Exporting classes from a JavaScript module allows you to organize your code and make it more modular. It also enables other modules to easily import and use the exported classes, promoting code reuse and maintainability.

#JavaScript #Modules