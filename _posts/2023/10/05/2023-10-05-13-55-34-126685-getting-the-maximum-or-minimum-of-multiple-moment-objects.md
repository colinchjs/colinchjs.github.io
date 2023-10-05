---
layout: post
title: "Getting the maximum or minimum of multiple moment objects"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

When working with date and time in JavaScript, the **Moment.js** library provides a powerful set of tools to manipulate and compare dates. However, there may be situations where you need to find the maximum or minimum value from a collection of Moment objects. In this article, we'll explore how to achieve this using Moment.js.

## Finding the maximum value

To find the maximum value from multiple Moment objects, you can use the `Math.max` function along with the `valueOf` method of Moment objects. The `valueOf` method returns the Unix timestamp representing the moment.

Here's an example code snippet that demonstrates how to find the maximum value:

```javascript
let moment1 = moment("2022-01-01");
let moment2 = moment("2022-01-03");
let moment3 = moment("2022-01-02");

let maxMoment = moment(Math.max(moment1.valueOf(), moment2.valueOf(), moment3.valueOf()));

console.log("Maximum moment:", maxMoment.format());
```

In this example, we create three Moment objects representing different dates. The `Math.max` function is used to find the maximum of the three values obtained by calling `valueOf` on each Moment object. Finally, we create a new Moment object using the maximum value and display it on the console.

## Finding the minimum value

Finding the minimum value is similar to finding the maximum. Instead of using `Math.max`, we can use `Math.min` along with the `valueOf` method of Moment objects.

```javascript
let moment1 = moment("2022-01-01");
let moment2 = moment("2022-01-03");
let moment3 = moment("2022-01-02");

let minMoment = moment(Math.min(moment1.valueOf(), moment2.valueOf(), moment3.valueOf()));

console.log("Minimum moment:", minMoment.format());
```

In this code snippet, we create three Moment objects representing different dates. The `Math.min` function is used to find the minimum of the three values obtained by calling `valueOf` on each Moment object. Finally, we create a new Moment object using the minimum value and display it on the console.

## Conclusion

By using the `valueOf` method and the `Math.max` or `Math.min` function, you can easily find the maximum or minimum value from a collection of Moment objects. This can be particularly useful when working with arrays or when you need to compare multiple dates and find the extreme values.

Remember to import the Moment.js library or include it in your project before using the code snippets provided in this article.

**#momentjs #datetime**