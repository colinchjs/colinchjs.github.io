---
layout: post
title: "Using AJAX to fetch and display data from a blockchain in JavaScript"
description: " "
date: 2023-09-15
tags: [blockchain, javascript]
comments: true
share: true
---

## Introduction

Blockchain technology has gained significant popularity in recent years, and developers are finding innovative ways to integrate it into their applications. One of the common use cases is fetching and displaying data from a blockchain in real-time.

In this blog post, we will explore how to use AJAX in JavaScript to fetch data from a blockchain and display it on a web page.

## Prerequisites

To follow along with this tutorial, you should have a basic understanding of JavaScript and AJAX. Additionally, you will need access to a blockchain API that allows fetching data.

## Step 1: Setting Up the HTML Structure

Start by creating an HTML file and setting up the basic structure. In this example, we will have a simple `<div>` element to display the fetched data.

```html
<!DOCTYPE html>
<html>
<head>
    <title>Fetching Data from a Blockchain</title>
</head>
<body>
    <div id="dataContainer"></div>

    <script src="script.js"></script>
</body>
</html>
```

## Step 2: Writing the JavaScript Code

Next, create a JavaScript file called `script.js` and include it in the HTML file using the `<script>` tag. This is where we will write our AJAX code.

```javascript
// Fetch data from blockchain API
function fetchData() {
    var xhr = new XMLHttpRequest();

    xhr.onreadystatechange = function() {
        if (xhr.readyState === 4 && xhr.status === 200) {
            var data = JSON.parse(xhr.responseText);
            displayData(data);
        }
    }

    xhr.open("GET", "https://blockchain-api.example.com/data", true);
    xhr.send();
}

// Display fetched data in the HTML
function displayData(data) {
    var container = document.getElementById("dataContainer");
    container.innerHTML = "<pre>" + JSON.stringify(data, null, 2) + "</pre>";
}

// Call the fetchData function to initiate the AJAX request
fetchData();
```

In this code snippet, we define a `fetchData()` function that makes an AJAX request to the blockchain API. Once we receive a successful response, we use the `displayData()` function to update the HTML element with the fetched data.

## Step 3: Testing the Code

Save both the HTML and JavaScript files in the same folder and open the HTML file in a web browser. The JavaScript code will be executed, and the fetched data from the blockchain API will be displayed inside the `<div>` element with the id "dataContainer".

## Conclusion

Using AJAX in JavaScript, we can easily fetch data from a blockchain API and display it on a web page. This allows developers to create dynamic applications that can display real-time data from the blockchain.

Remember to replace `"https://blockchain-api.example.com/data"` with the actual URL of the blockchain API you are using.

#blockchain #javascript