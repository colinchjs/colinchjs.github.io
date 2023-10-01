---
layout: post
title: "Hashing with Linear Probing"
description: " "
date: 2023-10-01
tags: [hashing, linearprobing]
comments: true
share: true
---

Hashing is a widely used technique in computer science to quickly locate data in a large collection. Linear probing is a method of resolving collisions in hash tables, where multiple keys are mapped to the same index.

## Understanding Hashing

Hashing involves mapping a given input, such as a string or an object, to a fixed-size numerical value called a hash code. The hash code is then used as an index to store the data in an array, known as the hash table.

## Collision Resolution with Linear Probing

In the case where two or more keys generate the same hash code and try to occupy the same index in the hash table, collision occurs. Linear probing is a simple strategy to resolve collisions by searching for the next available slot, usually the next consecutive index, to store the key.

Here's an example to illustrate the process of hashing with linear probing:

```python
class HashTable:
    def __init__(self, size):
        self.size = size
        self.keys = [None] * self.size
        self.values = [None] * self.size
    
    def hash(self, key):
        return hash(key) % self.size
    
    def insert(self, key, value):
        hash_value = self.hash(key)
        if self.keys[hash_value] is None:
            self.keys[hash_value] = key
            self.values[hash_value] = value
        else:
            index = (hash_value + 1) % self.size
            while self.keys[index] is not None:
                index = (index + 1) % self.size
            self.keys[index] = key
            self.values[index] = value
    
    def get(self, key):
        hash_value = self.hash(key)
        index = hash_value
        while self.keys[index] is not None:
            if self.keys[index] == key:
                return self.values[index]
            index = (index + 1) % self.size
        return None
```

In this example, we create a `HashTable` class that uses linear probing to handle collisions. The `hash` method calculates the hash code of the key, `insert` checks if the slot is occupied, and if not, stores the key and value at the calculated index. If the slot is occupied, it linearly searches for the next available slot, wrapping around to the start of the table if necessary. The `get` method searches for a given key using the same linear probing logic.

## Pros and Cons of Linear Probing

### Pros:
- Simplicity: The logic of linear probing is relatively easy to understand and implement.
- Space Efficiency: Use only a single extra array for values, resulting in less memory consumption compared to other collision resolution methods.

### Cons:
- Poor Performance in High Load: As the hash table fills up, the number of collisions increases, making linear probing slower.
- Clustering: Linear probing can lead to clustering, where keys that map to the same index tend to cluster together, resulting in poor performance.

## Conclusion

Linear probing is a simple and space-efficient solution for collision resolution in hash tables. However, its performance can degrade in scenarios with high load and clustering. Consider the characteristics of your data and the expected usage patterns when deciding whether to use linear probing or other collision resolution techniques. #hashing #linearprobing