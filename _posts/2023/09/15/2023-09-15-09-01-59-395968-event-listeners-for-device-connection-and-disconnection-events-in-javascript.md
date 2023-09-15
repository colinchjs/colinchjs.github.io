---
layout: post
title: "Event listeners for device connection and disconnection events in JavaScript"
description: " "
date: 2023-09-15
tags: [JavaScript, EventListeners]
comments: true
share: true
---

In JavaScript, you can use event listeners to detect when a device is connected or disconnected from the user's system. This can be useful when you want to perform specific actions based on the presence or absence of a particular device, such as a USB drive or a Bluetooth device.

To listen for these events, you can utilize the `navigator.usb` and `navigator.bluetooth` APIs, which provide access to the USB and Bluetooth devices connected to the user's system.

## Listening for USB Device Connection and Disconnection Events

To listen for USB device connection and disconnection events, you can use the `navigator.usb.onconnect` and `navigator.usb.ondisconnect` event listeners. Here's an example:

```javascript
navigator.usb.addEventListener('connect', (event) => {
  const device = event.device;
  console.log(`USB device connected: ${device.productName}`);
});

navigator.usb.addEventListener('disconnect', (event) => {
  const device = event.device;
  console.log(`USB device disconnected: ${device.productName}`);
});
```

In the above code, we are adding event listeners for the `connect` and `disconnect` events of the USB API. When a device is connected, the `connect` event is triggered and the connected device information can be accessed from the `event.device` property. Similarly, when a device is disconnected, the `disconnect` event is triggered.

## Listening for Bluetooth Device Connection and Disconnection Events

For Bluetooth device connection and disconnection events, you can use the `navigator.bluetooth.addEventListener` function to register event listeners. Here's an example:

```javascript
navigator.bluetooth.addEventListener('deviceconnected', (event) => {
  const device = event.device;
  console.log(`Bluetooth device connected: ${device.name}`);
});

navigator.bluetooth.addEventListener('devicedisconnected', (event) => {
  const device = event.device;
  console.log(`Bluetooth device disconnected: ${device.name}`);
});
```

In the above code, we are registering event listeners for the `deviceconnected` and `devicedisconnected` events of the Bluetooth API. The connected or disconnected device information can be accessed from the `event.device` property.

## Conclusion

By using event listeners in JavaScript, you can easily detect when a device is connected or disconnected from the user's system. Whether you are working with USB or Bluetooth devices, these APIs provide a convenient way to listen for these events and perform specific actions based on their occurrence.

#JavaScript #EventListeners