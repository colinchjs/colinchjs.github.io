---
layout: post
title: "Can you use ternary operations to compare two values in JavaScript?"
description: " "
date: 2023-10-12
tags: []
comments: true
share: true
---

The syntax for a ternary operation is:
```javascript
condition ? expression1 : expression2
```

If the condition is true, `expression1` will be evaluated, otherwise `expression2` will be evaluated.

Here's an example to compare two values using a ternary operation:

```javascript
const num1 = 10;
const num2 = 5;

const result = num1 > num2 ? "num1 is greater" : "num2 is greater";

console.log(result);
```

In this example, we compare `num1` and `num2` using the `>` operator. If `num1` is greater than `num2`, the result will be "num1 is greater", otherwise it will be "num2 is greater". The result is then stored in the variable `result` and printed to the console.

Ternary operations can be a useful tool when you need to make simple comparisons and assign values based on the result. They help in writing more concise and readable code.

#JavaScript #TernaryOperations