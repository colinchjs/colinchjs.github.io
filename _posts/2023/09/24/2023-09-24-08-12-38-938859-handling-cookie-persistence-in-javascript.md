---
layout: post
title: "Handling cookie persistence in JavaScript"
description: " "
date: 2023-09-24
tags: [cookies, JavaScript]
comments: true
share: true
---

Have you ever needed to store user information or preferences on a website? One common way to achieve this is by using cookies. Cookies are small pieces of data that are stored on a user's browser and can be accessed by the website each time the user visits it. In JavaScript, managing cookies is relatively straightforward, but ensuring their persistence can be a bit more challenging. In this blog post, we will explore techniques to handle cookie persistence in JavaScript.

## Set Cookie Expiration

By default, cookies do not have an expiration date and are considered *session cookies*. This means they are only valid for the duration of the user's browsing session. To make a cookie persist beyond the current session, we need to set an expiration date. We can achieve this by specifying the number of seconds from the current time when creating the cookie.

```javascript
const expiryDate = new Date();
expiryDate.setDate(expiryDate.getDate() + 7); // Cookie will expire in 7 days
document.cookie = `username=John Doe; expires=${expiryDate.toUTCString()}`;
```

In the example above, we set the expiry date of the cookie to be 7 days from the current date. This will make the cookie persist on the user's browser for a week.

## Handle Cookie Retrieval

To retrieve a cookie value in JavaScript, we parse the `document.cookie` string and extract the desired value. Each cookie is separated by a semicolon, so we split the string to get individual cookie key-value pairs.

```javascript
function getCookieValue(cookieName) {
  const cookies = document.cookie.split(';');
  for (let i = 0; i < cookies.length; i++) {
    const cookie = cookies[i].trim();
    if (cookie.startsWith(`${cookieName}=`)) {
      return cookie.split('=')[1];
    }
  }
  return '';
}

// Usage:
const username = getCookieValue('username');
console.log(username); // Output: "John Doe"
```

In the code snippet above, we create a function `getCookieValue` that takes in the cookie name as a parameter and returns its corresponding value. By looping through all the cookies, we can find the specific cookie we're interested in and extract its value.

## Refresh Cookie Expiration

When a user interacts with a website, we might want to refresh the cookie expiration to ensure it remains valid. This can be easily done by updating the cookie's expiration date using the same process we described earlier.

Here's an example of how to refresh a cookie's expiry date:

```javascript
function refreshCookieExpiration(cookieName) {
  const cookieValue = getCookieValue(cookieName);
  if (cookieValue) {
    const expiryDate = new Date();
    expiryDate.setDate(expiryDate.getDate() + 7); // Refresh the cookie's expiration to 7 days from now
    document.cookie = `${cookieName}=${cookieValue}; expires=${expiryDate.toUTCString()}`;
  }
}

// Usage:
refreshCookieExpiration('username');
```

The `refreshCookieExpiration` function takes the cookie name as a parameter, retrieves its value, and updates its expiration date if the cookie exists.

By understanding how to set, retrieve, and refresh cookie expiration in JavaScript, you can effectively manage cookie persistence on your website. This is essential for storing user preferences, session data, or any other information that needs to persist between visits.

#cookies #JavaScript