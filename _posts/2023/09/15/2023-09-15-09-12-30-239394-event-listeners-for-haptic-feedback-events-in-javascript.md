---
layout: post
title: "Event listeners for haptic feedback events in JavaScript"
description: " "
date: 2023-09-15
tags: [HapticFeedback]
comments: true
share: true
---

Modern web browsers offer various features to enhance user experience, and one such feature is haptic feedback. Haptic feedback provides tactile sensations to users by vibrating the device or applying a gentle rumble effect. This feedback can be triggered by events such as button clicks, notifications, or gestures.

In this blog post, we will explore how to add event listeners for haptic feedback events using JavaScript. We will utilize the **`navigator`** object's **`vibrate()`** method to provide haptic feedback to the user.

## Checking Haptic Feedback Support
Before adding event listeners, it's important to check whether the device supports haptic feedback. We can do this by verifying the presence of the **`vibrate()`** method in the **`navigator`** object.

```javascript
if ('vibrate' in navigator) {
    // Haptic feedback is supported
} else {
    // Haptic feedback is not supported
}
```

## Adding Event Listeners
To trigger haptic feedback, we can add event listeners to specific events and call the **`vibrate()`** method inside the event handler. Let's consider an example where we want to provide haptic feedback when a button with the class **`haptic-button`** is clicked.

```javascript
const button = document.querySelector('.haptic-button');

button.addEventListener('click', () => {
    navigator.vibrate(100); // Vibrate for 100 milliseconds
});
```

In the above code snippet, we select the button using **`querySelector()`** and add a click event listener to it using **`addEventListener()`**. Inside the event listener, we call the **`vibrate()`** method with the desired duration in milliseconds (100 milliseconds in this example).

## Using Different Patterns
In addition to specifying a duration in milliseconds, we can create more complex haptic feedback patterns by passing an array of durations to the **`vibrate()`** method. Each duration represents the time the device should vibrate, followed by a pause duration. For example, to create a pattern of two quick vibrations followed by a longer vibration, we can use the following code:

```javascript
navigator.vibrate([50, 100, 50]);
```

In the above code, the device will vibrate for 50 milliseconds, followed by a pause of 100 milliseconds, and then vibrate again for 50 milliseconds.

## Summary
Adding event listeners for haptic feedback events in JavaScript is a simple task that can greatly enhance the user experience of your web application. By utilizing the **`vibrate()`** method of the **`navigator`** object, we can provide tactile sensations in response to user interactions.

Remember to check for haptic feedback support before adding event listeners, and experiment with different vibration patterns to create more engaging experiences.

#JavaScript #HapticFeedback