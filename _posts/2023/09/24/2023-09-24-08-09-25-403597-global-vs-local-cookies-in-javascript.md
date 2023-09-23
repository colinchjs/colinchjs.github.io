---
layout: post
title: "Global vs local cookies in JavaScript"
description: " "
date: 2023-09-24
tags: []
comments: true
share: true
---

Cookies are small pieces of data stored on the client's machine by websites. They are commonly used to store user preferences, session information, and other data that needs to persist across different pages or visits.

In JavaScript, cookies can be classified into two types: global cookies and local cookies.

## Global Cookies
Global cookies are accessible to all the pages on the same domain. They are set using the `document.cookie` property and can be accessed and modified from any page within the domain. Global cookies are useful when you need to share data across multiple pages or maintain session information.

Here's an example of setting a global cookie:
```javascript
document.cookie = "username=John Doe; expires=Thu, 18 Dec 2025 12:00:00 UTC; path=/";
```
In this example, we set a cookie named "username" with the value "John Doe" and an expiration date of December 18, 2025. The `path=/` attribute ensures that the cookie is accessible from all pages within the domain.

To retrieve the value of a global cookie, you can simply access the `document.cookie` property, which returns a semicolon-separated string of all the cookies on the current domain.

## Local Cookies
Local cookies, also known as local storage, are specific to a single web page. They use the `localStorage` object to store data locally within the browser. Local storage is often used when you need to save user preferences or cache data for a specific page.

Here's an example of setting a local cookie using `localStorage`:
```javascript
localStorage.setItem("theme", "dark");
```
In this example, we store the value "dark" under the key "theme" in the local storage.

To retrieve the value of a local cookie, you can use the `getItem` method of the `localStorage` object:
```javascript
const theme = localStorage.getItem("theme");
```
In this case, the `theme` variable will contain the value "dark".

## Conclusion
Global cookies and local cookies both serve different purposes in JavaScript. Global cookies are accessible across multiple pages within a domain and are useful for maintaining session-related information. On the other hand, local cookies or local storage are specific to a single web page and are often used for storing user preferences or caching data.

Overall, the choice between global and local cookies depends on your specific requirements and the type of data you want to store.