---
layout: post
title: "Creating a custom useGeolocation hook for getting device's geolocation"
description: " "
date: 2023-10-11
tags: [using, conclusion]
comments: true
share: true
---

In this tutorial, we will learn how to create a custom React hook called `useGeolocation` that allows us to easily access the device's geolocation. This will enable us to retrieve the latitude and longitude coordinates of the user's device.

## Table of Contents
- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Creating the useGeolocation Hook](#creating-the-usegeolocation-hook)
- [Using the useGeolocation Hook](#using-the-usegeolocation-hook)
- [Conclusion](#conclusion)

## Introduction {#introduction}
Geolocation is a common feature used in many web applications. It allows us to determine the physical location of a device using its latitude and longitude coordinates. In this tutorial, we will create a custom React hook that encapsulates the logic for accessing the device's geolocation.

## Prerequisites {#prerequisites}
To follow along with this tutorial, you will need:
- Basic knowledge of React hooks
- A text editor or an integrated development environment (IDE)
- Node.js and npm installed on your machine

## Creating the useGeolocation Hook {#creating-the-usegeolocation-hook}

Let's start by creating a new file called `useGeolocation.js` where we will define our custom hook.

```javascript
import { useEffect, useState } from 'react';

const useGeolocation = () => {
  const [position, setPosition] = useState(null);

  useEffect(() => {
    const handleSuccess = ({ coords }) => {
      setPosition({
        latitude: coords.latitude,
        longitude: coords.longitude,
      });
    };

    const handleError = (error) => {
      console.error(error);
    };

    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(handleSuccess, handleError);
    } else {
      console.error('Geolocation is not supported by this browser.');
    }
  }, []);

  return position;
};

export default useGeolocation;
```

In the code above, we import the necessary dependencies from React. We define the `useGeolocation` hook, which initializes the `position` state variable using the `useState` hook. Inside the `useEffect` hook, we use the `navigator.geolocation` API to get the current position. If successful, we update the `position` state with the retrieved latitude and longitude coordinates.

## Using the useGeolocation Hook {#using-the-usegeolocation-hook}
Now that we have our custom hook, let's use it in a React component.

```jsx
import React from 'react';
import useGeolocation from './useGeolocation';

const GeolocationComponent = () => {
  const position = useGeolocation();

  return (
    <div>
      <h1>Device Geolocation</h1>
      {position ? (
        <p>
          Latitude: {position.latitude}<br />
          Longitude: {position.longitude}
        </p>
      ) : (
        <p>Loading geolocation...</p>
      )}
    </div>
  );
};

export default GeolocationComponent;
```

In the code above, we import our custom `useGeolocation` hook and use it in the `GeolocationComponent` component. We render the latitude and longitude coordinates if they are available, or display a loading message if they are still being fetched.

## Conclusion {#conclusion}
In this tutorial, we learned how to create a custom React hook called `useGeolocation` for easily accessing the device's geolocation. This allows us to retrieve the latitude and longitude coordinates of the user's device. By encapsulating this logic into a reusable hook, we can easily incorporate geolocation functionality into our React applications.