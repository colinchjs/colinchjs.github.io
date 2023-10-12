---
layout: post
title: "Can you provide an example of a simple ternary operation in JavaScript?"
description: " "
date: 2023-10-12
tags: []
comments: true
share: true
---

```javascript
const age = 18;
const canVote = (age >= 18) ? "Yes" : "No";

console.log(`Can vote? ${canVote}`);
```

In this example, we have a variable `age` initialized with a value of 18. The ternary operator is used to assign the value of `canVote` based on the value of `age`. If `age` is greater than or equal to 18, the value of `canVote` will be `"Yes"`, otherwise it will be `"No"`. Finally, we log the value of `canVote` to the console.

This is a concise way to write a simple conditional statement. It can be especially useful when you need to quickly assign a value based on a condition without writing a full if-else statement.

#javascript #ternaryoperation