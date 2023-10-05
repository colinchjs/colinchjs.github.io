---
layout: post
title: "Parsing a string formatted in a non-standard date/time format using Moment.js"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

When working with date and time in JavaScript, the Moment.js library is a go-to choice due to its powerful parsing and formatting capabilities. However, sometimes you may come across a scenario where the date and time string you need to parse is not in a standard format recognized by Moment.js. In such cases, you can still parse it using Moment.js by providing a custom format.

Here's how you can parse a string formatted in a non-standard date/time format using Moment.js:

```javascript
const moment = require('moment');

const dateString = '2021-03-15 06:30 PM';

const customFormat = 'YYYY-MM-DD hh:mm A';

const parsedDate = moment(dateString, customFormat);

console.log(parsedDate.format());  // Output: 2021-03-15T18:30:00+00:00

```

In the code snippet above, we start by importing the Moment.js library using the `require` statement. Then, we define the date string we want to parse in the `dateString` variable. In this example, the date string is `'2021-03-15 06:30 PM'`.

Next, we define the custom format that matches the format of the date string using Moment.js tokens. In this case, the format is `'YYYY-MM-DD hh:mm A'`. The `YYYY` token represents the 4-digit year, `MM` represents the 2-digit month, `DD` represents the 2-digit day, `hh` represents the 2-digit hour in 12-hour format, `mm` represents the 2-digit minute, and `A` represents the meridiem (AM/PM).

Finally, we use the `moment` function to parse the date string using the custom format. The resulting parsed date object is stored in the `parsedDate` variable.

To verify that the parsing was successful, we use the `format` function of the `parsedDate` object to output the parsed date in the default format. In this example, the output is `'2021-03-15T18:30:00+00:00'`, which represents the same date and time in the ISO 8601 format.

By providing a custom format, you can parse date and time strings in non-standard formats using Moment.js. This flexibility allows you to handle various date and time formats in your applications with ease.

#javascript #MomentJs