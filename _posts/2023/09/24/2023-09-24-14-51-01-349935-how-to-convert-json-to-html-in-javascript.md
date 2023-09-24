---
layout: post
title: "How to convert JSON to HTML in JavaScript."
description: " "
date: 2023-09-24
tags: [JavaScript, JSON]
comments: true
share: true
---
title: How to Convert JSON to HTML in JavaScript
date: 2021-10-01
tags: JavaScript, JSON, HTML
---

In this tutorial, we'll explore how to convert JSON data to HTML using JavaScript. Converting JSON to HTML can be useful when you want to display structured data in a user-friendly format on a website.

## Prerequisites

Before we dive into the code, make sure you have a basic understanding of JavaScript, HTML, and JSON.

## Convert JSON to HTML

To convert JSON to HTML in JavaScript, you can follow these steps:

1. Get the JSON data either from an API response or by reading it from a local file.

```javascript
const jsonData = {
  "name": "John Doe",
  "age": 25,
  "email": "john.doe@example.com"
};
```

2. Create an HTML template that will hold the converted JSON data.

```html
<div id="jsonContainer"></div>
```

3. Write JavaScript code to convert the JSON data into HTML.

```javascript
const jsonContainer = document.getElementById("jsonContainer");

function convertJsonToHtml(json) {
  let html = "";

  for (let key in json) {
    html += `<strong>${key}:</strong> ${json[key]}<br>`;
  }

  return html;
}

jsonContainer.innerHTML = convertJsonToHtml(jsonData);
```

In the above code, we define the `convertJsonToHtml` function, which takes the JSON data as input. This function iterates over each key in the JSON object and generates HTML code by concatenating the key-value pairs.

4. Finally, update the HTML container's content with the converted HTML.

```html
<div id="jsonContainer">
  <strong>name:</strong> John Doe<br>
  <strong>age:</strong> 25<br>
  <strong>email:</strong> john.doe@example.com<br>
</div>
```

By executing the code, the JSON data will be converted into HTML and injected into the `jsonContainer` div element.

## Conclusion

Converting JSON to HTML in JavaScript allows you to display structured data in a more readable and presentable format on your website. With the steps outlined in this tutorial, you can easily convert JSON data into HTML using JavaScript.

Remember to make sure that the JSON data is properly formatted and the HTML template is updated accordingly to meet your specific requirements.

```javascript
#JavaScript #JSON #HTML
```