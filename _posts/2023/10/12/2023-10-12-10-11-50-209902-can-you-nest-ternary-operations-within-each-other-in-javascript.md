---
layout: post
title: "Can you nest ternary operations within each other in JavaScript?"
description: " "
date: 2023-10-12
tags: []
comments: true
share: true
---

Here's an example of nesting ternary operations in JavaScript:

```javascript
const number = 10;

const result = number > 5 ? (number > 10 ? "Greater than 10" : "Greater than 5") : "Less than or equal to 5";

console.log(result);
```

In this example, we have a nested ternary operation. If the `number` variable is greater than 5, it moves on to the inner ternary operation `(number > 10 ? "Greater than 10" : "Greater than 5")`. If the `number` is greater than 10, it returns the string `"Greater than 10"`, otherwise it returns the string `"Greater than 5"`. If the `number` is not greater than 5, the outer ternary operation returns the string `"Less than or equal to 5"`.

Nesting ternary operations can be useful for creating more complex conditional logic in a concise manner. However, it's important to use them judiciously to maintain readability and avoid overly complex code.