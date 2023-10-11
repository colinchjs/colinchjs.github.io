---
layout: post
title: "Creating a custom useOnlineStatus hook for checking online status"
description: " "
date: 2023-10-11
tags: []
comments: true
share: true
---

In modern web applications, it's important to keep track of the user's online status. Whether you want to provide realtime updates or display relevant content based on their connectivity, having a reliable way to check online status is crucial. In this blog post, we will learn how to create a custom `useOnlineStatus` hook using React.

## Table of Contents
- [Introduction](#introduction)
- [Creating the Hook](#creating-the-hook)
- [Usage](#usage)
- [Conclusion](#conclusion)

## Introduction

The `Navigator.onLine` property in the browser provides information about the user's connectivity. It returns `true` if the user is online and `false` if offline. To make it easier to use this functionality in our React components, we can create a custom hook that encapsulates the logic.

## Creating the Hook

Let's start by creating a new file called `useOnlineStatus.js` and write the following code:

```javascript
import { useEffect, useState } from 'react';

const useOnlineStatus = () => {
  const [isOnline, setIsOnline] = useState(navigator.onLine);

  useEffect(() => {
    const handleOnlineStatus = () => setIsOnline(true);
    const handleOfflineStatus = () => setIsOnline(false);
    
    window.addEventListener('online', handleOnlineStatus);
    window.addEventListener('offline', handleOfflineStatus);

    return () => {
      window.removeEventListener('online', handleOnlineStatus);
      window.removeEventListener('offline', handleOfflineStatus);
    };
  }, []);

  return isOnline;
};

export default useOnlineStatus;
```

In the above code, we first import the necessary dependencies - `useEffect` and `useState` from the React library. Then, we define our `useOnlineStatus` hook. 

Inside the hook, we create a state variable `isOnline` and initialize it with the value of `navigator.onLine`. We use the `useEffect` hook to add event listeners for the `online` and `offline` events. 

When the online event fires, we set `isOnline` to `true`, and when the offline event fires, we set it to `false`. We also include cleanup logic to remove the event listeners when the component unmounts.

Finally, we return the `isOnline` state variable from the hook.

## Usage

To use our custom `useOnlineStatus` hook in a React component, we import it like any other hook:

```javascript
import React from 'react';
import useOnlineStatus from './useOnlineStatus';

const OnlineStatus = () => {
  const isOnline = useOnlineStatus();

  return (
    <div>
      <h1>Online Status: {isOnline ? 'Online' : 'Offline'}</h1>
    </div>
  );
};

export default OnlineStatus;
```

In the above code, we create a component called `OnlineStatus` that uses our custom hook. The hook returns the current online status, whether the user is online or offline. We can then use this value to render the appropriate content based on the status.

## Conclusion

In this blog post, we learned how to create a custom `useOnlineStatus` hook using React. This hook encapsulates the logic for checking the user's connectivity status and provides a simple way to use it in our components. By using this hook, we can easily adapt our application based on the user's online status, enhancing the user experience.