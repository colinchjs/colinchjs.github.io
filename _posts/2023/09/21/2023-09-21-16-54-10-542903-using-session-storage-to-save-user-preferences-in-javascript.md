---
layout: post
title: "Using session storage to save user preferences in JavaScript"
description: " "
date: 2023-09-21
tags: []
comments: true
share: true
---

When building web applications, it's common to allow users to customize their experience by setting preferences such as theme, language, or font size. One way to save these preferences is by using session storage in JavaScript.

## What is Session Storage?

Session storage is a web storage API supported by modern browsers that provides a way to store data for the duration of a user's session. It is similar to local storage but has a few key differences. While local storage persists even after the browser is closed, session storage is cleared once the user closes the browser tab or window.

## Storing User Preferences

To save user preferences using session storage, we can follow these steps:

### 1. Creating a Preference Object

First, we need to create an object that will hold all the user preferences. For example:

```javascript
let preferences = {
  theme: 'light',
  language: 'en',
  fontSize: 'medium'
};
```

### 2. Saving Preferences to Session Storage

To save the preferences object to the session storage, we can use the `setItem` method, which takes a key-value pair as arguments. We need to convert the object to a string using `JSON.stringify` before saving it:

```javascript
sessionStorage.setItem('preferences', JSON.stringify(preferences));
```

### 3. Retrieving Preferences from Session Storage

To retrieve the preferences from session storage, we can use the `getItem` method, which takes the key as an argument. We need to parse the string back to an object using `JSON.parse`:

```javascript
let savedPreferences = JSON.parse(sessionStorage.getItem('preferences'));
```

### 4. Updating Preferences

If the user decides to change their preferences, we can update the values in the `preferences` object and save it again to session storage. The old preferences will be replaced with the updated ones.

### 5. Removing Preferences

To remove the preferences from session storage, we can use the `removeItem` method, which takes the key as an argument:

```javascript
sessionStorage.removeItem('preferences');
```

## Usage Example

Here's an example of how to use session storage to save and retrieve user preferences:

```javascript
// Saving preferences
let preferences = {
  theme: 'dark',
  language: 'fr',
  fontSize: 'large'
};

sessionStorage.setItem('preferences', JSON.stringify(preferences));

// Retrieving preferences
let savedPreferences = JSON.parse(sessionStorage.getItem('preferences'));

console.log(savedPreferences);
// Output: { theme: 'dark', language: 'fr', fontSize: 'large' }

// Updating preferences
preferences.theme = 'light';
preferences.fontSize = 'medium';

sessionStorage.setItem('preferences', JSON.stringify(preferences));

console.log(JSON.parse(sessionStorage.getItem('preferences')));
// Output: { theme: 'light', language: 'fr', fontSize: 'medium' }

// Removing preferences
sessionStorage.removeItem('preferences');
```

## Conclusion

By using session storage, we can easily store and retrieve user preferences in JavaScript. Remember that session storage is cleared when the user closes the browser tab or window, so it's best suited for temporary data during a session.