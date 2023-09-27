---
layout: post
title: "Building a real-time dashboard with Javascript and GraphQL subscriptions"
description: " "
date: 2023-09-27
tags: [programming, graphql]
comments: true
share: true
---

In today's digital world, real-time updates have become a necessity for modern web applications. Whether it's tracking stock prices, monitoring server health, or displaying real-time data analytics, a real-time dashboard provides users with immediate insights and enhances their overall experience.

In this blog post, we'll explore how to build a real-time dashboard using Javascript and GraphQL subscriptions. GraphQL subscriptions allow us to receive real-time updates whenever the underlying data changes, ensuring that our dashboard always remains up-to-date.

## Prerequisites

Before we dive into building our real-time dashboard, let's ensure that we have the following prerequisites:

1. **Node.js**: Make sure to have Node.js installed on your machine.
2. **GraphQL Server**: Set up a GraphQL server or use an existing one that supports subscriptions.

## Setting Up the Project

To get started, let's create a new directory for our project and initialize a new Node.js project using the following commands:

```bash
mkdir real-time-dashboard
cd real-time-dashboard
npm init -y
```

Next, we need to install the necessary dependencies:

```bash
npm install graphql graphql-subscriptions apollo-client react react-dom
```

## Creating the Dashboard

Now that our project is set up, let's start building our real-time dashboard. We'll be using React for the frontend, Apollo Client for handling GraphQL subscriptions, and  GraphQL for the server.

First, let's create the basic structure of our dashboard. In the project root directory, create a new file called `Dashboard.js` and add the following code:

```javascript
import React from "react";

const Dashboard = () => {
  return (
    <div>
      <h1>Real-Time Dashboard</h1>
      {/* Add components and logic for displaying real-time data */}
	</div>
  );
};

export default Dashboard;
```

Next, let's create a subscription to receive real-time updates from the server. In the same file, add the following code:

```javascript
import React, { useEffect } from "react";
import { useSubscription } from "@apollo/client";
import { SUBSCRIPTION_NAME } from "../graphql/subscriptions"; // Replace with your subscription name

const Dashboard = () => {

  const { data } = useSubscription(SUBSCRIPTION_NAME);

  useEffect(() => {
    if (data) {
      // Update the dashboard with the received real-time data
    }
  }, [data]);

  return (
    <div>
      <h1>Real-Time Dashboard</h1>
      {/* Add components and logic for displaying real-time data */}
	</div>
  );
};

export default Dashboard;
```

Replace `SUBSCRIPTION_NAME` with the actual name of the subscription you defined in your GraphQL server.

Lastly, let's render our dashboard component. Create a new file called `index.js` in the project root directory and add the following code:

```javascript
import React from "react";
import ReactDOM from "react-dom";
import { ApolloProvider } from "@apollo/client";
import { ApolloClient, InMemoryCache } from "@apollo/client";
import Dashboard from "./components/Dashboard";

const client = new ApolloClient({
  uri: "http://localhost:4000/graphql", // Replace with your GraphQL server endpoint
  cache: new InMemoryCache(),
});

ReactDOM.render(
  <ApolloProvider client={client}>
    <Dashboard />
  </ApolloProvider>,
  document.getElementById("root")
);
```

Replace the `uri` with the actual endpoint of your GraphQL server.

## Running the Dashboard

To run the dashboard, use the following command in your project root directory:

```bash
npm start
```

This will start the development server and open the dashboard in your browser. Any real-time updates received from the GraphQL server will be reflected on the dashboard automatically.

## Conclusion

In this blog post, we learned how to build a real-time dashboard using Javascript and GraphQL subscriptions. By incorporating real-time updates, we can create dynamic and responsive dashboards that provide users with immediate insights. Remember to tailor the code to your specific project requirements and experiment with different features and components to enhance your dashboard's functionality and appearance.

#programming #javascript #graphql #realtime #dashboard