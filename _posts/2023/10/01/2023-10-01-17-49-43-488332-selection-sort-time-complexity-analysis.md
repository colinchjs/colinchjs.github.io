---
layout: post
title: "Selection Sort Time Complexity Analysis"
description: " "
date: 2023-10-01
tags: [algorithm, sorting]
comments: true
share: true
---

Selection sort is a simple sorting algorithm often used for educational purposes due to its simplicity. In this blog post, we will analyze the time complexity of selection sort and understand how it performs for different input sizes.

## Introduction to Selection Sort

Selection sort works by dividing the input into two parts - sorted and unsorted. It repeatedly selects the smallest element from the unsorted part and places it at the beginning of the sorted part. This process is repeated until the entire array is sorted.

Here is an example implementation of selection sort in Python:

```python
def selection_sort(arr):
    n = len(arr)
    
    for i in range(n):
        min_index = i
        for j in range(i+1, n):
            if arr[j] < arr[min_index]:
                min_index = j
                
        arr[i], arr[min_index] = arr[min_index], arr[i]
    
    return arr
```

## Time Complexity Analysis

The time complexity of selection sort can be analyzed by examining the number of comparisons and swaps performed.

### Comparisons

The outer loop of selection sort iterates `n` times, where `n` is the number of elements in the array. For each iteration, the inner loop iterates `n-i-1` times. Hence, the total number of comparisons is the sum of `n-1`, `n-2`, ..., 1, which can be expressed as `(n-1) * n / 2`.

### Swaps

Selection sort performs a swap operation for each iteration of the outer loop. Therefore, the total number of swaps is `n-1`.

Hence, the time complexity of selection sort is `O(n^2)` in the worst-case scenario, as both the number of comparisons and swaps are quadratic in the input size.

## Conclusion

Selection sort has a time complexity of `O(n^2)`, which makes it inefficient for large input sizes. It is mainly used for educational purposes and not recommended for practical use when more efficient sorting algorithms like merge sort or quicksort are available.

#algorithm #sorting