---
layout: post
title: "Hashing with Linear Probing Optimization (Double Hashing)"
description: " "
date: 2023-10-01
tags: [Tech, Hashing]
comments: true
share: true
---

Hashing is a widely used technique in computer science to efficiently store and retrieve data. It allows for constant time complexity for most operations, making it ideal for tasks such as searching, inserting, and deleting elements from a data structure. One common method of implementing a hash table is through linear probing.

Linear probing is a technique where collisions are resolved by searching for the next available slot in the hash table. However, linear probing can lead to clusters of occupied slots, causing degradation in performance. To mitigate this issue, a technique called **Double Hashing** can be used.

Double hashing is a variation of linear probing where a second hash function is used to calculate the step size when searching for an available slot. This helps to distribute the elements more evenly across the hash table, reducing the likelihood of clustering.

## How Double Hashing Works

1. Generate two hash functions:
   - `hash1(key)` calculates the initial hash value for the key.
   - `hash2(key)` calculates the step size for probing.

2. Compute the initial hash value using `hash1(key)`.

3. If the slot at the computed hash value is empty, store the element there. If not, perform the following steps:

4. Calculate the step size using `hash2(key)`.

5. Increment the hash value by the step size until an empty slot is found.

6. Store the element at the vacant slot.

## Example Code - Double Hashing in Python

```python
class DoubleHashingHashTable:
    def __init__(self, size):
        self.size = size
        self.hash_table = [None] * size

    def hash1(self, key):
        return key % self.size

    def hash2(self, key):
        # Ensure that the step size is always greater than 0.
        return 1 + (key % (self.size - 1))

    def insert(self, key, value):
        hash_value = self.hash1(key)
        if self.hash_table[hash_value] is None:
            self.hash_table[hash_value] = (key, value)
        else:
            step = self.hash2(key)
            while self.hash_table[hash_value] is not None:
                hash_value = (hash_value + step) % self.size
            self.hash_table[hash_value] = (key, value)

    def search(self, key):
        hash_value = self.hash1(key)
        if self.hash_table[hash_value] is not None and self.hash_table[hash_value][0] == key:
            return self.hash_table[hash_value][1]
        step = self.hash2(key)
        while self.hash_table[hash_value] is not None:
            if self.hash_table[hash_value][0] == key:
                return self.hash_table[hash_value][1]
            hash_value = (hash_value + step) % self.size
        return None

# Example usage:
hash_table = DoubleHashingHashTable(10)
hash_table.insert(5, "apple")
hash_table.insert(15, "orange")
hash_table.insert(25, "banana")

print(hash_table.search(15))  # Output: "orange"
```

Double hashing optimization can significantly improve the performance of hash tables by reducing the likelihood of clustering. It helps to evenly distribute the elements, resulting in faster retrieval of data. Consider implementing double hashing whenever linear probing is used to handle collisions in a hash table.

#Tech #Hashing #DataStructures