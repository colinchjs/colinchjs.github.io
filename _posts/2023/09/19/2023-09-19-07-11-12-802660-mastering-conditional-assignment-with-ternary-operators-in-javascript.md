---
layout: post
title: "Mastering conditional assignment with ternary operators in JavaScript"
description: " "
date: 2023-09-19
tags: [javascript, conditionalassignment]
comments: true
share: true
---

JavaScript provides several ways to conditionally assign values to variables. One powerful technique is using the *ternary operator*, also known as the *conditional operator*. This operator allows you to write concise and readable code while performing conditional assignments.

The syntax of the ternary operator is:

```javascript
condition ? valueIfTrue : valueIfFalse;
```

Let's explore some practical examples to understand how to master this technique.

## Example 1: Assigning a value based on a condition

Suppose we have a variable `age` and we want to assign a message based on whether `age` is greater than or equal to 18. Instead of using an if-else statement, we can use the ternary operator to achieve this in a single line:

```javascript
const message = age >= 18 ? "You are an adult" : "You are a minor";
```

In the above code, if `age` is greater than or equal to 18, the value `"You are an adult"` is assigned to `message`. Otherwise, the value `"You are a minor"` is assigned.

## Example 2: Assigning a value dynamically

We can also use the ternary operator to assign values dynamically based on conditions. Let's say we want to assign the value of `x` based on whether `condition` is true or false:

```javascript
const x = condition ? valueIfTrue : valueIfFalse;
```

In this example, if `condition` is true, the `valueIfTrue` is assigned to `x`. Otherwise, `valueIfFalse` is assigned.

## Example 3: Returning a value from a function

The ternary operator is not only useful for assigning values but also for returning different values from a function based on certain conditions. Consider the following example:

```javascript
function getDiscountPrice(isPremiumUser) {
  return isPremiumUser ? 0.2 : 0.1;
}
```

In this case, if `isPremiumUser` is true, the function returns `0.2`, indicating a 20% discount. Otherwise, it returns `0.1`, indicating a 10% discount.

## Conclusion

Mastering the conditional assignment with ternary operators can significantly streamline your code and make it more readable. It allows you to perform conditional assignments, dynamically assign values, and return different values from functions based on conditions. By utilizing this powerful technique, you can write cleaner and more efficient JavaScript code.

#javascript #conditionalassignment