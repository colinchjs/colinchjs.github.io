---
layout: post
title: "Implementing a cryptocurrency tracker with suspense in React"
description: " "
date: 2023-10-16
tags: [reactsuspense]
comments: true
share: true
---

In this blog post, we will learn how to build a simple cryptocurrency tracker app using React's suspense feature. Suspense allows us to suspend rendering in our app until some asynchronous task, such as fetching data, is completed.

## Table of Contents
- [Introduction](#introduction)
- [Setting up the project](#setting-up-the-project)
- [Fetch cryptocurrency data](#fetch-cryptocurrency-data)
- [Displaying the data](#displaying-the-data)
- [Handling errors](#handling-errors)
- [Conclusion](#conclusion)

## Introduction

Cryptocurrency markets are known for their volatility and real-time price fluctuations. A cryptocurrency tracker app can help us keep track of the latest price changes of various digital currencies. In this tutorial, we will build a React app that fetches and displays cryptocurrency data.

## Setting up the project

First, let's set up a new React project using Create React App. Open your terminal and run the following command:

```bash
npx create-react-app crypto-tracker
```

Once the project is created, navigate into the project directory:

```bash
cd crypto-tracker
```

## Fetch cryptocurrency data

To fetch cryptocurrency data, we will use an external API. There are many APIs available, but for this tutorial, we will use CoinGecko API. CoinGecko provides a free API that gives us access to various cryptocurrency data.

To use the API, we need to make an asynchronous request to retrieve the data. We can use the `fetch` function provided by the browser to do this. Let's create a new file called `api.js` inside the `src` directory and add the following code:

```javascript
export async function fetchCryptocurrencyData() {
  const response = await fetch('https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=10&page=1&sparkline=true');
  const data = await response.json();
  return data;
}
```

In the above code, we define an async function `fetchCryptocurrencyData` that uses `fetch` to make a GET request to the CoinGecko API. The API URL is specified with the required parameters to get the top 10 cryptocurrencies based on market capitalization.

## Displaying the data

Now that we have the cryptocurrency data, let's display it in our app. We will create a new component called `CryptoTracker` inside `src/App.js` as follows:

```javascript
import React, { Suspense } from 'react';
import { fetchCryptocurrencyData } from './api';

const CryptoTracker = () => {
  const data = fetchCryptocurrencyData();

  if (!data) {
    return <div>Loading...</div>;
  }

  return (
    <div>
      <h1>Cryptocurrency Tracker</h1>
      {data.map((crypto) => (
        <div key={crypto.id}>
          <h3>{crypto.name}</h3>
          <p>Price: {crypto.current_price}</p>
          <p>Market Cap: {crypto.market_cap}</p>
        </div>
      ))}
    </div>
  );
};

const App = () => (
  <Suspense fallback={<div>Loading...</div>}>
    <CryptoTracker />
  </Suspense>
);

export default App;
```

In the above code, we import the `fetchCryptocurrencyData` function we created earlier and call it in the `CryptoTracker` component. We use an `if` statement to handle the case when the data is still loading. Once the data is available, we map over it to display the cryptocurrency name, price, and market cap.

We wrap the `CryptoTracker` component with `Suspense` and provide a fallback UI to be shown while the data is loading.

## Handling errors

It's also important to handle errors in case the API request fails. Let's update the `CryptoTracker` component to handle errors gracefully:

```javascript
const CryptoTracker = () => {
  const data = fetchCryptocurrencyData();

  if (!data) {
    return <div>Loading...</div>;
  }

  if (data.error) {
    return <div>Error: {data.error}</div>;
  }

  return (
    // ...
  );
};
```

In the updated code, we add an additional `if` statement to check if the response includes an `error` property. If an error occurs, we display an error message in the UI.

## Conclusion

In this tutorial, we have learned how to implement a cryptocurrency tracker app using React's suspense feature. With suspense, we can easily handle asynchronous tasks and provide a better user experience. We fetch cryptocurrency data using an API, display it in our app, and handle potential errors.

By applying the concepts learned here, you can enhance the app further by adding features such as search functionality, charts, and more. Happy coding!

# References
- [React Documentation](https://reactjs.org/docs/react-api.html#reactsuspense)
- [CoinGecko API Documentation](https://www.coingecko.com/api/documentation)