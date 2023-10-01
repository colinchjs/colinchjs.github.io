---
layout: post
title: "Breadth First Search Algorithm"
description: " "
date: 2023-10-01
tags: [GraphTraversal]
comments: true
share: true
---

Breadth First Search (BFS) is a graph traversal algorithm that explores all the vertices of a graph level by level. It starts at a given source vertex and visits all of its neighboring vertices before moving on to the next level.

## How BFS Works

1. Create an empty queue and a boolean array to mark visited vertices.
2. Enqueue the source vertex and mark it as visited.
3. Dequeue a vertex from the queue and visit it.
4. Enqueue all its neighboring unvisited vertices and mark them as visited.
5. Repeat steps 3 and 4 until the queue becomes empty.

## Implementation in Python

```python
from collections import deque

def bfs(graph, start_vertex):
    visited = [False] * len(graph)
    queue = deque()

    queue.append(start_vertex)
    visited[start_vertex] = True

    while queue:
        current_vertex = queue.popleft()
        print(current_vertex)

        for neighbor in graph[current_vertex]:
            if not visited[neighbor]:
                queue.append(neighbor)
                visited[neighbor] = True
```

In the above implementation, `graph` is a list of lists representing the adjacency list representation of the graph. `start_vertex` is the vertex from where the BFS traversal should start.

The `bfs` function uses a queue (`deque` from the `collections` module) to keep track of vertices to visit. The `visited` array is used to mark vertices as visited to avoid revisiting them.

## Time and Space Complexity

The time complexity of the Breadth First Search algorithm is O(V + E), where V is the number of vertices and E is the number of edges in the graph. In the worst-case scenario, BFS visits all the vertices and edges.

The space complexity is O(V), as we need to maintain a queue and a visited array of size V.

#BFS #GraphTraversal