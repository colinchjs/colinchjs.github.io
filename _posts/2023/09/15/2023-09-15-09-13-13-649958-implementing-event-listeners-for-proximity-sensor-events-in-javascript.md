---
layout: post
title: "Implementing event listeners for proximity sensor events in JavaScript"
description: " "
date: 2023-09-15
tags: [JavaScript, ProximitySensor, EventListeners]
comments: true
share: true
---

In modern smartphones and tablets, proximity sensors are widely used to detect when an object is near the device. This technology is commonly used to control actions like turning off the screen during phone calls or triggering gestures in various applications. In this blog post, we will explore how to implement event listeners for proximity sensor events in JavaScript.

## Setting up the proximity sensor

Before we can listen to proximity sensor events, we need to access the sensor using the `Sensor` interface available in the web platform. We can use the `Sensor.requestPermission()` method to request permission from the user to access the proximity sensor. Let's look at the code:

```javascript
if ('permissions' in navigator) {
  navigator.permissions.query({ name: 'proximity' })
    .then(permissionStatus => {
      if (permissionStatus.state === 'granted') {
        setupProximitySensor();
      } else if (permissionStatus.state === 'prompt') {
        permissionStatus.onchange = () => {
          if (permissionStatus.state === 'granted') {
            setupProximitySensor();
          }
        };
      }
    })
    .catch(error => {
      console.error('Could not retrieve proximity sensor permission:', error);
    });
} else {
  console.error('Proximity sensor permissions not supported in this browser.');
}

function setupProximitySensor() {
  const proximitySensor = new ProximitySensor();

  proximitySensor.addEventListener('reading', event => {
    const isNear = event.near;
    // Perform actions based on proximity status
    if (isNear) {
      // Object is near the device
    } else {
      // Object is far from the device
    }
  });

  proximitySensor.start();
}
```

In the above code, we check if the device supports proximity sensor permissions by checking if the `permissions` object is available in the `navigator` API. We then request proximity sensor permission using `navigator.permissions.query()`. If the permission is granted, we proceed to set up the proximity sensor in the `setupProximitySensor` function. If the permission state is `prompt`, we set the `onchange` event of the permission status, so that when the user grants permission, we can proceed with setting up the proximity sensor.

## Handling proximity events

Once we have set up the proximity sensor, we can add an event listener for the `'reading'` event. This event gets fired whenever the proximity sensor reading changes. In the event handler, we can access the `event.near` property to check if an object is near or far from the device. Based on this information, we can perform different actions or trigger specific behaviors in our application.

## Conclusion

Implementing event listeners for proximity sensor events in JavaScript allows us to create immersive and interactive experiences on devices that support this technology. By using the `Sensor` interface and the `'reading'` event, we can easily detect changes in the proximity status of the device and perform actions accordingly.

Make sure to follow best practices when working with sensors and permissions. Always handle cases where proximity sensor permissions are not available or denied by the user. Additionally, consider the implications of accessing and monitoring user interaction with device sensors for privacy and security purposes.

#JavaScript #ProximitySensor #EventListeners