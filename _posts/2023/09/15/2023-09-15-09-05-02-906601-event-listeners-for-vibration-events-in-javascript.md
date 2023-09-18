---
layout: post
title: "Event listeners for vibration events in JavaScript"
description: " "
date: 2023-09-15
tags: [VibrationAPI]
comments: true
share: true
---

In modern web development, we can make use of various APIs to enhance the user experience of our websites and applications. One such API is the Vibration API, which allows us to control the vibration feature of a device. By using event listeners, we can respond to specific vibration events and trigger actions accordingly.

To get started, we first need to check if the Vibration API is supported by the user's browser using the `navigator` object. We can do this by checking if the `vibrate` property is present:

```javascript
if ('vibrate' in navigator) {
  // Vibration API is supported
  // Set up event listeners...
} else {
  // Vibration API is not supported
  // Take appropriate action or show an error message
}
```

Once we determine that the Vibration API is supported, we can proceed with setting up the event listeners. There are two main events we can listen for:

## 1. Vibration Start Event

The `vibrationstart` event is triggered when the vibration begins. We can listen for this event using the `addEventListener` method:

```javascript
navigator.vibrate.addEventListener('vibrationstart', function() {
  // Do something when vibration starts
});
```

Within the event handler function, we can define the actions we want to take when the vibration starts.

## 2. Vibration End Event

The `vibrationend` event is triggered when the vibration stops. We can listen for this event using the `addEventListener` method as well:

```javascript
navigator.vibrate.addEventListener('vibrationend', function() {
  // Do something when vibration ends
});
```

Similarly, within the event handler function, we can define the actions we want to take when the vibration stops.

Keep in mind that both `vibrationstart` and `vibrationend` events are not supported in all browsers. It's important to test for browser compatibility before relying on them.

Now that we have set up the event listeners, we can easily add custom behavior to our web projects when the vibration starts or ends. Whether it's providing haptic feedback or creating interactive experiences, the Vibration API and event listeners give us the flexibility to deliver a more engaging user experience.

**#JavaScript #VibrationAPI**