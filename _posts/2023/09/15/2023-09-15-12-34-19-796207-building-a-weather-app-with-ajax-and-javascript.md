---
layout: post
title: "Building a weather app with AJAX and JavaScript"
description: " "
date: 2023-09-15
tags: [weatherapp, javascript]
comments: true
share: true
---

In this blog post, we will walk you through the process of building a weather app using AJAX and JavaScript. We'll be using AJAX to fetch weather data from a third-party API, and JavaScript to handle the data and display it in our app.

## Getting Started

To begin with, let's start by setting up the HTML structure for our weather app. Create an HTML file and add the necessary elements such as input fields, buttons, and placeholders for displaying the weather information.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Weather App</title>
</head>
<body>
  <h1>Weather App</h1>
  
  <input type="text" id="cityInput" placeholder="Enter city name" />
  <button id="getWeatherBtn">Get Weather</button>
  
  <div id="weatherInfo"></div>

  <script src="script.js"></script>
</body>
</html>
```

Next, let's move on to writing the JavaScript code. Create a new JavaScript file and link it to your HTML file using the `<script>` tag.

## Fetching Weather Data with AJAX

First, we need to fetch the weather data from a third-party API. Let's use the OpenWeatherMap API for this example. To make an AJAX request, we'll use the `fetch()` function.

```javascript
const getWeatherData = () => {
  const apiKey = 'YOUR_API_KEY';
  const city = document.getElementById('cityInput').value;
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}`;

  fetch(url)
    .then(response => response.json())
    .then(data => showWeather(data))
    .catch(error => console.log(error));
};
```

In the `getWeatherData` function, we retrieve the API key and the city name entered by the user. We then construct the URL with the appropriate endpoint and parameters. The `fetch()` function sends a GET request to the API and returns a Promise. We handle the response and convert it to JSON format using the `.json()` method.

## Displaying Weather Information

Now that we have the weather data, let's create a function to display it on our app. We'll update the `showWeather` function to interact with our HTML elements.

```javascript
const showWeather = (weatherData) => {
  const weatherInfo = document.getElementById('weatherInfo');
  
  const { name, weather, main } = weatherData;
  const { description } = weather[0];
  const { temp, humidity } = main;

  weatherInfo.innerHTML = `
    <h2>${name}</h2>
    <p>${description}</p>
    <p>Temperature: ${temp}°C</p>
    <p>Humidity: ${humidity}%</p>
  `;
};
```

In the `showWeather` function, we extract the necessary information from the `weatherData` object and update the `weatherInfo` HTML element with the relevant weather information.

## Adding Event Listeners

The final step is to add an event listener to the "Get Weather" button in order to trigger the AJAX request and display the weather information.

```javascript
const getWeatherBtn = document.getElementById('getWeatherBtn');

getWeatherBtn.addEventListener('click', () => {
  getWeatherData();
});
```

## Conclusion

By following the steps outlined in this blog post, you should now have a basic understanding of how to build a weather app using AJAX and JavaScript. Feel free to enhance and customize the app further, such as adding additional weather data or improving the app's UI.

Remember to replace `'YOUR_API_KEY'` with your actual OpenWeatherMap API key to ensure that the app works correctly.

#weatherapp #javascript