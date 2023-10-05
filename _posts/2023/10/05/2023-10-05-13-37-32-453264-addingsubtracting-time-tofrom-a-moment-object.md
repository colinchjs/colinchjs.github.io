---
layout: post
title: "Adding/subtracting time to/from a moment object"
description: " "
date: 2023-10-05
tags: []
comments: true
share: true
---

In JavaScript, the moment.js library provides a simple and convenient way to manipulate date and time objects. One common task is adding or subtracting time from a moment object.

To add or subtract time from a moment object, you can use the `add` and `subtract` methods provided by the moment object. These methods modify the moment object in place and return the modified moment.

Here's an example of how to add time to a moment object:

```javascript
const moment = require('moment');

// Create a moment object for the current time
const now = moment();

// Add 1 hour to the current time
const futureTime = now.add(1, 'hour');

console.log(futureTime.format('YYYY-MM-DD HH:mm:ss'));
```

Output:
```
2022-01-01 14:00:00 
```

In the example above, we import the moment library and create a moment object for the current time using `moment()`. Then, we use the `add` method to add 1 hour to the current time. Finally, we format the modified moment object using `format` method and print it to the console.

Similarly, you can subtract time from a moment object by using the `subtract` method. Here's an example:

```javascript
const moment = require('moment');

// Create a moment object for the current time
const now = moment();

// Subtract 30 minutes from the current time
const pastTime = now.subtract(30, 'minutes');

console.log(pastTime.format('YYYY-MM-DD HH:mm:ss'));
```

Output:
```
2022-01-01 12:30:00 
```

In the example above, we subtracted 30 minutes from the current time and formatted the modified moment object using the `format` method.

By using the `add` and `subtract` methods provided by the moment library, you can easily manipulate moment objects and perform various date and time calculations in JavaScript.

#momentjs #javascript