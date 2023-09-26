---
layout: post
title: "Setting expiration time for session storage in JavaScript"
description: " "
date: 2023-09-21
tags: [SessionStorageExpiration]
comments: true
share: true
---

In web development, session storage is commonly used to store data temporarily on the client-side. However, the data stored in session storage is cleared once the user closes the browser tab or window.

Sometimes, you may want to set an expiration time for session storage, so that the data remains accessible for a specific duration, even if the user refreshes the page or closes and reopens the browser. In this article, we will explore how to set an expiration time for session storage in JavaScript.

## Using a timestamp to set expiration time

One way to set an expiration time for session storage is by using a timestamp. Here's an example of how you can achieve this:

```javascript
const data = {
  // your data here
};

const expirationTime = new Date().getTime() + (60 * 60 * 1000); // 1 hour from now
sessionStorage.setItem('data', JSON.stringify(data));
sessionStorage.setItem('expirationTime', expirationTime);

// To check if the data has expired
const currentTime = new Date().getTime();
const storedTime = sessionStorage.getItem('expirationTime');
if (currentTime > storedTime) {
  sessionStorage.removeItem('data');
  sessionStorage.removeItem('expirationTime');
}
```

In the above example, we first create an object `data` which represents the data we want to store in session storage. We then set the expiration time to be one hour from the current time using `new Date().getTime()`.

We stringify the `data` object and store it in session storage with the key `'data'`. Additionally, we store the expiration time in session storage with the key `'expirationTime'`.

To check if the stored data has expired, we compare the current time with the stored expiration time. If the current time is greater than the stored expiration time, we remove the data and expiration time from session storage.

## Adding a custom hashtag to indicate that the article is about session storage expiration in JavaScript
#### #JavaScript #SessionStorageExpiration