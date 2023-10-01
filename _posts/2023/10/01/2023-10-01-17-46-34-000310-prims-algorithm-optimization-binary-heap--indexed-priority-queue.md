---
layout: post
title: "Prim's Algorithm Optimization (Binary Heap + Indexed Priority Queue)"
description: " "
date: 2023-10-01
tags: []
comments: true
share: true
---

In graph theory, Prim's algorithm is a popular algorithm used to find the minimum spanning tree for a weighted, undirected graph. The algorithm starts with an arbitrary vertex and repeatedly adds the cheapest edge that connects a vertex in the tree to a vertex outside the tree until all vertices are included in the tree.

However, the naive implementation of Prim's algorithm has a time complexity of O(V^2), where V is the number of vertices. This can be prohibitively slow for large graphs. 

To optimize Prim's algorithm, we can use a combination of a binary heap and an indexed priority queue. This optimization reduces the time complexity to O(E*log(V)), where E is the number of edges.

## Binary Heap

A binary heap is a data structure that allows efficient insertion and extraction of the minimum element in O(logn) time. It can be implemented using an array, where each node at index `i` has its left child at index `2i+1` and right child at index `2i+2`.

## Indexed Priority Queue

An indexed priority queue is a data structure that allows efficient insertion, deletion, and update of elements with associated priorities. It is implemented using a binary heap, where each element is associated with an index. This allows us to efficiently update the priorities of elements in the queue.

## Optimized Prim's Algorithm

The optimized Prim's algorithm involves the following steps:

1. Initialize an indexed priority queue with the first vertex as the source and all other vertices with a priority of positive infinity.
2. While the indexed priority queue is not empty, do the following:
    - Extract the minimum vertex `v` from the indexed priority queue.
    - Add `v` to the minimum spanning tree.
    - Update the priorities of all adjacent vertices `u` not yet in the minimum spanning tree. If the weight of the edge between `v` and `u` is less than `u`'s current priority, update the priority to the weight of the edge.
3. Return the minimum spanning tree.

## Example Code

```python
import heapq

def prim(graph, source):
    n = len(graph)
    mst = []
    visited = [False] * n
    pq = [(0, source)]
    heapq.heapify(pq)

    while pq:
        weight, v = heapq.heappop(pq)
        if visited[v]:
            continue
        visited[v] = True
        mst.append(v)

        for u, w in graph[v]:
            if not visited[u]:
                heapq.heappush(pq, (w, u))

    return mst

# Example usage
graph = [
    [(1, 2), (2, 3)],
    [(0, 2), (2, 4), (3, 5)],
    [(0, 3), (1, 4), (3, 6)],
    [(1, 5), (2, 6)]
]

minimum_spanning_tree = prim(graph, 0)
print(minimum_spanning_tree)
```

In the example code above, we define a function `prim` which takes a weighted graph in the form of an adjacency list and a source vertex. The function returns the minimum spanning tree of the input graph starting from the source vertex.

We use an indexed priority queue implemented using a binary heap to efficiently extract the minimum vertex and update priorities. The function initializes the priority queue with the source vertex and continues adding vertices to the minimum spanning tree until all vertices are included.

By using the optimized version of Prim's algorithm, we can significantly reduce the computational complexity and solve larger graph problems more efficiently.