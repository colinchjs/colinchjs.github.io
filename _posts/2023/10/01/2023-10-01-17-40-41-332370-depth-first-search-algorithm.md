---
layout: post
title: "Depth First Search Algorithm"
description: " "
date: 2023-10-01
tags: [graphtraversal]
comments: true
share: true
---

Depth First Search (DFS) is a graph traversal algorithm that explores as far as possible along each branch before backtracking. It is widely used in various applications such as finding connected components, detecting cycles, and solving mazes.

## Implementation

Here is an example implementation of the Depth First Search algorithm in Python:

```python
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
        
    visited.add(start)
    print(start, end=" ")

    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
```

## Usage

To use this algorithm, you need to represent the graph as an adjacency list. An adjacency list is a data structure that stores the neighbors of each vertex in a graph.

Here's an example usage of the `dfs` function:

```python
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}

dfs(graph, 'A')
```

Output:
```
A B D E F C
```

## Complexity

The time complexity of the Depth First Search algorithm is O(V + E), where V is the number of vertices and E is the number of edges in the graph. The space complexity is O(V), where V is the number of vertices.

## Conclusion

The Depth First Search algorithm is a powerful graph traversal technique that can be applied to various problems. It helps in exploring all the vertices of a graph efficiently. Understanding this algorithm can be beneficial for solving graph-related problems in a structured and efficient manner.

#DFS-algorithm #graphtraversal