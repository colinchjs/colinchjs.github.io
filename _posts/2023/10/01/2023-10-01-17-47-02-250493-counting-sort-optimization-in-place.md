---
layout: post
title: "Counting Sort Optimization (In-Place)"
description: " "
date: 2023-10-01
tags: [CountingSort, Sorting]
comments: true
share: true
---

Counting sort is a simple and efficient sorting algorithm that is often used when the range of input values to be sorted is small. It works by counting the occurrences of each distinct element in the input array and then using those counts to place the elements in sorted order. However, the traditional implementation of counting sort requires additional memory space to store the count of each element.

In this blog post, we will explore an optimization for counting sort that makes it **in-place**, meaning it requires no additional memory beyond the input array.

## Traditional Counting Sort

To understand the optimization, let's first briefly review the traditional counting sort algorithm. The steps involved are as follows:

1. Determine the range of the input values and create an array, `count`, of size equal to the range to store the counts of each element.
2. Iterate over the input array and increment the count for each element encountered.
3. Modify the `count` array such that each count represents the number of elements less than or equal to the corresponding index.
4. Create a new output array, `sorted`, of the same size as the input array.
5. Iterate over the input array again and use the counts to determine the correct position in `sorted` for each element.
6. Copy the elements from `sorted` back to the input array.

## In-Place Counting Sort Optimization

The optimization for in-place counting sort involves modifying the input array directly instead of creating a separate `sorted` array. The steps are as follows:

1. Determine the range of the input values and create an array, `count`, of size equal to the range to store the counts of each element.
2. Iterate over the input array and increment the count for each element encountered.
3. Modify the `count` array such that each count represents the number of elements less than or equal to the corresponding index.
4. Iterate over the input array again and use the counts to shift the elements to their correct position in the array.
5. The array is now sorted in-place.

```python
def counting_sort_inplace(arr):
    if len(arr) == 0:
        return arr

    min_val = min(arr)
    max_val = max(arr)
    count = [0] * (max_val - min_val + 1)

    for num in arr:
        count[num - min_val] += 1
    
    total = 0
    for i in range(len(count)):
        count[i], total = total, total + count[i]
    
    for num in arr:
        index = num - min_val
        while count[index] != index:
            arr[index], arr[count[index]] = arr[count[index]], arr[index]
            count[index], index = index, count[index]

    return arr
```

## Conclusion

In-place counting sort is a valuable optimization that allows us to sort an array using only the existing memory space without the need for additional arrays. This can be particularly useful in situations where memory is limited or efficiency is critical. By understanding the traditional counting sort algorithm and the modifications needed for the in-place optimization, we can leverage this technique to improve the efficiency of our sorting operations. #CountingSort #Sorting