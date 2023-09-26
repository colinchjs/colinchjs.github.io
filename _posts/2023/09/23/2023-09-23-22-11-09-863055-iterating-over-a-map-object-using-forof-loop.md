---
layout: post
title: "Iterating over a Map object using for...of loop"
description: " "
date: 2023-09-23
tags: [MapObject]
comments: true
share: true
---

Hashtags: #JavaScript #MapObject

---

In JavaScript, the `Map` object is a built-in data structure that allows you to store key-value pairs. One common task you may encounter is iterating over the `Map` object to access and manipulate its values. In this blog post, we'll explore how to iterate over a `Map` object using the `for...of` loop.

The `for...of` loop is a convenient way to iterate over iterable objects in JavaScript, including `Map` objects. It provides a clean and concise syntax for looping through the elements of an iterable, such as an array, set, or `Map`.

To demonstrate this, let's assume we have a `Map` object that represents a list of names and ages:

```javascript
let persons = new Map();
persons.set("John", 25);
persons.set("Emily", 30);
persons.set("Michael", 35);
```

To iterate over the `persons` `Map`, we can use the `for...of` loop as follows:

```javascript
for (let [name, age] of persons) {
    console.log(`${name} is ${age} years old`);
}
```

In the above code, we're using destructuring to extract the `name` and `age` values from each entry in the `persons` `Map`. We then log the name and age together in a sentence.

When executing the code, the output will be:

```
John is 25 years old
Emily is 30 years old
Michael is 35 years old
```

It's important to note that the `for...of` loop iterates over the entries of the `Map` object in the order of insertion. This ensures that the elements are processed in the order they were added to the `Map`.

Additionally, unlike the `for...in` loop, the `for...of` loop only iterates over the values and does not include any properties inherited from the object's prototype chain.

In conclusion, the `for...of` loop provides a concise and efficient way to iterate over iterable objects, including `Map` objects. By leveraging this looping mechanism, you can easily access and manipulate the key-value pairs stored in a `Map`. Happy coding!

---

Hashtags: #JavaScript #MapObject