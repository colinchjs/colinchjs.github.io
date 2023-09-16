---
layout: post
title: "Building microservices with Express.js and a service registry like Consul"
description: " "
date: 2023-09-17
tags: [ExpressJS, Consul, Microservices, ServiceRegistry, ServiceDiscovery]
comments: true
share: true
---

Microservices architecture has gained significant popularity due to its ability to break down large monolithic applications into smaller, independent services. These services can be independently developed, deployed, and scaled, making the development process more efficient and flexible.

One crucial aspect of microservices architecture is service discovery and registration. When working with a distributed system of microservices, it's essential to have a reliable service registry that allows services to discover and communicate with each other.

In this blog post, we will explore how to build microservices using Express.js, a popular Node.js framework, and Consul, a service registry and discovery tool.

## What is Express.js?

Express.js is a minimal and flexible web application framework for Node.js. It provides a simple and intuitive programming model to build web applications and APIs. With its middleware approach, Express enables developers to handle requests and responses, define routes, and implement custom logic easily.

## What is Consul?

Consul is a powerful service registry and discovery tool developed by HashiCorp. It provides a centralized way to register and discover various services in a distributed system. Consul ensures that services can find each other dynamically without hardcoded configurations, making it a perfect fit for microservices architecture.

## Setting up a Microservice with Express.js

To begin, let's create a simple microservice with Express.js. Assuming you have Node.js and npm already installed, follow these steps to set up a new Express project:

1. Create a new directory for your microservice and navigate to it in your terminal.
2. Run `npm init` to initialize a new Node.js project and follow the prompts to generate a `package.json` file.
3. Install Express.js by running `npm install express`.
4. Create an `index.js` file and add the following code:

```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, microservice!');
});

app.listen(3000, () => {
  console.log('Microservice is running on port 3000');
});
```

5. Start the microservice by running `node index.js`. You should see the message "Microservice is running on port 3000" in the terminal.
6. Open your browser and visit `http://localhost:3000`. You should see the message "Hello, microservice!" displayed.

Congratulations! You have successfully set up a basic microservice using Express.js.

## Registering Microservices with Consul

Now that we have our microservice up and running, let's integrate Consul for service registration and discovery. Follow these steps to get started:

1. Install Consul by visiting https://www.consul.io/downloads and downloading the appropriate version for your operating system.
2. Start the Consul agent by running `consul agent -dev` in your terminal.
3. Install the `consul` npm package in your Express.js project by running `npm install consul`.
4. Update the `index.js` file with the following code:

```javascript
const express = require('express');
const app = express();
const Consul = require('consul');

const consul = new Consul();

app.get('/', (req, res) => {
  res.send('Hello, microservice!');
});

app.listen(3000, () => {
  // Register microservice with Consul
  consul.agent.service.register({
    name: 'microservice',
    address: 'localhost',
    port: 3000,
    check: {
      http: 'http://localhost:3000',
      interval: '5s',
      timeout: '1s',
    },
    tags: ['nodejs', 'express'],
  }, () => {
    console.log('Microservice is running and registered with Consul');
  });
});
```

In the updated code, we import the `consul` package and create a new instance of the `Consul` class. Then, we register our microservice with Consul using the `consul.agent.service.register` method. We provide the necessary details like name, address, port, and check parameters to ensure Consul can monitor the health of our microservice.

5. Restart your microservice by stopping the running node process and running `node index.js` again.
6. Open your browser and visit `http://localhost:3000`. The microservice should be running as before.
7. To verify that the microservice is registered with Consul, open your browser and visit `http://localhost:8500`. You should see the Consul web interface where you can explore and discover your registered services.

## Discovering Microservices with Consul

Now that our microservice is registered with Consul, let's see how to discover and communicate with it. Follow these steps:

1. Create another Express.js microservice following the same steps as before.
2. In the new microservice, update the route to fetch data from the registered microservice:

```javascript
app.get('/', (req, res) => {
  const microserviceUrl = 'http://localhost:3000'; // Update with your microservice's URL
  fetch(microserviceUrl)
    .then(response => response.text())
    .then(data => {
      res.send(`Fetched data from microservice: ${data}`);
    })
    .catch(error => {
      res.send('Failed to fetch data from microservice');
    });
});
```

In this code, we use the `fetch` function to make an HTTP request to the registered microservice URL. The response is then sent back to the client.

3. Register the new microservice with Consul following the same steps as before.
4. Start both microservices and visit the new microservice URL (`http://localhost:3001`). You should see the response fetched from the registered microservice.

By leveraging Consul's service discovery capabilities, we can easily discover and communicate with microservices in a distributed system.

## Conclusion

In this blog post, we learned how to build microservices using Express.js and integrate Consul as a service registry. With Express.js, we created a basic microservice, and by leveraging Consul, we registered and discovered our microservices dynamically.

Using tools like Express.js and Consul, developers can embrace the benefits of microservices architecture, enabling them to build scalable and resilient applications.

#ExpressJS #Consul #Microservices #ServiceRegistry #ServiceDiscovery