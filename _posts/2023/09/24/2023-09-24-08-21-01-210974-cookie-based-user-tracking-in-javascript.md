---
layout: post
title: "Cookie-based user tracking in JavaScript"
description: " "
date: 2023-09-24
tags: [TechBlog]
comments: true
share: true
---

In web development, user tracking is crucial for understanding user behavior, personalizing experiences, and delivering targeted content. One common method to achieve this is through the use of cookies in JavaScript. Cookies are small text files that are stored on the user's device and can be accessed by web servers or JavaScript.

## Setting a Cookie

To track a user's activity, you can set a cookie using the `document.cookie` property in JavaScript. In its simplest form, setting a cookie involves providing a name and a value for the cookie. Here's an example:

```javascript
document.cookie = "userId=12345";
```

In the above code, we set a cookie named "userId" with a value of "12345". The `document.cookie` property allows you to set multiple cookies by separating them with semicolons.

## Reading a Cookie

Once a cookie is set, you can retrieve its value in subsequent page requests. Here's how to read a cookie using JavaScript:

```javascript
const cookies = document.cookie.split("; ");
let userId;

for (let i = 0; i < cookies.length; i++) {
  const cookieParts = cookies[i].split("=");
  const name = cookieParts[0];
  const value = cookieParts[1];

  if (name === "userId") {
    userId = value;
    break;
  }
}

console.log(userId);
```

In this code, we split the `document.cookie` string by semicolon and space to obtain an array of cookies. We then iterate over the array to find the cookie with the name "userId" and retrieve its value.

## Expiring a Cookie

By default, a cookie is considered a session cookie, which means it expires when the user closes the browser. However, you can set an expiration date for a cookie to make it persist across sessions. Here's an example of setting an expiration date:

```javascript
const expirationDate = new Date();
expirationDate.setMonth(expirationDate.getMonth() + 1);

document.cookie = `userId=12345; expires=${expirationDate.toUTCString()}`;
```

In this code, we create a new `Date` object and set the expiration date to one month from the current date. We then use the `toUTCString()` method to format the date as required by the `expires` attribute of the cookie.

## Deleting a Cookie

To remove or delete a cookie, you can simply set its expiration date in the past. Here's an example of deleting the "userId" cookie:

```javascript
const pastDate = new Date("2000-01-01");

document.cookie = "userId=; expires=" + pastDate.toUTCString();
```

In this code, we create a `Date` object representing a past date. Setting the expiration date to a date in the past effectively removes the cookie from the user's device.

## Conclusion

Cookie-based user tracking in JavaScript allows websites to track user data for various purposes. By setting, reading, expiring, and deleting cookies, developers can implement user tracking mechanisms. However, it's essential to consider privacy concerns and inform users about the data being tracked, in compliance with regulations like the General Data Protection Regulation (GDPR).

#TechBlog #JavaScript