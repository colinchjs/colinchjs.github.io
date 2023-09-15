---
layout: post
title: "Creating a todo list app with AJAX and JavaScript"
description: " "
date: 2023-09-15
tags: [javascript, AJAX]
comments: true
share: true
---

In today's fast-paced world, staying organized is crucial. A todo list app can help us keep track of tasks and ensure important items aren't overlooked. In this tutorial, we will learn how to build a simple yet powerful todo list app using AJAX and JavaScript.

## Prerequisites

Before we begin, make sure you have the following:

- Basic knowledge of HTML, CSS, and JavaScript.
- A text editor or an integrated development environment (IDE) to write code.
- An understanding of AJAX (Asynchronous JavaScript and XML).

## Setting up the Project

Let's start by setting up the basic structure of our todo list app. Create a new HTML file and add the following code:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Todo List App</title>
</head>
<body>
  <h1>Todo List App</h1>

  <input type="text" id="taskInput" placeholder="Enter a task">
  <button id="addTaskBtn">Add Task</button>

  <ul id="taskList"></ul>

  <script src="script.js"></script>
</body>
</html>
```

In the above code, we have a simple HTML structure with an input field to enter tasks, a button to add tasks, and an empty unordered list (`<ul>`) to display the tasks. We have also included a JavaScript file, `script.js`, which we will create next.

## Implementing AJAX for Task Creation

Now, let's write the JavaScript code to handle adding tasks using AJAX. Create a new file called `script.js` and add the following code:

```javascript
// Get the required HTML elements
const taskInput = document.getElementById('taskInput');
const addTaskBtn = document.getElementById('addTaskBtn');
const taskList = document.getElementById('taskList');

// Event listener for the "Add Task" button
addTaskBtn.addEventListener('click', () => {
  const task = taskInput.value;

  if (task !== '') {
    // Create a new XMLHttpRequest object
    const xhttp = new XMLHttpRequest();

    // Configure the callback for the AJAX request
    xhttp.onreadystatechange = () => {
      if (xhttp.readyState === 4 && xhttp.status === 200) {
        // Task added successfully, update the UI
        const li = document.createElement('li');
        const taskText = document.createTextNode(task);
        li.appendChild(taskText);
        taskList.appendChild(li);

        taskInput.value = ''; // Clear the input
      }
    };

    // Send the AJAX request
    xhttp.open('POST', '/api/tasks', true);
    xhttp.setRequestHeader('Content-type', 'application/json');
    xhttp.send(JSON.stringify({ task }));
  }
});
```

In the above code, we first get references to the HTML elements we need using `getElementById()`. Then, we add an event listener to the "Add Task" button so that when it is clicked, we can handle the task creation logic.

Inside the event listener, we retrieve the entered task from the input field and perform some basic validation to ensure it is not empty. If the task is valid, we create a new XMLHttpRequest object to make an AJAX request.

We configure the callback function for the AJAX request using `onreadystatechange`. When the request is completed (`readyState === 4`) and the response status is successful (`status === 200`), we update the UI by appending a new task to the task list. Finally, we clear the input field.

## Conclusion

Congratulations! You have successfully built a simple todo list app using AJAX and JavaScript. This app allows users to add tasks dynamically without reloading the page, resulting in a seamless user experience. You can enhance this app by adding additional features like task deletion and task completion status.

Remember to optimize your app for performance and stay updated with the latest techniques in front-end development to deliver the best user experience.

#javascript #AJAX #todoList #webdevelopment