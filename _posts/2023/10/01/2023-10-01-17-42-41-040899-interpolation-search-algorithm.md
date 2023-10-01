---
layout: post
title: "Interpolation Search Algorithm"
description: " "
date: 2023-10-01
tags: [InterpolationSearch, Algorithm]
comments: true
share: true
---

Interpolation search is a **search algorithm** used to efficiently find a specific element in a sorted array of values. It is an improvement over **binary search** as it can adaptively narrow down the search range based on the values in the array.

The interpolation search algorithm works by estimating the position of the target value based on the values of the first and last elements in the array. It then narrows down the search range by calculating a new position based on the estimated estimate and the value at that position. This process is repeated until the target value is found or determined to be not present in the array.

The core idea behind interpolation search is to use **interpolation formula** to predict the probable position of the target value:

```
pos = low + ((high - low) / (arr[high] - arr[low])) * (x - arr[low])
```

Where `low` and `high` are the starting and ending indices of the search range, `arr` is the sorted array, and `x` is the target value.

The interpolation search algorithm has an average time complexity of **O(log log n)**, making it faster than binary search for large input arrays with uniformly distributed values. However, it may perform poorly in certain scenarios, such as when the array contains *repeated or non-uniformly distributed values*.

### Algorithm Steps:

1. Initialize `low` and `high` to the starting and ending indices of the search range.
2. While the target value is within the range and not found:
   - Calculate the estimated position using the interpolation formula.
   - If the estimated position matches the target value, return its index.
   - If the estimated value is *less* than the target value, narrow down the range to the higher half.
   - If the estimated value is *greater* than the target value, narrow down the range to the lower half.
3. If the target value is not found, return -1 to indicate its absence in the array.

### Example Code (Python):

```python
def interpolation_search(arr, x):
    low = 0
    high = len(arr) - 1

    while low <= high and x >= arr[low] and x <= arr[high]:
        pos = low + ((high - low) // (arr[high] - arr[low])) * (x - arr[low])

        if arr[pos] == x:
            return pos

        if arr[pos] < x:
            low = pos + 1
        else:
            high = pos - 1

    return -1
```

### Conclusion

Interpolation search is an efficient search algorithm that can be used to quickly find a specific element in a sorted array. While it provides a faster average case time complexity compared to binary search, it may not always outperform it in certain scenarios. Understanding the strengths and limitations of interpolation search can help in choosing the most appropriate search algorithm for a given problem. #InterpolationSearch #Algorithm