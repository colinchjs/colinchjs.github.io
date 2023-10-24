---
layout: post
title: "Constructor functions for sorting and searching in JavaScript"
description: " "
date: 2023-10-24
tags: [References, sorting]
comments: true
share: true
---

Sorting and searching are common operations in programming, and JavaScript provides built-in methods to handle them. However, there may be cases where you need more control and customizability when it comes to sorting and searching arrays. Constructor functions in JavaScript can be handy in such situations.

In this blog post, we will explore how to use constructor functions to create custom sorting and searching algorithms in JavaScript.

## Table of Contents
- [Introduction](#introduction)
- [Sorting with Constructor Functions](#sorting-with-constructor-functions)
- [Searching with Constructor Functions](#searching-with-constructor-functions)
- [Conclusion](#conclusion)

## Introduction

Constructor functions allow us to create custom objects with their own properties and methods. We can leverage this feature to create objects that encapsulate sorting and searching algorithms.

## Sorting with Constructor Functions

To create a constructor function for custom sorting, we first define the object and its properties. Let's create a `Sort` object that takes an array as a parameter and has a `bubbleSort` method.

```javascript
function Sort(array) {
  this.array = array;
  
  this.bubbleSort = function() {
    let len = this.array.length;
    
    for (let i = 0;  i < len - 1; i++) {
      for (let j = 0; j < len - 1 - i; j++) {
        if (this.array[j] > this.array[j + 1]) {
          // Swap elements
          let temp = this.array[j];
          this.array[j] = this.array[j + 1];
          this.array[j + 1] = temp;
        }
      }
    }
    
    return this.array;
  }
}
```

Now, we can create a `Sort` object by passing an array to the constructor and call the `bubbleSort` method to sort the array.

```javascript
let numbers = [4, 2, 7, 1, 8];
let customSort = new Sort(numbers);
let sortedArray = customSort.bubbleSort();
console.log(sortedArray); // [1, 2, 4, 7, 8]
```

Using constructor functions for sorting allows us to have more control over the sorting algorithm and customize it based on our specific requirements.

## Searching with Constructor Functions

Similar to sorting, constructor functions can also be used for creating custom searching algorithms. Let's create a `Search` object with a `binarySearch` method that takes an array and a target element as parameters.

```javascript
function Search(array, target) {
  this.array = array;
  this.target = target;
  
  this.binarySearch = function() {
    let low = 0;
    let high = this.array.length - 1;
    
    while (low <= high) {
      let mid = Math.floor((low + high) / 2);
      
      if (this.array[mid] === this.target) {
        return mid;
      } else if (this.array[mid] < this.target) {
        low = mid + 1;
      } else {
        high = mid - 1;
      }
    }
    
    return -1; // Target not found
  }
}
```

We can create a `Search` object by passing an array and the target element to the constructor. Then, we can call the `binarySearch` method to perform the search and get the index of the target element.

```javascript
let numbers = [1, 2, 4, 7, 8];
let customSearch = new Search(numbers, 7);
let targetIndex = customSearch.binarySearch();
console.log(targetIndex); // 3
```

By using constructor functions for searching, we can implement different search algorithms such as binary search, linear search, or even custom search algorithms tailored to our needs.

## Conclusion

Constructor functions in JavaScript offer a powerful way to create custom sorting and searching algorithms. By encapsulating the algorithms inside objects, we can have more control and adaptability. This flexibility allows us to create sorting and searching functionalities that meet our specific requirements.

Next time you need a custom sorting or searching algorithm, consider using constructor functions in JavaScript to build your solution.

#References
- [MDN Web Docs: Constructor function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/constructor)
- [MDN Web Docs: Array.prototype.sort()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
- [MDN Web Docs: Array.prototype.indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
- [Wikipedia: Sorting algorithm](https://en.wikipedia.org/wiki/Sorting_algorithm)
- [Wikipedia: Search algorithm](https://en.wikipedia.org/wiki/Search_algorithm)

#javascript #sorting #searching