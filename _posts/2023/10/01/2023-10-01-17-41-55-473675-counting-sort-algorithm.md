---
layout: post
title: "Counting Sort Algorithm"
description: " "
date: 2023-10-01
tags: [sortingalgorithm, countingsort]
comments: true
share: true
---

Counting Sort is a simple yet efficient sorting algorithm that works well when the range of input values is small. It is not a comparison-based algorithm like bubble sort or merge sort, but it relies on counting the occurrences of each unique element in the input array. This algorithm works best for sorting non-negative integers. 

## How Counting Sort works

The algorithm involves three steps:

1. Counting the occurrences of each element: Create a count array of size `k`, where `k` is the range of input values. Iterate through the input array and increment the corresponding count for each element.

2. Calculating the running sum of counts: Modify the count array by calculating the running sum of counts. This step helps determine the position of each element in the sorted output array.

3. Building the sorted output array: Iterate through the input array in reverse order. For each element, find its position in the count array and place it in the correct position in the output array.

## Example Implementation in Python

Here's an example implementation of Counting Sort in Python:

```python
def counting_sort(arr):
    # Find the maximum element in the input array
    max_element = max(arr)
    
    # Create a count array of size (max_element + 1) and initialize all values to 0
    count = [0] * (max_element + 1)
    
    # Calculate the count of each element
    for i in arr:
        count[i] += 1
    
    # Calculate the running sum of counts
    for i in range(1, len(count)):
        count[i] += count[i - 1]
    
    # Build the sorted output array
    output = [0] * len(arr)
    for i in range(len(arr) - 1, -1, -1):
        output[count[arr[i]] - 1] = arr[i]
        count[arr[i]] -= 1
    
    return output
```

## Complexity Analysis

The time complexity of Counting Sort is O(n + k), where n is the number of elements in the input array and k is the range of input values. The space complexity is O(n + k) as well, due to the auxiliary count array.

## Conclusion

Counting Sort is a useful algorithm when we have a small range of input values. It outperforms comparison-based sorting algorithms in terms of time complexity but may require additional space to store the count array. 

By understanding the working principles and implementation details of Counting Sort, you can apply this algorithm in scenarios where it fits well and improve the efficiency of your sorting tasks.

#sortingalgorithm #countingsort