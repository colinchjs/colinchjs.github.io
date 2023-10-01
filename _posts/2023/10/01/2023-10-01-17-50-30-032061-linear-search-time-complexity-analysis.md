---
layout: post
title: "Linear Search Time Complexity Analysis"
description: " "
date: 2023-10-01
tags: [search, algorithm]
comments: true
share: true
---

## Introduction

In computer science, linear search is a simple algorithm for finding a target value within a list or an array. It sequentially checks each element of the list until a match is found or until all elements have been checked. This algorithm has a time complexity of O(n), where n is the number of elements in the list.

## The Algorithm

The linear search algorithm can be implemented as follows:

```python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1
```

The function `linear_search` takes in an array (`arr`) and a target value. It then iterates through each element of the array and checks if it matches the target value. If a match is found, the index of the element is returned. If no match is found, -1 is returned.

## Time Complexity Analysis

The time complexity of linear search can be analyzed by looking at the worst-case scenario. In the worst case, the target value is not present in the array, and the algorithm needs to iterate through all the elements.

Let's assume the array has n elements. In the worst case scenario, we would need to compare the target value with each element. Therefore, the maximum number of comparisons would be n.

Hence, the time complexity of linear search is O(n).

## Conclusion

Linear search is a simple and straightforward algorithm for finding a target value in a list or an array. However, its time complexity of O(n) makes it inefficient for large datasets. For scenarios where efficiency is crucial, other search algorithms like binary search can be used.

#search #algorithm