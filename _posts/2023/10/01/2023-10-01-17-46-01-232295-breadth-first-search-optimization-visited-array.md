---
layout: post
title: "Breadth First Search Optimization (Visited Array)"
description: " "
date: 2023-10-01
tags: [optimization]
comments: true
share: true
---

When it comes to graph traversals, Breadth First Search (BFS) is a widely used algorithm. It explores all the vertices of a graph in breadth-first order, i.e., it visits all the vertices at the same level before moving on to the next level. This algorithm is particularly useful when finding the shortest paths in unweighted graphs.

While the basic implementation of BFS is quite straightforward, there is one optimization technique that can significantly improve its performance - the use of a visited array. In this article, we will explore how the visited array optimization can enhance the efficiency of BFS.

## The Basic BFS Algorithm ##

Before we dive into the optimization technique, let's quickly recap the basic BFS algorithm. Here's a simple implementation in Python:

```python
from collections import deque

def bfs(graph, start):
    queue = deque()
    visited = set()

    queue.append(start)
    visited.add(start)

    while queue:
        vertex = queue.popleft()
        print(vertex)  # Process the vertex here

        for adjacent in graph[vertex]:
            if adjacent not in visited:
                queue.append(adjacent)
                visited.add(adjacent)
```

The above code implements the standard BFS algorithm using a queue to store the vertices and a visited set to keep track of the visited vertices. The algorithm iteratively dequeues a vertex, processes it, and enqueues its adjacent vertices if they haven't been visited before.

## The Visited Array Optimization ##

The visited array optimization replaces the visited set with a visited array, which can significantly improve the performance of the BFS algorithm. Instead of using a set to check whether a vertex has been visited, we use a boolean array to store the visited information.

Here's an optimized version of the BFS algorithm with the visited array:

```python
def bfs(graph, start):
    queue = deque()
    visited = [False] * len(graph)

    queue.append(start)
    visited[start] = True

    while queue:
        vertex = queue.popleft()
        print(vertex)  # Process the vertex here

        for adjacent in graph[vertex]:
            if not visited[adjacent]:
                queue.append(adjacent)
                visited[adjacent] = True
```

In this optimized version, we initialize the visited array with `False` values representing unvisited vertices. When visiting a vertex, instead of adding it to the visited set, we mark the corresponding element in the visited array as `True`. This change eliminates the overhead of manipulating the set and results in faster lookups.

## Summary ##

The visited array optimization is a simple but effective technique to enhance the performance of Breadth First Search. By replacing the visited set with a visited array, we can achieve significant speed improvements in terms of storage and lookup operations. This optimization is particularly useful when dealing with large graphs or performance-critical applications.

Feel free to experiment with the optimized BFS algorithm in your own code and measure its performance improvements. Remember to always consider the specific requirements of your application and choose the most appropriate algorithm and optimizations accordingly.

#optimization #BFS