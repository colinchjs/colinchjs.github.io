---
layout: post
title: "Storing multiple values in a single cookie in JavaScript"
description: " "
date: 2023-09-24
tags: []
comments: true
share: true
---

Cookies are small text files that are stored on a user's device by a website. They are commonly used to store small pieces of information such as user preferences, session data, and shopping cart details.

In JavaScript, cookies can be accessed and manipulated using the `document.cookie` property. By default, cookies can only store a single value. However, there are cases where you may need to store multiple values in a single cookie. In this blog post, we will explore a technique to achieve this.

## JSON.stringify and JSON.parse

One way to store multiple values in a single cookie is by serializing an object or an array using JSON. The JSON (JavaScript Object Notation) format allows us to convert JavaScript objects or arrays into a string representation that can be stored as a cookie value.

To store multiple values in a cookie, follow these steps:

1. Create an object or an array that contains the values you want to store:
```javascript
const userData = {
  username: "john_doe",
  email: "john@example.com",
  role: "user"
};
```

2. Convert the object or array into a string using `JSON.stringify()`:
```javascript
const cookieValue = JSON.stringify(userData);
```

3. Set the cookie with the string value:
```javascript
document.cookie = `userData=${cookieValue}`;
```

To retrieve the stored values from the cookie, follow these steps:

1. Get the cookie value using the `document.cookie` property:
```javascript
const cookieData = document.cookie
  .split('; ')
  .find(row => row.startsWith('userData='))
  .split('=')[1];
```

2. Parse the cookie value back into an object or array using `JSON.parse()`:
```javascript
const userData = JSON.parse(cookieData);
```

3. Access the stored values as properties of the object or elements of the array:
```javascript
console.log(userData.username); // Output: john_doe
console.log(userData.email); // Output: john@example.com
console.log(userData.role); // Output: user
```

By using the `JSON.stringify()` and `JSON.parse()` functions, we can easily store and retrieve multiple values in a single cookie in JavaScript.

## Conclusion

Storing multiple values in a single cookie can be achieved by serializing an object or an array into a string using `JSON.stringify()`. Similarly, the serialized string can be parsed back into its original form using `JSON.parse()`. This technique allows us to store complex data structures in cookies and retrieve them when needed.

Remember to use this approach responsibly and be mindful of the size limitations, as cookies have size restrictions.