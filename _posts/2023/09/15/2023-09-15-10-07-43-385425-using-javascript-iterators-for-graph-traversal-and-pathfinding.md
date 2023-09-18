---
layout: post
title: "Using JavaScript iterators for graph traversal and pathfinding"
description: " "
date: 2023-09-15
tags: [graph, pathfinding, traversal]
comments: true
share: true
---

Graphs are a fundamental data structure used in various fields, including computer science and network analysis. Traversal and pathfinding algorithms are commonly used to explore and find optimal paths within these graphs. In this blog post, we will explore how we can leverage JavaScript iterators to implement efficient graph traversal and pathfinding algorithms.

## What are JavaScript Iterators?

JavaScript iterators are objects that provide a standardized way to iterate over and traverse collections or structures. They allow you to define a custom iteration behavior for an object, enabling you to iterate through its elements using `for...of` loops or the `next()` method.

## Representing a Graph in JavaScript

Before diving into traversal and pathfinding, let's briefly discuss how we can represent a graph in JavaScript. There are several ways to represent graphs, but one commonly used approach is an adjacency list. In this representation, each vertex of the graph is associated with a list of its neighboring vertices.

```javascript
class Graph {
  constructor() {
    this.vertices = new Map();
  }

  addVertex(vertex) {
    this.vertices.set(vertex, []);
  }

  addEdge(vertex1, vertex2) {
    this.vertices.get(vertex1).push(vertex2);
    this.vertices.get(vertex2).push(vertex1);
  }

  getNeighbors(vertex) {
    return this.vertices.get(vertex);
  }
}

const graph = new Graph();

graph.addVertex(1);
graph.addVertex(2);
graph.addVertex(3);

graph.addEdge(1, 2);
graph.addEdge(2, 3);
```

In this example, we have defined a `Graph` class with methods to add vertices, add edges between vertices, and retrieve neighboring vertices for a given vertex.

## Depth-First Search (DFS) Traversal

Depth-First Search is a classic graph traversal algorithm that explores as far as possible along each branch before backtracking. We can implement DFS traversal using JavaScript iterators. Let's see how:

```javascript
Graph.prototype.dfsTraversal = function* (startVertex) {
  const visited = new Set();

  yield startVertex;
  visited.add(startVertex);

  for (const neighbor of this.getNeighbors(startVertex)) {
    if (!visited.has(neighbor)) {
      yield* this.dfsTraversal(neighbor);
    }
  }
};

for (const vertex of graph.dfsTraversal(1)) {
  console.log(vertex);
}
```

In this code snippet, we define a generator function `dfsTraversal` on the `Graph` prototype. Using a `Set` to keep track of visited vertices, we recursively traverse the graph depth-first, yielding each vertex as it is visited. Finally, we can iterate over the traversal results using a `for...of` loop.

## Pathfinding with Breadth-First Search (BFS)

Breadth-First Search is another popular graph traversal algorithm used for finding the shortest path between two vertices. To perform pathfinding using BFS, we can utilize JavaScript iterators as well. Here's an example:

```javascript
Graph.prototype.bfsPathfinding = function* (startVertex, targetVertex) {
  const queue = [[startVertex, []]];
  const visited = new Set();

  while (queue.length > 0) {
    const [currentVertex, path] = queue.shift();

    visited.add(currentVertex);

    for (const neighbor of this.getNeighbors(currentVertex)) {
      if (!visited.has(neighbor)) {
        const newPath = [...path, currentVertex];

        if (neighbor === targetVertex) {
          yield [...newPath, neighbor]; // Found the target, yield the path
        } else {
          queue.push([neighbor, newPath]);
        }
      }
    }
  }
};

for (const path of graph.bfsPathfinding(1, 3)) {
  console.log(path);
}
```

In this code snippet, we use a queue to perform a breadth-first search for the target vertex. As we explore each neighbor vertex, we add the current path and vertex to the queue. If the target vertex is encountered, we yield the complete path. The `for...of` loop will then iterate over all the paths found.

## Conclusion

JavaScript iterators provide a powerful way to implement graph traversal and pathfinding algorithms. Using the examples above, you can now apply these concepts to traverse and find paths within your own graphs. Leveraging JavaScript iterators can help you write more efficient and readable code when working with graphs in JavaScript.

#javascript #graph #pathfinding #traversal