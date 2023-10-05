---
layout: post
title: "Parsing a time string with a non-standard time format pattern using Moment.js"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

When working with date and time in JavaScript, the Moment.js library is a popular choice due to its flexibility and ease of use. However, it follows the standard date and time format patterns defined by the ISO-8601 standard. But what if you have a non-standard time format pattern? In this article, we will learn how to parse a time string with a non-standard time format pattern using Moment.js.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Parsing a Time String](#parsing-a-time-string)
- [Custom Time Format Pattern](#custom-time-format-pattern)
- [Conclusion](#conclusion)
- [Hashtags](#hashtags)

<a name="prerequisites"></a>
## Prerequisites

To follow along with this tutorial, you'll need to have the Moment.js library installed in your project. You can either include it directly in your HTML file using a script tag or install it via a package manager like npm or yarn.

<a name="parsing-a-time-string"></a>
## Parsing a Time String

Moment.js provides a `moment()` function that allows us to create moment objects from timestamps, dates, and strings. By default, it attempts to parse the string using the ISO-8601 standard format. For example:

```javascript
const timeString = '2022-01-01T12:30:00';
const momentObj = moment(timeString);
console.log(momentObj.format('HH:mm:ss'));
// Output: 12:30:00
```

In the above example, the time string follows the ISO-8601 format, and Moment.js can successfully parse it and format it as desired.

<a name="custom-time-format-pattern"></a>
## Custom Time Format Pattern

What if you have a time string in a non-standard format? Moment.js provides a way to parse time strings with custom format patterns using the `moment().parse()` function. Let's consider an example:

```javascript
const timeString = '01/01/2022 12:30 PM';
const momentObj = moment(timeString, 'MM/DD/YYYY hh:mm A');
console.log(momentObj.format('HH:mm:ss'));
// Output: 12:30:00
```

In the above example, the `moment()` function takes the time string and the custom format pattern as parameters. The format pattern consists of various tokens, such as `MM` for the month, `DD` for the day, `YYYY` for the year, `hh` for the hour, `mm` for the minutes, and `A` for AM/PM indicator.

By passing the custom format pattern, Moment.js can parse the time string correctly and format it as desired.

<a name="conclusion"></a>
## Conclusion

Moment.js is a powerful library for handling dates and times in JavaScript. In this article, we learned how to parse time strings with non-standard time format patterns using Moment.js. By leveraging the `moment().parse()` function and defining the custom format pattern, we can accurately parse time strings in various formats.

It is important to keep in mind that Moment.js is a deprecated library. It is recommended to use alternatives like Luxon and Day.js, which offer similar functionality with improved performance and maintainability.

<a name="hashtags"></a>
## Hashtags

#MomentJs #TimeParsing