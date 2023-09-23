---
layout: post
title: "Working with session cookies in JavaScript"
description: " "
date: 2023-09-24
tags: [javascript, sessioncookies]
comments: true
share: true
---

Session cookies are a commonly used technique to store user information on the client-side using JavaScript. They are temporary cookies that are stored only for the duration of a user's session on a website. In this blog post, we will explore how to work with session cookies in JavaScript.

## What are Session Cookies?

Session cookies, also known as transient cookies, are used to store temporary information that is specific to a particular user session. They are stored in memory and are deleted as soon as the user closes their web browser.

Session cookies play a crucial role in web applications as they allow websites to keep track of user activities and provide personalized experiences. They are commonly used for maintaining user login sessions, shopping carts, and other session-specific data.

## Creating Session Cookies

In JavaScript, you can create a session cookie using the `document.cookie` property. Here's an example:

```javascript
document.cookie = "username=John Doe; expires=session; path=/";
```

In the above example, we set a session cookie named "username" with the value "John Doe". The `expires` attribute is set to "session" to indicate that the cookie should expire when the user closes the browser. The `path` attribute specifies the URL path for which the cookie is valid.

## Retrieving Session Cookies

To retrieve the value of a session cookie, you can access the `document.cookie` property and parse it. Here's an example:

```javascript
function getCookie(cookieName) {
  const name = cookieName + "=";
  const decodedCookie = decodeURIComponent(document.cookie);
  const cookieArray = decodedCookie.split(';');
  for (let i = 0; i < cookieArray.length; i++) {
    let cookie = cookieArray[i];
    while (cookie.charAt(0) === ' ') {
      cookie = cookie.substring(1);
    }
    if (cookie.indexOf(name) === 0) {
      return cookie.substring(name.length, cookie.length);
    }
  }
  return "";
}

const username = getCookie("username");
console.log(username);
```

In the above example, we define a `getCookie` function that takes a cookie name as an argument and returns its value. We split the `document.cookie` string into an array of individual cookies, iterate through them, and extract the value of the desired cookie.

## Deleting Session Cookies

To delete a session cookie in JavaScript, you can set its expiration date to a past date. Here's an example:

```javascript
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
```

In the above example, we set the expiration date of the "username" cookie to a date in the past, effectively deleting it.

## Conclusion

Session cookies play a vital role in web development for storing temporary information on the client-side. In this blog post, we explored how to create, retrieve, and delete session cookies using JavaScript. By leveraging session cookies, developers can enhance user experiences and provide personalized content. Start using session cookies in your JavaScript projects to unlock the power of client-side storage.

\#javascript #sessioncookies