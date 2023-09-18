---
layout: post
title: "Implementing dynamic form validation with ternary operators in Vue.js"
description: " "
date: 2023-09-19
tags: [vuejs, formvalidation]
comments: true
share: true
---

Form validation is an essential aspect of any modern web application. With Vue.js, a popular JavaScript framework, you can easily implement dynamic form validation to ensure that user input meets the desired criteria.

In this blog post, we will explore how to use ternary operators in Vue.js to create dynamic form validation. This approach allows us to conditionally display error messages based on the validity of each form field.

## Setting Up the Vue.js Project

Before we dive into form validation, let's set up a basic Vue.js project. You can use the Vue CLI to create a new project with the following command:

```bash
vue create dynamic-form-validation
```

Once the project is created, navigate to its directory:

```bash
cd dynamic-form-validation
```

## Creating the Form Component

Create a new file called `Form.vue` in the `src/components` directory and add the following code:

```html
<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <div>
        <label for="email">Email:</label>
        <input type="text" id="email" v-model="email" />
        <span v-if="showEmailError" class="error">Invalid email address</span>
      </div>
      <div>
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" />
        <span v-if="showPasswordError" class="error">Password must be at least 8 characters</span>
      </div>
      <button type="submit">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      password: '',
    };
  },
  computed: {
    showEmailError() {
      return !this.isValidEmail(this.email) && this.email !== '';
    },
    showPasswordError() {
      return this.password.length < 8 && this.password !== '';
    },
  },
  methods: {
    isValidEmail(email) {
      // Implement your own email validation logic here
      const emailRegex = /^[\w-]+(\.[\w-]+)*@[a-zA-Z0-9-]+(\.[a-zA-Z0-9-]+)*(\.[a-zA-Z]{2,})$/;
      return emailRegex.test(email);
    },
    handleSubmit() {
      // Handle form submission logic here
      if (this.showEmailError || this.showPasswordError) {
        return;
      }
      // Submit form
      console.log('Form submitted successfully');
    },
  },
};
</script>
```

In this example, we have a simple form that accepts an email and password. The `v-model` directive binds the form inputs to `email` and `password` data properties.

The `computed` property `showEmailError` checks if the entered email is invalid and not empty. If it is, it returns `true`, triggering the display of an error message.

Similarly, the `showPasswordError` computed property checks if the entered password is too short and not empty.

The `handleSubmit` method is called when the form is submitted. It checks if either the email or password has an error. If there is an error, the form submission is prevented, and an error message is displayed.

## Styling the Component

To make the error messages more visually appealing, add the following CSS styles to the component:

```css
<style>
.error {
  color: red;
}
</style>
```

## Using the Form Component

To use the `Form` component created above, replace the content in the `App.vue` file with the following code:

```html
<template>
  <div id="app">
    <Form />
  </div>
</template>

<script>
import Form from './components/Form.vue';

export default {
  name: 'App',
  components: {
    Form,
  },
};
</script>
```

## Testing the Dynamic Form Validation

Now that everything is set up, start the development server with the following command:

```bash
npm run serve
```

Visit `http://localhost:8080` in your web browser to see the form in action.

Try entering an invalid email address or a password shorter than 8 characters. You should see the error message displayed dynamically, guiding the user to correct their input.

## Conclusion

Dynamic form validation is a crucial aspect of web development. By utilizing ternary operators in Vue.js, we can easily conditionally display error messages based on user input.

In this blog post, we explored how to implement dynamic form validation using Vue.js, setting up a basic project, creating a form component, and leveraging computed properties to control the display of error messages.

Now you have the knowledge to employ dynamic form validation in your Vue.js applications to enhance user experience and prevent invalid submissions.

#vuejs #formvalidation