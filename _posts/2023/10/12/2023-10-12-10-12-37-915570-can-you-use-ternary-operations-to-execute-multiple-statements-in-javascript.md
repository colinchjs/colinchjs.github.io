---
layout: post
title: "Can you use ternary operations to execute multiple statements in JavaScript?"
description: " "
date: 2023-10-12
tags: []
comments: true
share: true
---

The syntax of the ternary operator is as follows:

```javascript
condition ? expression1 : expression2;
```

The condition is evaluated first. If the condition is true, expression1 will be executed. If the condition is false, expression2 will be executed.

To execute multiple statements, you can use multiple expressions separated by a comma within each expression. For example:

```javascript
condition ? (expression1, expression2, expression3) : expression4;
```

In this example, if the condition is true, expression1, expression2, and expression3 will be executed. If the condition is false, expression4 will be executed.

Here's an example that demonstrates the usage of ternary operations to execute multiple statements in JavaScript:

```javascript
const num = 5;

num > 0 ? (
  console.log("Positive number."),
  console.log("This is an example of multiple statements.")
) : (
  console.log("Negative number.")
);
```

In this example, if the value of the `num` variable is greater than 0, it will print "Positive number" and "This is an example of multiple statements". Otherwise, it will print "Negative number".

Using ternary operations to execute multiple statements can help simplify your code and make it more concise. However, it's important to use them judiciously and ensure that the code remains readable and maintainable.

#JavaScript #TernaryOperator