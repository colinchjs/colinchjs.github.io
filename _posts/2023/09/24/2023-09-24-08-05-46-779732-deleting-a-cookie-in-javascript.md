---
layout: post
title: "Deleting a cookie in JavaScript"
description: " "
date: 2023-09-24
tags: [Cookies]
comments: true
share: true
---

Cookies are small pieces of data that websites store on a user's computer. They are commonly used to remember user preferences, maintain sessions, and provide personalized experiences. In JavaScript, you can create, read, and delete cookies to manage user data.

## Creating a Cookie

Before we dive into deleting a cookie, let's quickly review how to create a cookie in JavaScript. To create a cookie, use the `document.cookie` property and set it equal to a string containing the desired cookie name, value, and optional parameters.

```javascript
document.cookie = "cookieName=cookieValue; expires=Thu, 01 Jan 2023 00:00:00 UTC; path=/;"
```

In the above example, we set a cookie named "cookieName" with the value "cookieValue". We also set an expiration date for the cookie using the `expires` parameter. The `path` parameter specifies the path where the cookie is accessible.

## Deleting a Cookie

To delete a cookie, set the `expires` parameter to a date in the past. By doing this, the browser will automatically remove the cookie.

```javascript
document.cookie = "cookieName=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;"
```

In the above example, we set the `expires` parameter to a past date (January 1, 1970), effectively deleting the cookie named "cookieName". Don't forget to set the same `path` parameter that was used when creating the cookie.

## Example Function to Delete a Cookie

Here's an example function that you can use to delete a cookie in JavaScript:

```javascript
function deleteCookie(cookieName) {
  document.cookie = cookieName + "=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;";
}
```

You can call this function by passing the name of the cookie you want to delete as a parameter, like this:

```javascript
deleteCookie("cookieName");
```

## Conclusion

Deleting cookies in JavaScript is a straightforward process. By setting the `expires` parameter to a date in the past, you can effectively delete a cookie and remove it from the user's browser. Remember to set the same `path` parameter as used when creating the cookie to ensure proper deletion.

#JavaScript #Cookies