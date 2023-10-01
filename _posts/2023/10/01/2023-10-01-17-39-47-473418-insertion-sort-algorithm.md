---
layout: post
title: "Insertion Sort Algorithm"
description: " "
date: 2023-10-01
tags: []
comments: true
share: true
---

Insertion sort is a simple and efficient sorting algorithm that works by repeatedly comparing adjacent elements and swapping them if they are in the wrong order. It is an in-place sorting algorithm, which means it operates directly on the input array without requiring additional space.

### How insertion sort works?

The insertion sort algorithm works by dividing the array into two parts: sorted and unsorted. At the beginning, the first element in the array is considered as the sorted part. The algorithm then iterates through the unsorted part, one element at a time, and compares it with elements in the sorted part. It finds the appropriate position for the current element in the sorted part and inserts it there. This process continues until the entire array becomes sorted.

### Pseudocode for Insertion Sort

Here is the pseudocode for the insertion sort algorithm:

```
insertionSort(array)
  for i from 1 to length(array) - 1
    key = array[i]
    j = i - 1
    while j >= 0 and array[j] > key
      array[j + 1] = array[j]
      j = j - 1
    array[j + 1] = key
```

### Example Code in Python

Here is an example implementation of the insertion sort algorithm in Python:

```python
def insertion_sort(array):
    for i in range(1, len(array)):
        key = array[i]
        j = i - 1
        while j >= 0 and array[j] > key:
            array[j + 1] = array[j]
            j = j - 1
        array[j + 1] = key

# Example usage
arr = [5, 2, 8, 12, 1, 6]
insertion_sort(arr)
print(arr)  # Output: [1, 2, 5, 6, 8, 12]
```

### Complexity analysis

The worst-case time complexity of the insertion sort algorithm is O(n^2) when the input array is in reverse order. The best-case time complexity is O(n) when the input array is already sorted. The average-case time complexity is also O(n^2). The space complexity is O(1) since it sorts the array in-place.

### Conclusion

Insertion sort is a simple and efficient sorting algorithm that works well for small-sized or partially sorted arrays. While it is not as fast as some more advanced sorting algorithms like merge sort or quicksort, it is easy to understand and implement. Use insertion sort when simplicity and space efficiency are important considerations.