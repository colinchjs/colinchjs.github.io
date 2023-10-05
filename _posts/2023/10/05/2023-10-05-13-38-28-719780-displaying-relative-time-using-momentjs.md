---
layout: post
title: "Displaying relative time using Moment.js"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

In web development, displaying relative time is a common requirement for displaying dates and time in a human-readable format. One popular library that simplifies this task is Moment.js. Moment.js is a JavaScript library that allows you to manipulate, format, and parse dates and time.

In this tutorial, we will learn how to display relative time using Moment.js. We will cover the following topics:

1. [Installation](#installation)
2. [Using Moment.js to display relative time](#using-moment-js-to-display-relative-time)
3. [Examples](#examples)

Let's get started!

## 1. Installation {#installation}

To use Moment.js in your project, you need to include the library in your HTML file. You can do this by adding the following script tag in the `<head>` section of your HTML file:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
```

Alternatively, you can download the Moment.js library from the [official website](https://momentjs.com/downloads/moment.min.js) and include it in your project manually.

## 2. Using Moment.js to display relative time {#using-moment-js-to-display-relative-time}

Once you have included the Moment.js library in your project, you can easily display relative time using the `moment()` function. The `moment()` function returns a Moment object that represents the current date and time.

To display relative time, you can use the `fromNow()` method on a Moment object. This method returns a string representing the relative time from the current date and time.

Here's an example of how to display relative time using Moment.js:

```javascript
const now = moment();
const relativeTime = now.fromNow();

console.log(relativeTime);
```

The output of this code will be something like "2 hours ago" or "a few seconds ago" depending on the current date and time.

## 3. Examples {#examples}

Let's see some more examples of displaying relative time using Moment.js:

```javascript
const timestamp = "2021-09-20T10:30:00Z";
const relativeTime = moment(timestamp).fromNow();

console.log(relativeTime);
```

Output: "12 hours ago"

```javascript
const date = moment("2021-09-25");
const relativeTime = date.fromNow();

console.log(relativeTime);
```

Output: "2 days ago"

These examples showcase how easy it is to display relative time using Moment.js. You can apply the `fromNow()` method to any valid Moment object to get the relative time from the current date and time.

## Conclusion

Moment.js provides a simple and convenient way to display relative time in web applications. By using the `moment()` function and the `fromNow()` method, you can effortlessly display dates and time in a human-readable format. It's a powerful tool for improving the user experience and making your web applications more intuitive.

Make sure to check out the official [Moment.js documentation](https://momentjs.com/docs/) for more information on how to use this library and its various features.

#momentjs #webdevelopment