---
layout: post
title: "Accessing values from a Map object using keys"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

**JavaScript:**

```javascript
const myMap = new Map();

myMap.set('key1', 'value1');
myMap.set('key2', 'value2');
myMap.set('key3', 'value3');

console.log(myMap.get('key2')); // Output: value2
```

**Python:**

```python
my_map = {'key1': 'value1', 'key2': 'value2', 'key3': 'value3'}

print(my_map['key2'])  # Output: value2
```

**Java:**

```java
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        Map<String, String> myMap = new HashMap<>();

        myMap.put("key1", "value1");
        myMap.put("key2", "value2");
        myMap.put("key3", "value3");

        System.out.println(myMap.get("key2")); // Output: value2
    }
}
```

**C#:**

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        Dictionary<string, string> myMap = new Dictionary<string, string>();

        myMap.Add("key1", "value1");
        myMap.Add("key2", "value2");
        myMap.Add("key3", "value3");

        Console.WriteLine(myMap["key2"]); // Output: value2
    }
}
```

**Ruby:**

```ruby
my_map = { 'key1' => 'value1', 'key2' => 'value2', 'key3' => 'value3' }

puts my_map['key2'] # Output: value2
```

**Swift:**

```swift
var myMap = [String: String]()

myMap["key1"] = "value1"
myMap["key2"] = "value2"
myMap["key3"] = "value3"

print(myMap["key2"]) // Output: Optional("value2")
```

Regardless of the programming language you're using, remember that keys are case-sensitive. So make sure the key you're accessing matches the case and spelling used when it was added to the `Map`.