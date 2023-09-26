---
layout: post
title: "Cookie-based language translation in JavaScript"
description: " "
date: 2023-09-24
tags: [code]
comments: true
share: true
---

Language translation is an essential feature for websites to cater to users from different regions and languages. In this blog post, we'll explore how to implement cookie-based language translation in JavaScript.

## Why Cookie-based Translation?

There are several ways to implement language translation on a website, such as URL parameters, HTML attributes, or using server-side techniques. However, using cookies allows us to persist the user's chosen language preference across different pages and sessions.

## Implementation Steps

### Step 1: Setup Language Options

First, we need to define the available language options that users can choose from. Let's consider a simple example with two options: English (default) and French.

```javascript
const languages = {
  en: "English",
  fr: "French"
};
```

### Step 2: Handle Language Selection

Next, we'll create a function that handles the user's language selection. This function will set a cookie with the selected language and reload the page to apply the changes.

```javascript
function setLanguage(lang) {
  document.cookie = `language=${lang}; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=/`;
  location.reload();
}
```

### Step 3: Get the Current Language

To retrieve the user's chosen language, we'll create a function that reads the language cookie and returns the corresponding value.

```javascript
function getLanguage() {
  const cookies = document.cookie.split("; ");
  for (let i = 0; i < cookies.length; i++) {
    const [name, value] = cookies[i].split("=");
    if (name === "language") {
      return value;
    }
  }
  return null;
}
```

### Step 4: Translate Content

Finally, we'll create a translation function that takes a key and returns the translated content based on the user's selected language.

```javascript
function translate(key) {
  const lang = getLanguage();
  if (lang === "fr") {
    switch (key) {
      case "hello":
        return "Bonjour";
      case "bye":
        return "Au revoir";
      // Add more translations as needed
    }
  }
  // Default to English translations
  switch (key) {
    case "hello":
      return "Hello";
    case "bye":
      return "Goodbye";
    // Add more translations as needed
  }
}
```

## Usage Examples

Now, let's see how we can use these functions to implement cookie-based language translation on our website.

```javascript
// Get the current language
const currentLanguage = getLanguage();

// Display a translated greeting
const greetingElement = document.getElementById("greeting");
greetingElement.textContent = translate("hello") + " World!";

// Handle language selection
const languageSelect = document.getElementById("language-select");
languageSelect.value = currentLanguage;
languageSelect.addEventListener("change", function () {
  setLanguage(this.value);
});
```

## Conclusion

By implementing cookie-based language translation in JavaScript, we can provide a seamless experience for users to browse the website in their preferred language. Remember to optimize your translation texts and consider SEO aspects while implementing multilingual functionality on your website.

#code #javascript