---
layout: post
title: "Rest Parameters in JavaScript Functions"
description: " "
date: 2023-09-20
tags: [Functions]
comments: true
share: true
---

To define rest parameters, we simply prefix the parameter name with three dots (`...`). This tells JavaScript that any extra arguments passed to the function should be collected into an array.

Here's an example of a function that uses rest parameters to calculate the sum of multiple numbers:

```javascript
function sum(...numbers) {
  let result = 0;

  for (let i = 0; i < numbers.length; i++) {
    result += numbers[i];
  }

  return result;
}

console.log(sum(1, 2, 3, 4, 5)); // Output: 15
console.log(sum(10, 20)); // Output: 30
```

In the above code, the `sum` function accepts any number of arguments and collects them into the `numbers` array using rest parameters. We can then loop through the array and calculate the sum of all the numbers.

Rest parameters can also be used with other named parameters in a function. However, it's important to note that rest parameters must be the last parameter in the function's parameter list.

```javascript
function printInfo(name, age, ...hobbies) {
  console.log(`Name: ${name}`);
  console.log(`Age: ${age}`);
  console.log(`Hobbies: ${hobbies.join(", ")}`);
}

printInfo("John", 25, "Reading", "Gardening", "Cycling");
```

In the above example, the `printInfo` function accepts `name` and `age` as regular parameters, and the rest parameter `hobbies` will collect any remaining arguments into an array. We can then use the `join` method to concatenate the hobbies array into a string, separated by commas.

Rest parameters in JavaScript functions provide a flexible and concise way to handle variable numbers of arguments, making our code more adaptable and readable. So, the next time you encounter a situation where you need to handle multiple arguments in a function, consider using rest parameters to simplify your code.

#JavaScript #Functions