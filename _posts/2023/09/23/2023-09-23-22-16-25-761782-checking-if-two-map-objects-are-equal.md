---
layout: post
title: "Checking if two Map objects are equal"
description: " "
date: 2023-09-23
tags: [java]
comments: true
share: true
---

## Approach 1: Using `equals()` method

The `Map` interface provides an `equals()` method that can be used to compare two maps for equality. This method checks if the specified object is also a `Map` object and contains the same key-value mappings.

Example code:

```java
Map<String, Integer> map1 = new HashMap<>();
map1.put("one", 1);
map1.put("two", 2);
map1.put("three", 3);

Map<String, Integer> map2 = new HashMap<>();
map2.put("one", 1);
map2.put("two", 2);
map2.put("three", 3);

boolean areEqual = map1.equals(map2);
System.out.println("Are the maps equal? " + areEqual);
```

Output:

```
Are the maps equal? true
```

## Approach 2: Manually comparing key-value pairs

If you want to check for equality with more control and customization, you can manually compare the key-value pairs of the two `Map` objects.

Example code:

```java
Map<String, Integer> map1 = new HashMap<>();
map1.put("one", 1);
map1.put("two", 2);
map1.put("three", 3);

Map<String, Integer> map2 = new HashMap<>();
map2.put("one", 1);
map2.put("two", 22); // Different value for 'two' key
map2.put("three", 3);

boolean areEqual = true;

if (map1.size() != map2.size()) {
    areEqual = false;
} else {
    for (Map.Entry<String, Integer> entry : map1.entrySet()) {
        String key = entry.getKey();
        Integer value1 = entry.getValue();
        Integer value2 = map2.get(key);
        if (!value1.equals(value2)) {
            areEqual = false;
            break;
        }
    }
}

System.out.println("Are the maps equal? " + areEqual);
```

Output:

```
Are the maps equal? false
```

By comparing the key-value pairs one by one, you have finer control over the equality comparison. This approach allows you to define additional conditions or rules for determining the equality of `Map` objects.

In conclusion, depending on your requirements, you can either use the `equals()` method provided by the `Map` interface or perform a manual comparison of the key-value pairs to check if two `Map` objects are equal. The choice between these approaches depends on factors such as the desired level of control, customization, and performance. #java #map