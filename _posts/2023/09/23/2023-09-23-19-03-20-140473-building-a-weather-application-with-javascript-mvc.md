---
layout: post
title: "Building a weather application with JavaScript MVC"
description: " "
date: 2023-09-23
tags: [javascript, weatherapplication]
comments: true
share: true
---

In the era of modern web development, creating feature-rich applications is a common task for developers. In this blog post, we will explore how to build a weather application using JavaScript and the Model-View-Controller (MVC) architectural pattern.

## What is MVC?

MVC is a software design pattern that separates an application into three interconnected components - Model, View, and Controller. This separation helps in organizing code, enhancing maintainability, and improving code reusability.

- **Model**: The model represents the data and logic of the application. It encapsulates and manages the application's state, as well as performs operations on the data.

- **View**: The view is responsible for rendering the user interface. It displays the data from the model and provides a means for user interaction.

- **Controller**: The controller acts as an intermediary between the model and the view. It handles user inputs, manipulates the model accordingly, and updates the view accordingly.

## Setting up the Project

To get started, create a new directory for your project and navigate into it using the command line. Initialize a new Node.js project by running the command `npm init -y`.

Next, install the necessary dependencies by running `npm install express body-parser axios`. We will be using Express.js as our web server framework, Body-parser to parse request bodies, and Axios to make HTTP requests to the weather API.

## Designing the Model

In this Weather application, we need a model to handle fetching weather data from a weather API. Let's create a `WeatherModel.js` file and define our model.

```javascript
const axios = require('axios');

class WeatherModel {
  constructor() {
    this.weatherAPI = 'https://api.weatherapi.com/v1/current.json';
  }

  async getWeatherData(location) {
    try {
      const response = await axios.get(this.weatherAPI, {
        params: {
          key: 'YOUR_API_KEY',
          q: location,
        },
      });

      return response.data;
    } catch (error) {
      console.error('Error fetching weather data:', error);
      throw error;
    }
  }
}

module.exports = WeatherModel;
```

In the above code, we define a `WeatherModel` class with a `getWeatherData` method that takes a location as an input. It makes a GET request to the weather API using Axios and returns the weather data.

## Implementing the Controller

The controller will handle user inputs, make calls to the model, and update the view accordingly. Let's create a `WeatherController.js` file and define our controller.

```javascript
const WeatherModel = require('./WeatherModel');

class WeatherController {
  constructor() {
    this.model = new WeatherModel();
  }

  async getWeather(req, res) {
    const { location } = req.query;

    try {
      const weatherData = await this.model.getWeatherData(location);
      res.status(200).json(weatherData);
    } catch (error) {
      res.status(500).json({ error: 'An error occurred' });
    }
  }
}

module.exports = WeatherController;
```

In the above code, we create a `WeatherController` class with a `getWeather` method. This method takes the location from the query parameters, calls the `getWeatherData` method from the model, and sends the weather data as a JSON response.

## Building the View

The view is responsible for rendering the user interface. In this case, let's assume we're creating a simple web application that displays the weather data as a JSON response. Create an `index.html` file in your project's root directory and add the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Weather Application</title>
</head>
<body>
  <h1>Weather Application</h1>

  <form id="weatherForm">
    <input type="text" name="location" placeholder="Enter location" required>
    <button type="submit">Get Weather</button>
  </form>

  <div id="weatherData"></div>

  <script src="main.js"></script>
</body>
</html>
```

In the above code, we create a simple form to input the location and a div to display the weather data.

## Putting it All Together

Now, let's create our main server file `server.js` that will handle requests and interact with the controller.

```javascript
const express = require('express');
const bodyParser = require('body-parser');
const WeatherController = require('./WeatherController');

const app = express();
const weatherController = new WeatherController();

app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

app.get('/weather', weatherController.getWeather);

app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

In the above code, we create an Express app, initialize a `WeatherController` object, and define a route that calls the `getWeather` method of the controller when a GET request is received at `/weather`.

To run the application, execute the command `node server.js` in the project's root directory. Visit `http://localhost:3000` in your web browser and enter a location in the form. Upon form submission, the weather data will be displayed below the form.

Congratulations! You have successfully built a weather application using JavaScript and the MVC architectural pattern. Make sure to replace `'YOUR_API_KEY'` with your actual API key to fetch weather data.

#javascript #mvc #weatherapplication