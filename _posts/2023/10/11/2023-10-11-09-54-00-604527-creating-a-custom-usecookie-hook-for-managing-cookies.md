---
layout: post
title: "Creating a custom useCookie hook for managing cookies"
description: " "
date: 2023-10-11
tags: [react, cookies]
comments: true
share: true
---

Managing cookies in a web application is a common task, and it can become repetitive and error-prone if done manually every time. To simplify the process, we can create a custom `useCookie` hook that provides an easy way to set, retrieve, and delete cookies. In this blog post, we will go through the steps of creating this custom hook using React.

## Table of Contents
- [Introduction](#introduction)
- [Setting up the Project](#setting-up-the-project)
- [Creating the useCookie Hook](#creating-the-usecookie-hook)
- [Using the useCookie Hook](#using-the-usecookie-hook)
- [Conclusion](#conclusion)

## Introduction

Cookies are small pieces of data stored on the client-side by the browser. They can be used to store user-specific information, track user behavior, or personalize the user experience. In a React application, managing cookies can be done using the JavaScript `document.cookie` API, but it can quickly become complex and repetitive.

To simplify the process, we will create a custom `useCookie` hook that abstracts away the complexities of working with cookies and provides a clean and intuitive API for setting, retrieving, and deleting cookies.

## Setting up the Project

Before we start creating the `useCookie` hook, let's set up a basic React project using `create-react-app`:

```bash
npx create-react-app cookie-manager
cd cookie-manager
```

Next, open the project in your favorite code editor and create a new file called `useCookie.js` in the `src` directory.

## Creating the useCookie Hook

In the `useCookie.js` file, let's start by importing React and creating a custom hook called `useCookie`:

```jsx
import { useState } from 'react';

const useCookie = () => {
  const [cookie, setCookie] = useState('');

  // TODO: Add functionality for setting, retrieving, and deleting cookies

  return {
    cookie,
    setCookie,
  };
};

export default useCookie;
```

Next, we need to add the functionality for setting, retrieving, and deleting cookies. Here's an example implementation:

```jsx
import { useState, useEffect } from 'react';

const useCookie = (cookieName) => {
  const [cookie, setCookie] = useState('');

  const getCookie = () => {
    const cookies = document.cookie.split(';');
    for (let i = 0; i < cookies.length; i++) {
      const [name, value] = cookies[i].split('=');
      if (name.trim() === cookieName) {
        return decodeURIComponent(value);
      }
    }
    return '';
  };

  const setCookie = (value) => {
    const encodedValue = encodeURIComponent(value);
    document.cookie = `${cookieName}=${encodedValue}; path=/`;
  };

  const deleteCookie = () => {
    document.cookie = `${cookieName}=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;`;
  };

  useEffect(() => {
    setCookie(getCookie());
  }, []);

  return {
    cookie,
    setCookie,
    deleteCookie,
  };
};

export default useCookie;
```
In this implementation, we split the `document.cookie` string into individual cookies and iterate through them to find the specific cookie we are interested in. When setting a cookie, we encode the value and set it using the `document.cookie` API. To delete a cookie, we set its expiration date to a past date.

Note that the `useEffect` hook is used to set the initial state of the cookie when the component using the `useCookie` hook mounts.

## Using the useCookie Hook

Now that we have our `useCookie` hook, let's see how we can use it in a component. 

```jsx
import React from 'react';
import useCookie from './useCookie';

const App = () => {
  const { cookie, setCookie, deleteCookie } = useCookie('myCookie');

  const handleSetCookie = () => {
    setCookie('Hello, World!');
  };

  const handleDeleteCookie = () => {
    deleteCookie();
  };

  return (
    <div>
      <p>Cookie Value: {cookie}</p>
      <button onClick={handleSetCookie}>Set Cookie</button>
      <button onClick={handleDeleteCookie}>Delete Cookie</button>
    </div>
  );
};

export default App;
```

In this example, we import our `useCookie` hook and use it within the `App` component. We pass the name of the cookie we want to work with ('myCookie') to the hook and destructure the `cookie`, `setCookie`, and `deleteCookie` functions from the hook's return value.

We then render the current value of the cookie and provide two buttons to set or delete the cookie.

## Conclusion

In this blog post, we went through the process of creating a custom `useCookie` hook for managing cookies in a React application. By abstracting away the complexities of working with cookies, this hook provides an easy and intuitive way to set, retrieve, and delete cookies.

Using this custom hook saves time and reduces code duplication, making the management of cookies in a web application much more efficient and error-free. Feel free to extend or modify the `useCookie` hook to fit your specific needs and use cases.

#react #cookies