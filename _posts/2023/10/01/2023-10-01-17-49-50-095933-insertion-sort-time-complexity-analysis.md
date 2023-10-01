---
layout: post
title: "Insertion Sort Time Complexity Analysis"
description: " "
date: 2023-10-01
tags: [algorithm, sorting]
comments: true
share: true
---

Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It compares each element with the items before it and inserts it in the correct position in the sorted part of the array.

The time complexity of Insertion Sort can be analyzed as follows:

## Best case scenario
In the best case scenario, when the array is already sorted, Insertion Sort has a time complexity of **O(n)**.

In this case, the algorithm simply checks each element once, finds that it is already in the correct position, and moves on to the next element.

## Average case scenario
In the average case scenario, when the input elements are randomly distributed, Insertion Sort has a time complexity of **O(n^2)**.

In this case, the algorithm needs to compare each element with all the previous elements in the sorted part of the array until it finds the correct position to insert it. As a result, for each element, it performs approximately half of the number of comparisons that would be required in the worst case scenario.

## Worst case scenario
In the worst case scenario, when the input elements are sorted in reverse order, Insertion Sort has a time complexity of **O(n^2)**.

In this case, the algorithm needs to compare each element with all the previous elements in the sorted part of the array and shift them one position to the right until it finds the correct position to insert the element. This results in a maximum number of comparisons and shifts for each element.

## Conclusion
Insertion Sort is not the most efficient sorting algorithm in terms of time complexity, especially for large datasets. However, it has some advantages, such as simplicity and in-place sorting (no additional memory required).

It is important to consider the time complexity analysis of Insertion Sort when choosing the appropriate sorting algorithm for a given problem.

#algorithm #sorting