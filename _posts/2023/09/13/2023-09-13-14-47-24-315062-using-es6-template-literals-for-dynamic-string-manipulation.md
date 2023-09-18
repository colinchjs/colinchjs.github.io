---
layout: post
title: "Using ES6 Template Literals for Dynamic String Manipulation"
description: " "
date: 2023-09-13
tags: [template]
comments: true
share: true
---

In JavaScript, ES6 introduced a new feature called **Template Literals**, which provides an easy and flexible way to manipulate strings dynamically. With Template Literals, you can embed expressions and variables directly inside a string, making it simple and intuitive to create dynamic and complex strings.

## Syntax

Template Literals are defined using backticks (\`) instead of single or double quotes. Inside a Template Literal, you can embed placeholders, also known as template placeholders, by wrapping them in curly braces and preceding them with a dollar sign (`${expression}`).

Let's see an example to better understand the syntax:

```javascript
const name = "John";
const greeting = `Hello, ${name}!`;
console.log(greeting);
// Output: Hello, John!
```

In the above code snippet, the variable `name` is dynamically inserted inside the Template Literal using `${name}`. When `console.log(greeting)` is executed, it will output the string "Hello, John!".

## String Manipulation

Template Literals can be used to manipulate strings in various ways. They allow you to concatenate multiple strings, format numbers, perform calculations, and even nest template literals within each other.

### Concatenating Strings

```javascript
const firstName = "John";
const lastName = "Doe";
const fullName = `${firstName} ${lastName}`;
console.log(fullName);
// Output: John Doe
```

In the above example, the two variables `firstName` and `lastName` are concatenated using a space (" ") as a separator. The resulting string is stored in the `fullName` variable and printed to the console.

### Formatting Numbers

```javascript
const price = 9.99;
const formattedPrice = `The price is: $${price.toFixed(2)}`;
console.log(formattedPrice);
// Output: The price is: $9.99
```

In this example, the number stored in the `price` variable is formatted to have exactly two decimal places using the `toFixed()` method. It is then embedded inside the Template Literal along with the rest of the string.

### Performing Calculations

```javascript
const quantity = 5;
const pricePerUnit = 9.99;
const totalPrice = `Total price: $${(quantity * pricePerUnit).toFixed(2)}`;
console.log(totalPrice);
// Output: Total price: $49.95
```

In the above code snippet, the total price is calculated by multiplying the `quantity` variable with the `pricePerUnit` variable. The result is then embedded inside the Template Literal, resulting in a dynamically calculated total price.

### Nesting Template Literals

```javascript
const firstName = "John";
const lastName = "Doe";
const greeting = `Hello, ${`${firstName} ${lastName}`}!`;
console.log(greeting);
// Output: Hello, John Doe!
```

In this example, a Template Literal is nested within another Template Literal. The inner Template Literal concatenates the `firstName` and `lastName` variables, which are then dynamically inserted inside the outer Template Literal.

## Conclusion

ES6 Template Literals provide a powerful and concise way to manipulate strings dynamically in JavaScript. They offer flexibility and readability, making it easier to construct complex and dynamic strings. Being able to embed expressions and variables directly in the string simplifies code maintenance, as it eliminates the need for manual string concatenation.

So, the next time you need to dynamically manipulate strings in your JavaScript code, consider using Template Literals for a cleaner and more efficient solution.

**#javascript #es6 #template-literals**