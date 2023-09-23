---
layout: post
title: "Checking if a Map object contains a specific key"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

```java
// Create a HashMap
Map<String, Integer> map = new HashMap<>();

// Add some key-value pairs
map.put("one", 1);
map.put("two", 2);
map.put("three", 3);

// Check if the map contains a specific key
boolean containsKey = map.containsKey("two");
System.out.println("Contains key 'two': " + containsKey);

containsKey = map.containsKey("four");
System.out.println("Contains key 'four': " + containsKey);
```

Output:

```
Contains key 'two': true
Contains key 'four': false
```

In this example, we create a `Map` object called `map` and populate it with some key-value pairs. Then, we use the `containsKey()` method to check if the map contains the keys "two" and "four". The results are printed to the console.

Remember to replace `String` and `Integer` with the actual types used in your `Map` object.