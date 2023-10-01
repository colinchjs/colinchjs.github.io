---
layout: post
title: "Topological Sort Time Complexity Analysis"
description: " "
date: 2023-10-01
tags: [techblog, topologicalsort]
comments: true
share: true
---

Topological sort is an algorithm used to sort the vertices of a directed graph in such a way that for every directed edge from vertex A to vertex B, vertex A comes before vertex B in the sorted order. It is commonly used in various applications like task scheduling, dependency resolution, and scheduling jobs with dependencies.

The time complexity of the topological sort algorithm depends on the algorithm used to find the topological ordering. Here, we will discuss two popular algorithms for topological sorting and analyze their time complexities.

## 1. Depth-First Search (DFS) based algorithm

The first algorithm we will discuss is based on Depth-First Search. In this algorithm, we start from an arbitrary vertex and recursively explore all the unvisited vertices adjacent to it. We mark the vertex as visited once we have visited all its adjacent vertices. The topological sorting order is determined by the order in which the vertices finish their recursive exploration.

*Time Complexity: O(V + E)*

- V represents the number of vertices in the graph.
- E represents the number of edges in the graph.

During the depth-first search, every vertex and every edge is visited once. Therefore, the time complexity is *O(V + E)*.

## 2. Kahn's algorithm

Kahn's algorithm is another popular algorithm for topological sorting. It uses the concept of indegrees to find the topological ordering. In this algorithm, we start by finding all the vertices with indegree 0 (vertices that have no incoming edges) and add them to a queue. Then, for each vertex in the queue, we visit its adjacent vertices and decrease their indegree by 1. If any of the adjacent vertices have an indegree of 0 as a result, we add them to the queue. The process continues until all the vertices have been visited.

*Time Complexity: O(V + E)*

- V represents the number of vertices in the graph.
- E represents the number of edges in the graph.

In Kahn's algorithm, we visit each vertex and each edge once. Therefore, the time complexity is also *O(V + E)*.

## Conclusion
Both the Depth-First Search based algorithm and Kahn's algorithm for topological sorting have a time complexity of *O(V + E)*.

Using this analysis, we can determine the efficiency of the topological sort algorithm and choose the most suitable algorithm for our specific use case.

#techblog #topologicalsort