---
layout: post
title: "Creating an MVC application with Express.js and a templating engine like EJS or Pug"
description: " "
date: 2023-09-17
tags: [ExpressJS]
comments: true
share: true
---

Express.js is a powerful web application framework for Node.js that allows you to build robust and scalable web applications. One common architectural pattern used with Express.js is the Model-View-Controller (MVC) pattern. In this blog post, we will explore how to create an MVC application using Express.js and a templating engine like EJS or Pug.

## What is MVC?

MVC is a software architectural pattern that separates an application into three interconnected components:

- **Model**: Represents the data and business logic of the application.
- **View**: Renders the data and presents it to the user.
- **Controller**: Handles user inputs, interacts with the model, and updates the view accordingly.

By using the MVC pattern, you can better organize your code, improve code maintainability, and achieve separation of concerns.

## Setting Up the Project

To get started, make sure you have Node.js installed on your machine. Create a new directory for your project and navigate to it in your terminal.

Initialize a new Node.js project by running the following command:

```
npm init -y
```

Next, install the necessary dependencies:

```
npm install express <templating-engine>
```

Replace `<templating-engine>` with either `ejs` or `pug`, depending on your preference. These templating engines allow you to dynamically render HTML pages by injecting data into templates.

## Folder Structure

To follow MVC principles, create the following folder structure:

```
- controllers/
  - indexController.js
- models/
  - indexModel.js
- views/
  - index.ejs (or index.pug)
- app.js
```

- The `controllers` folder will contain your controller files, responsible for handling user requests and interacting with the model and view.
- The `models` folder will hold your model files, responsible for managing data and business logic.
- The `views` folder will store your template files, representing the user interface.
- The `app.js` file acts as the entry point of your application.

## Implementing the MVC Pattern

1. In `app.js`, require the necessary dependencies and set up Express.js:

```javascript
const express = require('express');
const app = express();
const indexController = require('./controllers/indexController');

// Set up middleware and configuration

// Define routes

app.listen(3000, () => {
  console.log('Server running on port 3000');
});
```
2. In `indexModel.js`, define your model:

```javascript
const indexModel = {
  getData: () => {
    // Fetch data from a database or API
    // Perform any necessary data manipulations
    // Return the processed data
    return data;
  },
};

module.exports = indexModel;
```

3. In `indexController.js`, implement your controller:

```javascript
const indexModel = require('../models/indexModel');

const indexController = {
  getIndex: (req, res) => {
    const data = indexModel.getData();

    res.render('index', { data });
  },
};

module.exports = indexController;
```

4. In the `views` folder, create an `index.ejs` (or `index.pug`) file. This file will serve as your template:

```ejs
<!DOCTYPE html>
<html>
  <head>
    <title>MVC Application</title>
  </head>
  <body>
    <h1>Welcome to the MVC Application</h1>
    <p>Data: <%= data %></p>
  </body>
</html>
```

5. Define the route in `app.js` to connect the controller to the view:

```javascript
app.get('/', indexController.getIndex);
```

## Conclusion

By following the MVC pattern, you can create scalable and maintainable Express.js applications. The model handles the data and business logic, the view renders the data to the user, and the controller handles the interaction between the model and view. With the help of a templating engine like EJS or Pug, you can dynamically generate HTML pages based on the data. Start building your own MVC application with Express.js and a templating engine today!

#ExpressJS #MVC