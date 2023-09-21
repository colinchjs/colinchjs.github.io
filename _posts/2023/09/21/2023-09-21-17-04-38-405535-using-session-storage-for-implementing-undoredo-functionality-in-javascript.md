---
layout: post
title: "Using session storage for implementing undo/redo functionality in JavaScript"
description: " "
date: 2023-09-21
tags: [undo, redo]
comments: true
share: true
---

Have you ever needed to implement undo and redo functionality in your JavaScript application? It can be quite challenging to keep track of all the changes and allow the user to revert them. One efficient approach is to use session storage to store the state of the application at each step. In this article, we'll explore how to leverage session storage to implement undo and redo functionality in JavaScript.

## What is Session Storage?

Session storage is a web storage API that allows us to store key-value pairs in the browser. The stored data is available only for the duration of the user's session and is cleared once they close the browser. Unlike local storage, session storage is isolated to the specific tab or window, meaning that data stored in one tab is not accessible in another.

## Setting Up the Environment

To get started, create a new HTML file and add the following code:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Undo/Redo Example</title>
</head>
<body>
  <button id="undoButton">Undo</button>
  <button id="redoButton">Redo</button>
  <div id="output"></div>

  <script src="script.js"></script>
</body>
</html>
```

Next, create a new JavaScript file called `script.js` in the same directory and add the following code:

```javascript
const undoButton = document.getElementById('undoButton');
const redoButton = document.getElementById('redoButton');
const outputDiv = document.getElementById('output');

const MAX_STATES = 10;
let currentState = 0;

function updateOutput(value) {
  outputDiv.innerText = value;
}

function saveState(state) {
  sessionStorage.setItem(`state_${currentState}`, state);
  currentState++;
}

function undo() {
  if (currentState > 0) {
    currentState--;
    const state = sessionStorage.getItem(`state_${currentState}`);
    updateOutput(state);
  }
}

function redo() {
  if (currentState < sessionStorage.length && currentState < MAX_STATES) {
    const state = sessionStorage.getItem(`state_${currentState}`);
    updateOutput(state);
    currentState++;
  }
}

undoButton.addEventListener('click', undo);
redoButton.addEventListener('click', redo);

// Example usage
saveState("Initial state");
saveState("State after first change");
saveState("State after second change");
```

## How It Works

In the HTML code, we have two buttons, an output div, and a script tag that links to our JavaScript file. The JavaScript code retrieves the necessary elements using `getElementById` and sets up event listeners for the undo and redo buttons.

The `saveState` function takes the current state as an argument and stores it in session storage with a unique key, `state_<current_state>`. We increment the `currentState` variable after each save.

The `undo` function checks if there are any previous states available. If so, it gets the previous state from session storage and updates the output.

The `redo` function checks if there are any future states available. If so, it retrieves the next state from session storage and updates the output.

## Adding Undo/Redo Functionality

To add undo and redo functionality to your application, you need to call the `saveState` function whenever there is a significant change to the application state. For example, if you have an input field and the user updates its value, you can save the state in the `input` event listener:

```javascript
const inputField = document.getElementById('myInput');
inputField.addEventListener('input', function() {
  const newState = inputField.value;
  saveState(newState);
});
```

By saving every state change in session storage, you can easily revert to previous states using the undo button and go forward using the redo button.

## Conclusion

Using session storage to implement undo/redo functionality in JavaScript provides a straightforward and efficient way to track and revert application state changes. By leveraging the session storage API, you can give your users the ability to undo and redo actions with ease.

#undo #redo