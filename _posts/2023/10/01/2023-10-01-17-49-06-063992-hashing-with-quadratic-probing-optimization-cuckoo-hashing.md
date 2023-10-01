---
layout: post
title: "Hashing with Quadratic Probing Optimization (Cuckoo Hashing)"
description: " "
date: 2023-10-01
tags: [hashing, optimization]
comments: true
share: true
---

Hashing is a fundamental concept in computer science and is widely used in various applications to quickly retrieve data based on a key. Quadratic Probing is a technique used to resolve collisions that occur in hash tables, where multiple keys are hashed to the same index. In this blog post, we will explore how Quadratic Probing can be optimized using Cuckoo Hashing, a technique that provides a high load factor and efficient lookup times.

## Understanding Quadratic Probing

Quadratic Probing is a collision resolution technique where, when a collision occurs, the next available slot is found by adding an incrementing quadratic value to the original hash index. The quadratic value is typically the square of an integer, starting from 1.

```python
def quadratic_probing(hash_table, key):
    index = hash_function(key)  # Hash the key to get the initial index
    i = 1
    while hash_table[index] is not None and hash_table[index] != key:
        index = (index + i * i) % table_size
        i += 1
    return index
```

In the above code snippet, we iterate through the hash table starting from the initial index and calculate the next index using the quadratic formula `(index + i * i) % table_size`. We increment the quadratic value `i` until we find an empty slot or the key we are searching for. The `% table_size` operation ensures that we wrap around to the beginning of the table if we reach the end.

While Quadratic Probing provides a simple way to resolve collisions, it suffers from a problem known as clustering. Clustering occurs when keys that map to the same index keep colliding, leading to longer and longer probe sequences, impacting the performance of the hash table.

## Optimizing with Cuckoo Hashing

Cuckoo Hashing is a technique that aims to reduce clustering and achieve a more efficient lookup time by employing two hash functions and multiple hash tables. Instead of storing only one key at each index, Cuckoo Hashing uses two hash functions to determine two possible indexes for a key.

```python
def cuckoo_hashing(hash_table, key):
    index1 = hash_function1(key)  # Hash with first hash function
    index2 = hash_function2(key)  # Hash with second hash function
    
    if hash_table[index1] is None:
        hash_table[index1] = key
        return index1
    elif hash_table[index2] is None:
        hash_table[index2] = key
        return index2
    else:
        evicted_key = hash_table[index2]
        hash_table[index2] = key
        
        # Recursively evict keys from the other hash table
        cuckoo_hashing(hash_table, evicted_key)
        return index2
```

In the above code snippet, we first hash the key using two hash functions `hash_function1` and `hash_function2`. We check the first index, and if it's empty, we store the key there. If not, we check the second index, and if it's empty, we store the key there. If both indexes are occupied, we evict one of the keys and recursively call `cuckoo_hashing` to find a new place for the evicted key.

By utilizing two hash functions and multiple hash tables, Cuckoo Hashing mitigates clustering and achieves a more efficient lookup time. However, it requires additional space and may involve a series of rehashing operations if there is no suitable place for a key.

# Conclusion

Hashing with Quadratic Probing can be optimized using Cuckoo Hashing, a technique that provides a high load factor and efficient lookup times. While Quadratic Probing suffers from clustering, Cuckoo Hashing avoids it by employing two hash functions and multiple hash tables. By understanding the fundamentals of Quadratic Probing and exploring the optimization provided by Cuckoo Hashing, developers can implement efficient and reliable hash tables in their applications.

#hashing #optimization