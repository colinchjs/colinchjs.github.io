---
layout: post
title: "Storing form data in cookies with JavaScript"
description: " "
date: 2023-09-24
tags: [JavaScript, Cookies]
comments: true
share: true
---

In web development, it is common to store form data in order to remember user input or preferences. One of the methods to achieve this is by using cookies. Cookies are small pieces of data that are stored on the user's browser and sent back to the server with each subsequent request. In this blog post, we will explore how to store form data in cookies using JavaScript.

## Creating HTML Form

First, let's create a simple HTML form to collect user data. For demonstration purposes, we will create a form with fields for name and email.

```html
<form id="myForm">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
  
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
  
    <button type="submit">Submit</button>
</form>
```

## Storing Form Data in Cookies

To store form data in cookies, we can use JavaScript to listen for the form submission event and then retrieve the form values. We can then set the values as cookies using `document.cookie`.

```javascript
document.getElementById("myForm").addEventListener("submit", function(event) {
    event.preventDefault();

    var name = document.getElementById("name").value;
    var email = document.getElementById("email").value;

    // Set cookies with form data
    document.cookie = "name=" + encodeURIComponent(name) + ";path=/";
    document.cookie = "email=" + encodeURIComponent(email) + ";path=/";
  
    // Optionally, provide an expiration date for the cookies
    var expirationDate = new Date();
    expirationDate.setFullYear(expirationDate.getFullYear() + 1);
    document.cookie = "name=" + encodeURIComponent(name) + ";expires=" + expirationDate.toUTCString() + ";path=/";
    document.cookie = "email=" + encodeURIComponent(email) + ";expires=" + expirationDate.toUTCString() + ";path=/";

    // Redirect to a thank you page
    window.location.href = "thank-you.html";
});
```

In the code above, we first prevent the default form submission behavior using `preventDefault()`. We then retrieve the values of the name and email fields using `getElementById`. 

Next, we set the cookies using `document.cookie`. We use `encodeURIComponent()` to ensure that the values are properly encoded. The `path=/` parameter ensures that the cookie is valid for all pages within the domain.

Optionally, we can set an expiration date for the cookies using `expires` parameter. In this example, we set the expiration date to one year from the current date.

Finally, we redirect the user to a thank you page using `window.location.href`.

## Retrieving Stored Form Data

To retrieve the stored form data from cookies, we can use JavaScript to read the cookies and populate the form fields.

```javascript
var storedName = getCookie("name");
var storedEmail = getCookie("email");

if (storedName && storedEmail) {
    document.getElementById("name").value = decodeURIComponent(storedName);
    document.getElementById("email").value = decodeURIComponent(storedEmail);
}

// Helper function to get specific cookies
function getCookie(name) {
    var cookieName = name + "=";
    var cookies = document.cookie.split(';');
  
    for (var i = 0; i < cookies.length; i++) {
        var cookie = cookies[i].trim();
      
        if (cookie.indexOf(cookieName) === 0) {
            return cookie.substring(cookieName.length, cookie.length);
        }
    }
  
    return null;
}
```

In the code above, we define a helper function `getCookie` that takes a cookie name as a parameter and returns the corresponding cookie value.

We retrieve the values of "name" and "email" cookies and decode them using `decodeURIComponent`. If the cookies exist, we set the values of the form fields using `getElementById` and `value` property.

By using this method, we can store form data in cookies and later retrieve it to pre-populate the form fields, providing a personalized experience for the users.

#JavaScript #Cookies