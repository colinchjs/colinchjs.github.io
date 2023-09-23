---
layout: post
title: "Adding key-value pairs to a Map object"
description: " "
date: 2023-09-23
tags: [KeyvaluePairs, MapObject]
comments: true
share: true
---

To add key-value pairs to a Map object, you can use the `set()` method. This method takes two parameters: the key and the value.

Here is an example in Java:

```java
import java.util.HashMap;
import java.util.Map;

public class MapExample {
    public static void main(String[] args) {
        // Create a new Map object
        Map<String, Integer> map = new HashMap<>();

        // Add key-value pairs to the map
        map.put("apple", 10);
        map.put("banana", 20);
        map.put("orange", 15);

        // Print the map
        System.out.println(map);
    }
}
```

In the above example, we first create a new `HashMap` object named `map`. We then use the `put()` method to add key-value pairs to the map. Finally, we print the map to verify the added key-value pairs.

Here is an example in JavaScript:

```javascript
// Create a new Map object
let map = new Map();

// Add key-value pairs to the map
map.set("apple", 10);
map.set("banana", 20);
map.set("orange", 15);

// Print the map
console.log(map);
```

In JavaScript, we create a new `Map` object named `map`. We then use the `set()` method to add key-value pairs to the map. Finally, we use `console.log()` to print the map.

Key-value pairs can be added to a Map object using the `set()` method in both Java and JavaScript. This allows you to easily store and retrieve data based on their associated keys.

#KeyvaluePairs #MapObject