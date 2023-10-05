---
layout: post
title: "Parsing a Unix timestamp with milliseconds using Moment.js"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

When working with timestamps in JavaScript, it can be helpful to use a library like Moment.js to parse and manipulate dates and times. In some cases, you may need to parse a Unix timestamp that includes milliseconds. In this case, Moment.js provides a convenient way to handle these timestamps.

To parse a Unix timestamp with milliseconds using Moment.js, you can use the `moment` function and pass the timestamp as an argument along with the format string that matches the timestamp format. Here's an example:

```javascript
const timestamp = 1616590915060; // Unix timestamp with milliseconds

const date = moment(timestamp).format('YYYY-MM-DD HH:mm:ss.SSS');
console.log(date);
```

In this example, the timestamp `1616590915060` is passed to the `moment` function, and the format string `'YYYY-MM-DD HH:mm:ss.SSS'` is used to specify the output format. The resulting formatted date will include the year, month, day, hour, minute, second, and milliseconds.

The output of the above code will be:

```
2021-03-24 14:21:55.060
```

By using Moment.js, you can easily parse a Unix timestamp with milliseconds and format it in a desired way. This can be particularly useful when working with APIs that return timestamps in this format.

Note that Moment.js is now considered a legacy project and is in maintenance mode. The Moment team recommends using modern date and time libraries like Luxon or Date-fns for new projects.

To conclude, by utilizing Moment.js, you can effectively parse Unix timestamps with milliseconds and format them according to your needs. This enables you to handle and display precise timestamps with ease.

\#javascript #momentjs