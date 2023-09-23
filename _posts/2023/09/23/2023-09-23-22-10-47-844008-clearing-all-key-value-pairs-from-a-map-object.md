---
layout: post
title: "Clearing all key-value pairs from a Map object"
description: " "
date: 2023-09-23
tags: [JavaScript, DataStructure]
comments: true
share: true
---

# Method 1: Using the `clear` method

The `Map` object in JavaScript provides a built-in `clear` method that removes all key-value pairs from the map. Here's how you can use this method:

```javascript
// Create a new Map object
let myMap = new Map();

// Add some key-value pairs
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

// Clear the Map object
myMap.clear();

console.log(myMap.size); // Output: 0
```

In the above code, we first create a new Map object `myMap` and add some key-value pairs. We then call the `clear` method on the map, which removes all the key-value pairs. Finally, we print the size of the map, which should be 0 indicating that all the key-value pairs have been cleared.

# Method 2: Reassigning a new Map object

Another approach to clear a Map object is by reassigning it with a new Map object. Here's an example:

```javascript
// Create a new Map object
let myMap = new Map();

// Add some key-value pairs
myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

// Clear the Map object by reassigning with a new Map object
myMap = new Map();

console.log(myMap.size); // Output: 0
```

In the above code, we follow similar steps as before, but instead of calling the `clear` method, we assign a new `Map` object to the variable `myMap`. This effectively clears the original Map object and creates a fresh one with no key-value pairs.

**Conclusion:**
In JavaScript, there are multiple ways to clear the key-value pairs from a Map object. You can use the `clear` method provided by the Map object or reassign the Map object with a new instance. Both methods achieve the same result of clearing the Map. Choose the method that best fits your code logic and requirements.

# #JavaScript #Map #DataStructure