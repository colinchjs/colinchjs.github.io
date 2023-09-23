---
layout: post
title: "Implementing a cookie-based login system in JavaScript"
description: " "
date: 2023-09-24
tags: [JavaScript, Authentication]
comments: true
share: true
---

In this tutorial, we will learn how to implement a cookie-based login system in JavaScript. This type of authentication allows users to stay logged in even if they close the browser and reopen it later. We will be using JavaScript and cookies to authenticate users and manage their login sessions.

## Prerequisites
Before we get started, make sure you have the following prerequisites:

1. Basic knowledge of JavaScript.
2. An understanding of HTTP cookies.

## Steps

### Step 1: Create the Login Form
First, let's create a basic login form in HTML. Open your editor and add the following code:

```html
<form id="loginForm">
  <label for="username">Username:</label>
  <input type="text" id="username" name="username" required>

  <label for="password">Password:</label>
  <input type="password" id="password" name="password" required>

  <button type="submit">Log In</button>
</form>
```

### Step 2: Handle Form Submission
Next, we need to handle the form submission using JavaScript. Add the following script after the form:

```javascript
document.getElementById('loginForm').addEventListener('submit', function (event) {
  event.preventDefault(); // prevent default form submission

  var username = document.getElementById('username').value;
  var password = document.getElementById('password').value;

  // Perform authentication check here
  if (username === 'admin' && password === 'password') {
    // Set cookie with logged-in user information
    document.cookie = 'loggedIn=true; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=/';

    // Redirect user to home page
    window.location.href = '/home';
  } else {
    alert('Invalid username or password');
  }
});
```

### Step 3: Validate Session on Page Load
To check if the user is logged in when they revisit the site, we need to validate the session. Add the following function to your script:

```javascript
function validateSession() {
  var loggedIn = (document.cookie.indexOf('loggedIn=true') !== -1);

  if (!loggedIn) {
    // Redirect user to login page
    window.location.href = '/login';
  }
}

// Call the function on page load
validateSession();
```

### Step 4: Implement Logout Functionality
Lastly, let's implement a logout functionality. Add the following script to your code:

```javascript
function logout() {
  // Clear the cookie
  document.cookie = 'loggedIn=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/';

  // Redirect user to login page
  window.location.href = '/login';
}
```

And don't forget to add a logout button in your HTML:

```html
<button onclick="logout()">Log Out</button>
```

## Conclusion
In this tutorial, we learned how to implement a cookie-based login system in JavaScript. By storing a cookie on the user's browser, we were able to maintain their login session even if they closed the browser. This approach provides a seamless and convenient user experience.

#JavaScript #Authentication