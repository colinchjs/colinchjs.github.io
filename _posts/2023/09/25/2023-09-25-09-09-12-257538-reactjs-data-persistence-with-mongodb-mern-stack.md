---
layout: post
title: "React.js data persistence with MongoDB (MERN stack)"
description: " "
date: 2023-09-25
tags: [reactjs, mongodb]
comments: true
share: true
---

In this blog post, we will explore how to implement data persistence in a React.js application using MongoDB as the database. We will be building a MERN (MongoDB, Express.js, React.js, Node.js) stack application.

## Setting up the project

To begin, make sure you have Node.js and MongoDB installed on your machine. Then, create a new directory for your project and navigate to it in the terminal.

```bash
$ mkdir mern-data-persistence
$ cd mern-data-persistence
```

Next, let's set up the backend of our application using Express.js and MongoDB. Create a `server` directory and initialize a new Node.js project inside it.

```bash
$ mkdir server
$ cd server
$ npm init -y
```

Install the required dependencies: `express`, `mongoose`, and `cors`.

```bash
$ npm install express mongoose cors
```

Now, let's create a `server.js` file inside the `server` directory and configure it as follows:

```javascript
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
const port = 3000;

app.use(cors());
app.use(express.json());

// Connect to MongoDB
mongoose.connect('mongodb://localhost:27017/mern', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => {
    console.log('Connected to MongoDB');
    app.listen(port, () => {
      console.log(`Server is running on port ${port}`);
    });
  })
  .catch((err) => {
    console.error('Failed to connect to MongoDB:', err);
  });
```

In the above code, we are setting up the Express.js server, enabling CORS to allow cross-origin requests, and connecting to the MongoDB database.

## Implementing the frontend with React.js

Now let's move on to the frontend of our application. Create a new `client` directory inside the root directory and initialize a new React.js project inside it.

```bash
$ mkdir client
$ cd client
$ npx create-react-app .
```

Install the required dependencies: `axios`, `react-router-dom`.

```bash
$ npm install axios react-router-dom
```

To keep things simple, let's create a basic React component called `TodoForm` to handle the form submission and sending data to the server. Create a new file `TodoForm.js` inside the `src` directory and add the following code:

```javascript
import React, { useState } from 'react';
import axios from 'axios';

const TodoForm = () => {
  const [todo, setTodo] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    
    axios.post('http://localhost:3000/todos', { todo })
      .then((res) => {
        console.log(res.data);
        setTodo('');
      })
      .catch((err) => {
        console.error('Error:', err);
      });
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={todo}
        onChange={(e) => setTodo(e.target.value)}
      />
      <button type="submit">Add Todo</button>
    </form>
  );
};

export default TodoForm;
```

In the code above, we create a simple form component with an input field for the user to enter a todo item. On form submission, we make a POST request to the backend API endpoint `/todos` with the todo item as the request body.

## Conclusion

In this blog post, we learned how to implement data persistence in a React.js application using MongoDB in the MERN stack. We set up the backend server using Express.js and MongoDB, and implemented a basic form component in React.js to send data to the server.

By implementing data persistence, we can now store and retrieve data from the MongoDB database, allowing our application to have persistent state across sessions. This opens up possibilities for building more complex applications that rely on data storage and retrieval.

#reactjs #mongodb #mern #data-persistence #web-development