---
layout: post
title: "Building a task management application with JavaScript MVC"
description: " "
date: 2023-09-23
tags: [taskmanagement]
comments: true
share: true
---

Task management is an essential aspect of staying organized and productive in both personal and professional settings. By building a task management application with JavaScript and the Model-View-Controller (MVC) architecture, you can create a flexible and scalable solution to handle task tracking efficiently.

## Prerequisites

Before diving into building the application, ensure that you have:

- Basic knowledge of HTML, CSS, and JavaScript.
- Familiarity with MVC architecture and its concepts.

## Setting up the Project

To begin, create a new directory for your project and initialize a new JavaScript project using npm:

```
$ mkdir task-management-app
$ cd task-management-app
$ npm init -y
```

Next, install the necessary packages:

```bash
$ npm install express --save
$ npm install body-parser --save
```

## Creating the MVC Structure

To follow the MVC pattern, we need to separate the application into three distinct components:

1. **Model**: Handles data storage and manipulation.
2. **View**: Renders the user interface based on the data received from the model.
3. **Controller**: Handles user interactions and updates the model and view accordingly.

Create the following directory structure within your project folder:

```
- /controllers
    - tasksController.js
- /models
    - taskModel.js
- /views
    - index.html
```

## Implementing the Model

In the **taskModel.js** file, we define the data structure for the tasks and implement methods to handle task manipulation. Here is an example implementation:

```javascript
// taskModel.js
class TaskModel {
    constructor() {
        this.tasks = [];
    }

    getAllTasks() {
        return this.tasks;
    }

    addTask(task) {
        this.tasks.push(task);
    }

    removeTask(taskId) {
        this.tasks = this.tasks.filter(task => task.id !== taskId);
    }
}

module.exports = TaskModel;
```

## Implementing the View

In the **index.html** file, we create the user interface for the task management application. Use HTML, CSS, and JavaScript to structure and style the elements. Here's a basic example:

```html
<!-- index.html -->
<!DOCTYPE html>
<html>
<head>
    <!-- Add necessary CSS and scripts -->
    <link rel="stylesheet" href="styles.css">
    <script src="scripts.js"></script>
</head>
<body>
    <!-- Task list container -->
    <div id="task-list">
        <ul id="tasks">
            <!-- Dynamically populated tasks will be added here -->
        </ul>

        <!-- Task input form -->
        <form id="task-form">
            <input type="text" id="task-input" placeholder="Add a new task" required>
            <button type="submit">Add Task</button>
        </form>
    </div>
</body>
</html>
```

## Implementing the Controller

The **tasksController.js** file will contain the logic for handling user interactions and updating the model and view accordingly. Here is an example implementation using Express.js:

```javascript
// tasksController.js
const express = require('express');
const bodyParser = require('body-parser');
const TaskModel = require('../models/taskModel');

const app = express();
app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

const taskModel = new TaskModel();

// API endpoint to get all tasks
app.get('/api/tasks', (req, res) => {
    const tasks = taskModel.getAllTasks();
    res.json(tasks);
});

// API endpoint to add a new task
app.post('/api/tasks', (req, res) => {
    const { title } = req.body;
    const task = { id: Date.now(), title };
    taskModel.addTask(task);
    res.json(task);
});

// API endpoint to remove a task
app.delete('/api/tasks/:id', (req, res) => {
    const taskId = parseInt(req.params.id);
    taskModel.removeTask(taskId);
    res.sendStatus(200);
});

app.listen(3000, () => {
    console.log('Task Management App is running on port 3000');
});
```

## Running the Application

To start the application, run the following command:

```bash
$ node controllers/tasksController.js
```

Visit http://localhost:3000 in your browser to see the task management application in action.

## Conclusion

By following the MVC architecture, you have created a task management application using JavaScript. This application allows users to add, remove, and view tasks, enhancing productivity and organization. The separation of concerns provided by the MVC pattern allows for modular and maintainable code, making it easier to add new features in the future.

#javascript #mvc #taskmanagement