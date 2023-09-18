---
layout: post
title: "Building a multi-step form with Redux and Formik in JavaScript"
description: " "
date: 2023-09-14
tags: [react]
comments: true
share: true
---

One common requirement in web development is creating multi-step forms, where users can input information across different pages or sections. In this tutorial, we will learn how to build a multi-step form using Redux and Formik in JavaScript.

## What is Redux and Formik?

**Redux** is a state management library for JavaScript applications. It helps manage the application state in a predictable and consistent manner, making it easier to reason about the data flow in the application.

**Formik** is a popular form library for React applications. It simplifies form handling by providing a set of utility functions and components that streamline the process of building and managing forms.

## Prerequisites

To follow along with this tutorial, you will need:

- Basic understanding of JavaScript and React
- Node.js and npm installed on your machine
- Create React App set up

## Setting Up the Project

Start by creating a new React project using Create React App:

```bash
npx create-react-app multi-step-form
```

Next, navigate to the project directory:

```bash
cd multi-step-form
```

Install the required dependencies:

```bash
npm install redux react-redux formik
```

## Implementing the Multi-Step Form

### Step 1: Setting Up Redux

In the `src` folder, create a `redux` folder. Inside the `redux` folder, create a `store.js` file. This is where we will set up our Redux store.

```javascript
// src/redux/store.js

import { createStore } from 'redux';
import rootReducer from './reducers';

const store = createStore(rootReducer);

export default store;
```
### Step 2: Creating Redux Reducers

Inside the `redux` folder, create a `reducers.js` file. This is where we will define our reducers.

```javascript
// src/redux/reducers.js

const initialState = {
  form: {
    step: 1,
    firstname: '',
    lastname: '',
    email: '',
  },
};

const rootReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'SET_FIRSTNAME':
      return {
        ...state,
        form: {
          ...state.form,
          firstname: action.payload,
        },
      };
    case 'SET_LASTNAME':
      return {
        ...state,
        form: {
          ...state.form,
          lastname: action.payload,
        },
      };
    case 'SET_EMAIL':
      return {
        ...state,
        form: {
          ...state.form,
          email: action.payload,
        },
      };
    case 'SET_STEP':
      return {
        ...state,
        form: {
          ...state.form,
          step: action.payload,
        },
      };
    default:
      return state;
  }
};

export default rootReducer;
```
### Step 3: Setting Up Formik

In the `src` folder, create a `components` folder. Inside the `components` folder, create a `MultiStepForm.js` file. This is where we will define our multi-step form component.

```javascript
// src/components/MultiStepForm.js

import React from 'react';
import { connect } from 'react-redux';
import { Field, ErrorMessage, withFormik } from 'formik';

const MultiStepForm = ({
  values,
  errors,
  touched,
  handleChange,
  handleBlur,
  handleSubmit,
}) => {
  return (
    <form onSubmit={handleSubmit}>
      <div>
        <h3>Step 1</h3>
        <label htmlFor="firstname">First Name</label>
        <Field type="text" name="firstname" id="firstname" />
        <ErrorMessage name="firstname" component="div" />
      </div>

      <div>
        <h3>Step 2</h3>
        <label htmlFor="lastname">Last Name</label>
        <Field type="text" name="lastname" id="lastname" />
        <ErrorMessage name="lastname" component="div" />
      </div>

      <div>
        <h3>Step 3</h3>
        <label htmlFor="email">Email Address</label>
        <Field type="email" name="email" id="email" />
        <ErrorMessage name="email" component="div" />
      </div>

      <button type="submit">Submit</button>
    </form>
  );
};

const ConnectedMultiStepForm = connect()(MultiStepForm);

export default withFormik({
  mapPropsToValues: () => ({
    firstname: '',
    lastname: '',
    email: '',
  }),
  handleSubmit: (values, { props }) => {
    console.log(values);
    props.dispatch({ type: 'SET_FIRSTNAME', payload: values.firstname });
    props.dispatch({ type: 'SET_LASTNAME', payload: values.lastname });
    props.dispatch({ type: 'SET_EMAIL', payload: values.email });
  },
})(ConnectedMultiStepForm);
```
### Step 4: Rendering the Multi-Step Form

Open the `src/App.js` file and modify it to render the `MultiStepForm` component:

```javascript
// src/App.js

import React from 'react';
import { Provider } from 'react-redux';
import store from './redux/store';
import MultiStepForm from './components/MultiStepForm';

const App = () => {
  return (
    <Provider store={store}>
      <div className="App">
        <h1>Multi-Step Form Example</h1>
        <MultiStepForm />
      </div>
    </Provider>
  );
};

export default App;
```
## Conclusion

In this tutorial, we have learned how to build a multi-step form using Redux and Formik in JavaScript. We set up Redux store, created reducers, and implemented Formik to handle form state and validation. With this knowledge, you can now create interactive and user-friendly multi-step forms for your web applications. Happy coding!

#javascript #react