---
layout: post
title: "Binary Search Tree Algorithm"
description: " "
date: 2023-10-01
tags: [programming, algorithm]
comments: true
share: true
---

A Binary Search Tree (BST) is a data structure that allows for efficient searching, insertion, and deletion operations. Here, we will cover the algorithm for working with a BST.

## Basic Structure

A Binary Search Tree is a tree data structure where each node has at most two children, referred to as left and right child. The left child is always smaller than the parent, while the right child is always greater.

## Algorithm for Insertion

To insert a new element into a BST, follow these steps:

1. Start with the root node.
2. If the tree is empty, create a new node and make it the root.
3. If the value of the new node is less than the current node's value, move to the left child.
4. If the value of the new node is greater than the current node's value, move to the right child.
5. Repeat steps 3-4 until an appropriate spot is found.
6. Insert the new node at the appropriate spot.

```python
# Python implementation of the BST insertion algorithm

class Node:
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

def insert(root, value):
    if root is None:
        return Node(value)
    elif value < root.value:
        root.left = insert(root.left, value)
    else:
        root.right = insert(root.right, value)
    return root

# Example usage
root = Node(5)
insert(root, 3)
insert(root, 7)
insert(root, 1)
```

## Algorithm for Searching

To search for a value in a BST, follow these steps:

1. Start with the root node.
2. If the value to search for is equal to the current node's value, return the current node.
3. If the value is less than the current node's value, move to the left child.
4. If the value is greater than the current node's value, move to the right child.
5. Repeat steps 2-4 until the value is found or a leaf node is reached.
6. If the value is not found, return null or raise an exception.

```python
# Python implementation of the BST search algorithm

def search(root, value):
    if root is None or root.value == value:
        return root
    if value < root.value:
        return search(root.left, value)
    return search(root.right, value)

# Example usage
found_node = search(root, 7)
if found_node:
    print("Value found!")
else:
    print("Value not found.")
```

These algorithms provide the basic operations for working with a Binary Search Tree. With its efficient search and insertions, the BST data structure is a fundamental tool in computer science and is widely used in various applications. 

#programming #bst #algorithm