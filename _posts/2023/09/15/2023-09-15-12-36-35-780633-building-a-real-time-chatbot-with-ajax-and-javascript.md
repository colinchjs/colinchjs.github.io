---
layout: post
title: "Building a real-time chatbot with AJAX and JavaScript"
description: " "
date: 2023-09-15
tags: [chat, chat]
comments: true
share: true
---

With the increasing popularity of chatbots, integrating them into web applications has become essential. In this tutorial, we will learn how to build a real-time chatbot using AJAX and JavaScript. This seamless integration will allow users to communicate with the chatbot in real-time, enhancing the user experience.

## Prerequisites

To follow along with this tutorial, beginners should have a basic understanding of HTML, CSS, and JavaScript. Additionally, you will need a text editor and a web browser.

## Setup

1. Create a new HTML page and include the necessary CSS and JavaScript files.

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="styles.css">
    <script src="script.js"></script>
</head>
<body>
    <!-- Chatbot UI goes here -->
</body>
</html>
```

2. Add the Chatbot UI structure in the `<body>` section of the HTML page.

```html
<div id="chat-container">
    <div id="chat-header">
        <h3>Chatbot</h3>
    </div>
    <div id="chat-messages">
        <!-- Messages will be dynamically added here -->
    </div>
    <div id="chat-input">
        <input id="user-input" type="text" placeholder="Type your message">
        <button id="send-button">Send</button>
    </div>
</div>
```

## Fetching Messages from the Chatbot

To get responses from the chatbot, we will use AJAX to send asynchronous requests to the server.

1. Add the following JavaScript code inside the `<script>` tag:

```javascript
document.getElementById('send-button').addEventListener('click', sendMessage);

function sendMessage() {
    const userInput = document.getElementById('user-input').value;
    if (userInput !== '') {
        displayMessage(userInput, 'user');
        fetchChatbotResponse(userInput);
        document.getElementById('user-input').value = '';
    }
}

function displayMessage(message, sender) {
    const chatMessages = document.getElementById('chat-messages');
    const messageDiv = document.createElement('div');
    messageDiv.className = sender;
    messageDiv.innerText = message;
    chatMessages.appendChild(messageDiv);
}

function fetchChatbotResponse(userInput) {
    const url = `https://api.chatbot.com/getresponse?message=${userInput}`;
    fetch(url)
        .then(response => response.json())
        .then(data => {
            const chatbotResponse = data.response;
            displayMessage(chatbotResponse, 'chatbot');
        })
        .catch(error => {
            console.error('An error occurred:', error);
            displayMessage('Oops, something went wrong!', 'chatbot');
        });
}
```

2. Replace the URL `https://api.chatbot.com/getresponse` with the actual API endpoint that provides the chatbot responses.

## Styling the Chatbot UI

To enhance the chatbot experience, we can apply some basic CSS styles.

1. Create a CSS file called `styles.css` and add the following styles:

```css
#chat-container {
    max-width: 400px;
    margin: 0 auto;
    border: 1px solid #ccc;
    border-radius: 5px;
}

#chat-header {
    background-color: #f2f2f2;
    padding: 10px;
}

#chat-messages {
    padding: 10px;
    max-height: 300px;
    overflow-y: scroll;
}

#chat-messages div {
    margin-bottom: 10px;
}

#chat-container input[type="text"] {
    width: 70%;
    padding: 5px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

#chat-container button {
    padding: 5px 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
```

2. Link the CSS file in the head section of the HTML page.

```html
<link rel="stylesheet" href="styles.css">
```

## Conclusion

By following this tutorial, you have learned how to build a real-time chatbot using AJAX and JavaScript. Users can now seamlessly communicate with the chatbot within your web application. Remember to replace the placeholder API endpoint with your actual chatbot's API endpoint. Implement additional features and enhancements based on your specific requirements.

#chatbot #AJAX