---
layout: post
title: "How to fetch and display JSON data from an API in JavaScript."
description: " "
date: 2023-09-24
tags: [JavaScript]
comments: true
share: true
---

In modern web development, it is quite common to fetch data from an API and display it on a web page. JavaScript provides a built-in `fetch()` function that allows us to make HTTP requests and retrieve data in JSON format. In this tutorial, we will learn how to fetch and display JSON data from an API using JavaScript.

## Step 1: Fetching Data using `fetch()`

To fetch data from an API, we can use the `fetch()` function. This function takes a URL as an argument and returns a promise that resolves to the response object. We can then use this response object to extract the JSON data.

Here's an example of how to fetch JSON data using `fetch()`:

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    // Do something with the data
  })
  .catch(error => {
    console.log('Error:', error);
  });
```

In the code snippet above, we call the `fetch()` function with the API URL. We use the `then()` method to parse the response data as JSON using the `response.json()` method. We then chain another `then()` method to access the parsed JSON data and perform operations on it. Finally, we use the `catch()` method to handle any errors that may occur during the fetch.

## Step 2: Displaying the JSON Data

Once we have retrieved the JSON data, we can display it on our web page. One of the simplest ways to display the data is by manipulating the HTML DOM.

Here's an example of how to dynamically create HTML elements and display the JSON data:

```javascript
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => {
    const container = document.getElementById('data-container');

    data.forEach(item => {
      const element = document.createElement('div');
      element.textContent = item.name;
      container.appendChild(element);
    });
  })
  .catch(error => {
    console.log('Error:', error);
  });
```

In the code snippet above, we create a container element with the `id` of `data-container` in our HTML file. We then use `document.getElementById()` to select the container element. Inside the second `then()` method, we iterate over the JSON data using `forEach()` and create a new `<div>` element for each item. We set the text content of each `<div>` element to the `name` property of the item, and then append the elements to the container.

## Conclusion

Fetching and displaying JSON data from an API in JavaScript is a fundamental skill for web developers. By using the `fetch()` function and manipulating the DOM, we can easily retrieve data from an API and display it on a web page. This allows us to create dynamic and interactive websites that provide real-time data to users.

#JavaScript #API