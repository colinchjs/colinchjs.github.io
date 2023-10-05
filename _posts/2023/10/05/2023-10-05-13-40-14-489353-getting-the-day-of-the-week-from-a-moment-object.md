---
layout: post
title: "Getting the day of the week from a moment object"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

When working with dates and times in JavaScript, [Moment.js](https://momentjs.com/) is a popular library that provides a simple and powerful way to manipulate, format, and retrieve various information from date and time objects.

In this blog post, we'll focus on retrieving the day of the week from a Moment object. This is a common requirement in many applications, especially when dealing with calendars, scheduling, or displaying recurring events.

## Prerequisites

Before we begin, make sure you have Moment.js installed in your project. If you haven't already, you can install Moment.js using npm:

```shell
npm install moment
```

Alternatively, you can include Moment.js from a CDN in your HTML file:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.29.1/moment.min.js"></script>
```

## Retrieving the Day of the Week

To get the day of the week from a Moment object, you can make use of the `format()` method provided by Moment.js. The `format()` method allows us to specify various tokens that represent different parts of a date or time.

```javascript
const moment = require('moment');

const date = moment(); // creates a Moment object representing the current date and time
const dayOfWeek = date.format('dddd'); // retrieves the full day of the week
console.log(dayOfWeek); // Output: Thursday
```

In the example above, we first import Moment.js using the `require()` function if you're using Node.js. If you're including Moment.js via a CDN, you can skip the import step.

Next, we create a Moment object representing the current date and time using `moment()`. If you want to work with a specific date or time, you can pass a parameter to `moment()` with the desired value.

Then, we use the `format()` method to retrieve the day of the week. By passing in the `'dddd'` format token, we get the full name of the day. Moment.js provides various format tokens that you can use to retrieve different parts of a date or time.

Finally, we log the `dayOfWeek` variable to the console, which should output the current day of the week. You can replace `date` with any other Moment object to get the day of the week for a specific date.

## Conclusion

Retrieving the day of the week from a Moment object is straightforward using the `format()` method provided by Moment.js. By specifying the `'dddd'` format token, you can get the full name of the day.

Moment.js offers many other useful features for working with dates and times, such as parsing, arithmetic operations, and displaying formatted dates. Be sure to check out the [official Moment.js documentation](https://momentjs.com/docs/) for more information.

#programming #javascript