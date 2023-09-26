---
layout: post
title: "Building a photo gallery with JavaScript MVC"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

In today's digital world, photo galleries have become an essential feature for many websites. Whether you're showcasing your own photography skills or highlighting products, a visually appealing and user-friendly photo gallery can greatly enhance the user experience. In this blog post, we will explore how to build a photo gallery using the JavaScript Model-View-Controller (MVC) architecture.

## What is MVC?

MVC is a software architectural pattern that separates an application into three interconnected components: the Model, the View, and the Controller. This pattern promotes a clean separation of concerns, making it easier to maintain, modify, and test your code.

- The **Model** is responsible for representing the data and business logic of your application. It interacts with the backend server or data source to retrieve and update information.

- The **View** is responsible for rendering the user interface and displaying the data to the user. It handles user interactions and communicates with the controller to update the model when necessary.

- The **Controller** acts as the intermediary between the model and the view. It handles user inputs, updates the model accordingly, and ensures that the view is updated to reflect the changes.

## Setting Up the Project

To start building our photo gallery, we need to set up a basic project structure. Create a new directory for your project and initialize it as a JavaScript project using your preferred package manager. For this example, we will use NPM.

1. Open a terminal and navigate to the project directory.
2. Run the following command to initialize the project:

```bash
npm init -y
```

This command will generate a `package.json` file, which will track our project dependencies and configuration.

3. Install the necessary dependencies by running the following command:

```bash
npm install express body-parser ejs --save
```

Here, we are installing Express, Body-parser, and EJS. Express is a popular Node.js framework for building web applications, Body-parser allows us to parse incoming requests, and EJS is a templating language for generating dynamic HTML.

## Creating the Model

In our photo gallery, the model will represent the photos and their associated data. Let's create a `Photo` class that will serve as our model's blueprint.

```javascript
class Photo {
    constructor(id, name, description, imageUrl) {
        this.id = id;
        this.name = name;
        this.description = description;
        this.imageUrl = imageUrl;
    }
}
```

Here, the `Photo` class has four properties: `id`, `name`, `description`, and `imageUrl`. Feel free to add more properties based on your requirements.

## Building the View

Now that we have our model, let's move on to building the view. For the purpose of this example, we will use the EJS templating language to generate dynamic HTML views.

1. Create a new directory called `views` in the root of your project.
2. Inside the `views` directory, create a new file called `gallery.ejs`. This file will serve as our main photo gallery view.

In the `gallery.ejs` file, add the following code:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Photo Gallery</title>
</head>
<body>
    <h1>Photo Gallery</h1>

    <div id="photo-container">
        <% photos.forEach(function(photo) { %>
            <div class="photo">
                <h2><%= photo.name %></h2>
                <img src="<%= photo.imageUrl %>" alt="<%= photo.name %>">
                <p><%= photo.description %></p>
            </div>
        <% }) %>
    </div>
</body>
</html>
```

Here, we are using EJS's templating syntax to loop through an array of `photos` and display the name, image, and description for each photo.

## Implementing the Controller

The controller will handle the logic behind fetching the data from the model and rendering it in the view. Let's create a new file called `controller.js` in the root of your project and add the following code:

```javascript
const express = require('express');
const app = express();

const photos = [
    new Photo(1, "Photo 1", "Description 1", "https://example.com/photo1.jpg"),
    new Photo(2, "Photo 2", "Description 2", "https://example.com/photo2.jpg"),
    new Photo(3, "Photo 3", "Description 3", "https://example.com/photo3.jpg")
];

app.set('view engine', 'ejs');

app.get('/', (req, res) => {
    res.render('gallery', { photos });
});

app.listen(3000, () => {
    console.log('Server is running on http://localhost:3000');
});
```

Here, we are using Express to set up a basic server and routing. The controller defines a route for the root URL and renders the `gallery` view, passing the `photos` array as a parameter.

## Running the Photo Gallery

To run the photo gallery locally, follow these steps:

1. Open a terminal and navigate to the project directory.
2. Run the following command to start the server:

```bash
node controller.js
```

3. Open a web browser and visit `http://localhost:3000`. You should see the photo gallery with the sample photos displayed.

Congratulations! You have successfully built a photo gallery using JavaScript MVC. From here, you can enhance this application by adding features like photo filtering, sorting, and pagination. Explore more MVC concepts and JavaScript frameworks like React or Angular to take your photo gallery to the next level.

#javascript #MVC