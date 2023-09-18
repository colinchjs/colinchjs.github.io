---
layout: post
title: "Implementing a reactive form validation using JavaScript Proxy"
description: " "
date: 2023-09-18
tags: [webdevelopment, javascript]
comments: true
share: true
---

Form validation is an essential aspect of web development, ensuring that user inputs meet specific criteria before being processed. With the rise of JavaScript frameworks and libraries, developers have started adopting reactive programming approaches to handle form validation efficiently.

One popular method of implementing reactive form validation is by using JavaScript Proxies. A proxy is an object that intercepts operations performed on another object, allowing us to define custom behavior for various operations. In the context of form validation, we can use a proxy to observe and react to changes in form inputs in a declarative manner.

## Setting up the HTML

Let's start by setting up a simple HTML form that we'll use for demonstration purposes:

```html
<form id="myForm">
  <input name="username" type="text" placeholder="Username">
  <span id="username-error" style="color: red"></span>
  
  <input name="password" type="password" placeholder="Password">
  <span id="password-error" style="color: red"></span>
  
  <button type="submit">Submit</button>
</form>
```

We have two input fields, one for the username and one for the password. Each input field is accompanied by a corresponding `<span>` element that will display an error message if the validation fails.

## Writing the JavaScript Code

Now let's write the JavaScript code to create a reactive form validation using proxies:

```javascript
const form = document.getElementById('myForm');

const validationRules = {
  username: {
    required: true,
    minLength: 4,
    maxLength: 20
  },
  password: {
    required: true,
    minLength: 6
  }
};

const validationMessages = {
  username: {
    required: 'Username is required',
    minLength: 'Username must be at least 4 characters long',
    maxLength: 'Username cannot exceed 20 characters'
  },
  password: {
    required: 'Password is required',
    minLength: 'Password must be at least 6 characters long'
  }
};

const formProxy = new Proxy({}, {
  set(target, key, value) {
    target[key] = value;
    validateForm();
    return true;
  }
});

function validateForm() {
  const errors = {};

  for (const fieldName in validationRules) {
    const rules = validationRules[fieldName];
    const value = formProxy[fieldName];

    for (const ruleName in rules) {
      const ruleValue = rules[ruleName];

      if (ruleName === 'required' && !value) {
        errors[fieldName] = validationMessages[fieldName].required;
      } else if (ruleName === 'minLength' && value.length < ruleValue) {
        errors[fieldName] = validationMessages[fieldName].minLength;
      } else if (ruleName === 'maxLength' && value.length > ruleValue) {
        errors[fieldName] = validationMessages[fieldName].maxLength;
      }
    }
  }

  displayErrors(errors);
}

function displayErrors(errors) {
  for (const fieldName in validationMessages) {
    const errorMessage = errors[fieldName];
    const errorElement = document.getElementById(`${fieldName}-error`);

    if (errorMessage) {
      errorElement.textContent = errorMessage;
    } else {
      errorElement.textContent = '';
    }
  }
}

// Attach the formProxy to the form inputs
Array.from(form.elements).forEach(element => {
  if (element.nodeName === 'INPUT') {
    element.addEventListener('input', (event) => formProxy[element.name] = event.target.value);
  }
});

// Submit event listener
form.addEventListener('submit', (event) => {
  event.preventDefault();
  
  // Check if there are no errors
  if (Object.keys(displayErrors).length === 0) {
    // Submit the form
    form.submit();
  }
});
```

## How it Works

The code defines `validationRules` and `validationMessages` objects that specify the validation rules and corresponding error messages for each form field. 

The `formProxy` is created using the JavaScript `Proxy` class, which intercepts the setting of form inputs' values. Whenever a form input's value changes, the `set` method of the proxy is triggered, which sets the new value and calls the `validateForm` function.

The `validateForm` function iterates through each form field, checks the validation rules, and stores any errors in the `errors` object. The `displayErrors` function then updates the error messages in the HTML based on the `errors` object.

Finally, event listeners are attached to the form inputs to listen for changes and update the `formProxy` accordingly. When the form is submitted, the `submit` event is intercepted, and if there are no validation errors, the form is submitted.

By using JavaScript Proxies, we've implemented a reactive form validation system that automatically updates and displays errors as the user interacts with the form.

#webdevelopment #javascript