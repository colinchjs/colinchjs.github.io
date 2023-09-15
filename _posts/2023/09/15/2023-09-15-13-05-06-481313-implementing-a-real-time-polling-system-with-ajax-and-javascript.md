---
layout: post
title: "Implementing a real-time polling system with AJAX and JavaScript"
description: " "
date: 2023-09-15
tags: [programming, webdevelopment]
comments: true
share: true
---

In this tutorial, we will learn how to create a real-time polling system using AJAX and JavaScript. This polling system will allow users to vote on a question and see the live results without refreshing the page.

## Prerequisites

To follow along with this tutorial, you will need:

- Basic knowledge of HTML, CSS, and JavaScript.
- A code editor of your choice.
- A web server to run the code locally (e.g., Apache, Nginx).

## Setting up the Project

1. Create a new HTML file called `index.html` and add the following code:
```html
<!DOCTYPE html>
<html>
<head>
  <title>Real-time Polling System</title>
</head>
<body>
  <h1>Real-time Polling System</h1>
  <div id="poll"></div>

  <script src="script.js"></script>
</body>
</html>
```
2. Create a new JavaScript file called `script.js` and add the following code:
```javascript
window.onload = function() {
  // TODO: Implement the AJAX polling logic here
};
```

## Implementing the Polling Logic

Inside the `window.onload` function in `script.js`, we will implement the AJAX polling logic to fetch the poll results from the server and update the UI.

```javascript
window.onload = function() {
  function getPollResults() {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", "poll_results.php", true);
    xhr.onreadystatechange = function() {
      if (xhr.readyState === 4 && xhr.status === 200) {
        const pollData = JSON.parse(xhr.responseText);
        updateUI(pollData);
      }
    };
    xhr.send();
  }

  function updateUI(pollData) {
    const pollElement = document.getElementById("poll");
    pollElement.innerHTML = "";

    for (let option in pollData.options) {
      if (pollData.options.hasOwnProperty(option)) {
        const percentage = (pollData.totalVotes === 0) ? 0 : Math.round((pollData.options[option] / pollData.totalVotes) * 100);
        const optionElement = document.createElement("div");
        optionElement.innerHTML = `${option}: ${percentage}% (${pollData.options[option]} votes)`;

        pollElement.appendChild(optionElement);
      }
    }
  }

  // Poll the server every 5 seconds
  setInterval(getPollResults, 5000);
};
```

In this code, `getPollResults` is a function that sends an AJAX GET request to the server (in this example, `poll_results.php`). When the response is received, the `updateUI` function is called to update the poll results.

The `updateUI` function dynamically updates the HTML by creating div elements for each poll option and displaying the percentage and vote count.

Finally, we use `setInterval` to call `getPollResults` every 5 seconds, thus creating a real-time polling experience.

## Conclusion

Congratulations! You have successfully implemented a real-time polling system using AJAX and JavaScript. Users can now vote on a question and see the live results without refreshing the page. Experiment with different polling intervals and explore ways to customize the UI to enhance the user experience.

#programming #webdevelopment