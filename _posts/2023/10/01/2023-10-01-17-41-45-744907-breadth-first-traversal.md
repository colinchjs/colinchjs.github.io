---
layout: post
title: "Breadth First Traversal"
description: " "
date: 2023-10-01
tags: [graph, traversal]
comments: true
share: true
---

Breadth First Traversal (BFT) is a graph traversal algorithm that explores all the vertices of a graph in breadth-first order, i.e., it visits all the vertices at the same level before moving to the next level.

## How BFT Works

The algorithm starts from a specified vertex, called the **source vertex**, and visits all its neighbors before moving on to their neighbors. This process continues until all the vertices in the graph have been visited.

BFT makes use of a **queue** data structure to keep track of visited vertices and to determine which vertices to visit next. Initially, the source vertex is added to the queue. While the queue is not empty, we remove a vertex, visit it, mark it as visited, and then add all its unvisited neighbors to the queue.

## Example Implementation in Python

Here's an example implementation of Breadth First Traversal in Python:

```python
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.adj = [[] for _ in range(vertices)]

    def add_edge(self, u, v):
        self.adj[u].append(v)

    def breadth_first_traversal(self, source):
        visited = [False] * self.V
        queue = []

        visited[source] = True
        queue.append(source)

        while queue:
            vertex = queue.pop(0)
            print(vertex, end=" ")

            for neighbor in self.adj[vertex]:
                if not visited[neighbor]:
                    visited[neighbor] = True
                    queue.append(neighbor)
```

In this example, we define a `Graph` class that represents the graph using an adjacency list. The `add_edge` method is used to add edges between vertices. The `breadth_first_traversal` method implements the BFT algorithm.

## Conclusion

Breadth First Traversal is a fundamental graph traversal algorithm that can be applied to explore all vertices of a graph in breadth-first order. It is commonly used in various applications, such as finding the shortest path and discovering connected components in a graph.

#graph #traversal