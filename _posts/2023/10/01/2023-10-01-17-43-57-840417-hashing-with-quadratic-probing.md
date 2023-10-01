---
layout: post
title: "Hashing with Quadratic Probing"
description: " "
date: 2023-10-01
tags: [hashing, quadraticprobing]
comments: true
share: true
---

Hashing is a widely used technique in computer programming to quickly retrieve data from a large collection of items. One common approach to handle collisions in hash tables is called quadratic probing. In this blog post, we will explore how quadratic probing works and its benefits in handling collisions efficiently.

## What is Quadratic Probing?

Quadratic probing is a collision resolution technique used in hash tables. It is an open-addressing method that handles collisions by finding the next available slot in the table using a quadratic function. When a collision occurs, instead of immediately placing the new item in the next available slot, quadratic probing uses a probing sequence to find the next suitable position.

## Probing Sequence

When a collision occurs at position `h`, quadratic probing calculates the next position to probe based on a quadratic function of the form `(h + i^2) % table_size`, where `i` is the number of iterations. The modulo operator ensures that the calculated position stays within the bounds of the hash table.

## Benefits of Quadratic Probing

Quadratic probing offers several advantages compared to other collision resolution techniques:

1. **Better distribution**: Quadratic probing reduces primary clustering, where consecutive collisions occur in the same sequence. This leads to a better distribution of items in the hash table, improving performance.
2. **Fewer collisions**: With quadratic probing, the likelihood of finding an empty slot increases as the probing sequence progresses. This reduces the number of collisions, resulting in faster retrieval times.
3. **No need for extra data structures**: Unlike chaining or double hashing, quadratic probing does not require additional data structures to store collided items. It utilizes the existing hash table and its open slots effectively.

## Example Implementation in Python

Here's an example implementation of a hash table using quadratic probing in Python:

```python
class HashTable:
    def __init__(self, size):
        self.size = size
        self.table = [None] * size

    def _hash(self, key):
        # calculate hash value
        return key % self.size

    def _probe(self, hash_value, i):
        # calculate probing sequence
        return (hash_value + i ** 2) % self.size

    def insert(self, key, value):
        hash_value = self._hash(key)
        i = 0
        while self.table[hash_value] is not None:
            i += 1
            hash_value = self._probe(hash_value, i)
        self.table[hash_value] = value

    def get(self, key):
        hash_value = self._hash(key)
        i = 0
        while self.table[hash_value] is not None:
            if self.table[hash_value][0] == key:
                return self.table[hash_value][1]
            i += 1
            hash_value = self._probe(hash_value, i)
        return None
```

## Conclusion

Quadratic probing is an effective method for resolving collisions in hash tables. Its probing sequence reduces primary clustering, resulting in a more balanced distribution of items. Additionally, it doesn't require any extra data structures and provides fast retrieval times. So, the next time you encounter a collision in a hash table, consider using quadratic probing to handle it efficiently.

#hashing #quadraticprobing