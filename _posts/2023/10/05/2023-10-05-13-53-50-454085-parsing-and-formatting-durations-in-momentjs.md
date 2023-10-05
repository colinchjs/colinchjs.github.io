---
layout: post
title: "Parsing and formatting durations in Moment.js"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

In JavaScript, working with durations can sometimes be a bit tricky, especially when it comes to parsing and formatting them correctly. With the help of the Moment.js library, we can easily handle durations and perform various operations on them.

## Parsing Durations

When parsing durations in Moment.js, we can use the `moment.duration` function. This function accepts a string representation of a duration and creates a `Duration` object that we can work with.

Here's an example of parsing a duration string:

```javascript
const durationString = '2 hours';
const duration = moment.duration(durationString);
```
Here, we passed the duration string "2 hours" to the `moment.duration` function, which created a `Duration` object `duration`. Now, we can use this object to perform various operations.

## Formatting Durations

Formatting durations in Moment.js is just as straightforward. We can use the `humanize` method of the `Duration` object to get a human-readable string representation of the duration.

Here's an example of formatting a duration:

```javascript
const formattedDuration = duration.humanize(); // Outputs: "2 hours"
console.log(formattedDuration);
```

In this example, we called the `humanize` method on the `duration` object, which returned the formatted duration string "2 hours".

## Custom Formatting

Moment.js also provides options for custom formatting of durations. We can use the `format` method of the `Duration` object along with token strings to specify our desired formatting pattern.

Here's an example of custom formatting:

```javascript
const formattedDuration = duration.format("h [hours] m [minutes]"); // Outputs: "2 hours"
console.log(formattedDuration);
```

In this example, we used the token strings `h` and `m` to represent hours and minutes, respectively. The square brackets `[]` indicate that the enclosed part may be omitted if its value is zero.

## Conclusion

Parsing and formatting durations in Moment.js is a breeze thanks to its intuitive API. By using the `moment.duration` function for parsing and the `humanize` or `format` methods for formatting, we can easily handle durations in our JavaScript applications.

By correctly parsing and formatting durations, we can improve the user experience and ensure that durations are displayed in a clear and understandable way.

#momentjs #parsing #formatting