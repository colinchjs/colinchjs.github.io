---
layout: post
title: "Using Map object to implement a LRU (Least Recently Used) cache"
description: " "
date: 2023-09-23
tags: [programming, caching]
comments: true
share: true
---

LRU (Least Recently Used) cache is a commonly used cache eviction policy, where the least recently used items are removed from the cache when it reaches its capacity. In this blog post, we will explore how to implement an LRU cache using the `Map` object in JavaScript.

## Understanding the LRU Cache

An LRU cache has a fixed size capacity and stores key-value pairs. When a key-value pair is accessed, it becomes the most recently used item, moving it to the front of the cache. When the capacity is reached and a new item needs to be added, the least recently used item (the one at the end of the cache) is evicted.

The `Map` object in JavaScript provides a useful data structure to implement an LRU cache. It allows us to store key-value pairs and provides O(1) time complexity for accessing, inserting, and deleting elements. Additionally, the insertion order of elements is maintained in a `Map` object, which makes it easy to track the least recently used item.

## Implementing the LRU Cache

Here's an example implementation of an LRU cache using the `Map` object:

```javascript
class LRUCache {
  constructor(capacity) {
    this.capacity = capacity;
    this.cache = new Map();
  }

  get(key) {
    if (this.cache.has(key)) {
      const value = this.cache.get(key);
      this.cache.delete(key);
      this.cache.set(key, value);
      return value;
    }
    return -1; // Return -1 if the key is not in the cache
  }

  put(key, value) {
    if (this.cache.has(key)) {
      this.cache.delete(key);
    } else if (this.cache.size >= this.capacity) {
      // If the cache is full, remove the least recently used item
      const lruKey = this.cache.keys().next().value;
      this.cache.delete(lruKey);
    }
    this.cache.set(key, value);
  }
}
```

In this implementation, we use a `Map` object called `cache` to store the key-value pairs. The `get` method checks if the key is present in the cache. If it is, we delete the key-value pair from the cache and immediately set it again, which moves it to the front of the cache. If the key is not present, we return -1.

The `put` method first checks if the key already exists in the cache. If it does, we delete it to maintain the order of the items. If the cache is full, we remove the least recently used item by retrieving the first key using the `keys().next().value` method. Finally, we add the new key-value pair to the cache.

## Conclusion

Implementing an LRU cache using the `Map` object in JavaScript provides an efficient way to manage key-value pairs with a fixed capacity. The `Map` object's built-in data structure and methods simplify the implementation, allowing for efficient access, insertion, and deletion of items. Using an LRU cache can significantly improve the performance of applications that involve caching frequently accessed data.

#programming #caching