---
layout: post
title: "Sorting a Map object by keys"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

1. Convert the `Map` object to a `List` of `Map.Entry` objects.
2. Sort the `List` using a custom comparator that compares the keys of the `Map.Entry` objects.
3. Create a new `Map` object and populate it with the sorted entries from the `List`.

Here's an example implementation in Java:

```java
import java.util.*;

public class SortMapByKeyExample {
    public static void main(String[] args) {
        // Create a Map object
        Map<Integer, String> map = new HashMap<>();
        map.put(5, "Apple");
        map.put(3, "Banana");
        map.put(1, "Orange");
        map.put(4, "Mango");
        map.put(2, "Grape");

        // Convert Map to List of Map.Entry objects
        List<Map.Entry<Integer, String>> entryList = new ArrayList<>(map.entrySet());

        // Sort the List by keys using a custom comparator
        Collections.sort(entryList, new Comparator<Map.Entry<Integer, String>>() {
            @Override
            public int compare(Map.Entry<Integer, String> entry1, Map.Entry<Integer, String> entry2) {
                return entry1.getKey().compareTo(entry2.getKey());
            }
        });

        // Create a new LinkedHashMap to store the sorted entries
        Map<Integer, String> sortedMap = new LinkedHashMap<>();
        for (Map.Entry<Integer, String> entry : entryList) {
            sortedMap.put(entry.getKey(), entry.getValue());
        }

        // Print the sorted Map
        for (Map.Entry<Integer, String> entry : sortedMap.entrySet()) {
            System.out.println(entry.getKey() + ": " + entry.getValue());
        }
    }
}
```

In this example, we create a `Map` object with integer keys and string values. We convert the `Map` to a `List` of `Map.Entry` objects and then use `Collections.sort()` to sort the list based on the keys. Finally, we create a new `LinkedHashMap` and populate it with the sorted entries. The resulting `sortedMap` contains the same key-value pairs as the original `map`, but with the keys sorted in ascending order.

By following these steps, you can easily sort a `Map` object by keys in various programming languages. This approach gives you control over the order of keys in the sorted `Map`, regardless of the default order of the `Map` implementation.