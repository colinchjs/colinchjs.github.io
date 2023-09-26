---
layout: post
title: "Cookie attributes and their usage in JavaScript"
description: " "
date: 2023-09-24
tags: [Cookies]
comments: true
share: true
---

Cookies are small pieces of data that are stored in a user's web browser by websites they visit. They are commonly used to store user preferences, session data, and other information that can be accessed across multiple pages or visits to a website. In JavaScript, cookies can be created, modified, and read using the `document.cookie` property.

## Setting Cookie Attributes

When creating a cookie in JavaScript, you can specify various attributes to control its behavior. These attributes are added as key-value pairs to the cookie string. Here are some commonly used attributes:

### 1. **Name and Value**:

The name and value specify the data you want to store in the cookie. The syntax is `name=value`. For example, `document.cookie = "username=johndoe"`.

### 2. **Expires**:

The `expires` attribute sets the expiration date for the cookie. By default, cookies are stored until the browser session ends. To set a specific expiration date, provide a date string in the format `expires=date`. For example, `document.cookie = "username=johndoe; expires=Thu, 31 Dec 2022 23:59:59 GMT"`.

### 3. **Domain**:

The `domain` attribute specifies the domain of the website to which the cookie belongs. By default, cookies are associated with the current domain. To set it explicitly, use the `domain` attribute. For example, `document.cookie = "username=johndoe; domain=example.com"`.

### 4. **Path**:

The `path` attribute defines the path within the domain where the cookie is accessible. By default, cookies are available for the entire domain. To restrict a cookie to a specific path, use the `path` attribute. For example, `document.cookie = "username=johndoe; path=/admin"`.

### 5. **Secure**:

The `secure` attribute ensures that the cookie is only transmitted over a secure HTTPS connection. To secure a cookie, include the `Secure` attribute. For example, `document.cookie = "username=johndoe; secure"`.

## Reading and Modifying Cookie Values

To read a cookie value in JavaScript, you can access the `document.cookie` property. The `document.cookie` string contains all the cookies stored by the website as a single string. You can parse it to retrieve specific values.

```javascript
const cookies = document.cookie.split("; ");
for (let i = 0; i < cookies.length; i++) {
  const cookie = cookies[i].split("=");
  const name = cookie[0];
  const value = cookie[1];
  // Access the cookie data here
}
```

To modify a cookie, you simply create a new cookie with the same name and update its value, along with any other attributes that need to be changed.

```javascript
document.cookie = "username=newvalue; expires=Thu, 31 Dec 2022 23:59:59 GMT";
```

## Conclusion

Cookie attributes play a crucial role in controlling the behavior of cookies in JavaScript. By setting the appropriate attributes, you can manage the expiration, accessibility, and security of cookies. Understanding these attributes allows you to store and retrieve user-specific data effectively. #JavaScript #Cookies