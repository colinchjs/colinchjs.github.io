---
layout: post
title: "Implementing internationalization in JavaScript MVC"
description: " "
date: 2023-09-23
tags: [Internationalization]
comments: true
share: true
---

In today's globalized world, it is essential to provide multilingual support in web applications. Implementing internationalization (i18n) allows users to switch between different languages, providing a personalized experience and expanding the reach of your application to a diverse user base.

In this blog post, we will discuss how to implement internationalization in a JavaScript Model-View-Controller (MVC) framework. Specifically, we will focus on i18n implementation using the popular JavaScript frameworks such as AngularJS and React.

## AngularJS i18n Implementation

AngularJS provides built-in support for internationalization through its i18n module. To implement internationalization in AngularJS, follow these steps:

1. Configure AngularJS to load the necessary i18n files based on the user's language preference. This can be done by using the `$translateProvider` module, which allows you to define language-specific translation files.

   ```javascript
   angular.module('myApp', ['pascalprecht.translate'])
     .config(function ($translateProvider) {
       $translateProvider.useStaticFilesLoader({
         prefix: 'translations/locale-',
         suffix: '.json'
       });

       $translateProvider.preferredLanguage('en');
     });
   ```

2. Create separate translation files for each language, following the JSON format. For example, you can have `locale-en.json` for English and `locale-es.json` for Spanish.

   ```json
   {
     "greeting": "Hello",
     "welcome_message": "Welcome to our application!"
   }
   ```

3. Inject the `$translate` service wherever you need to display translated strings, and use the `$translate.instant()` function to fetch translated values.

   ```html
   <div>{{ 'greeting' | translate }}</div>
   <div>{{ 'welcome_message' | translate }}</div>
   ```

   The translated values will be fetched based on the user's language preference.

## React i18n Implementation

React does not have built-in support for internationalization, but there are several popular libraries available that can be used to achieve internationalization in a React application. One of the most commonly used libraries is `react-i18next`.

Here's a brief guide on how to implement internationalization in React using `react-i18next`:

1. Install the required libraries by running the following command:

   ```bash
   npm install react-i18next i18next --save
   ```

2. Set up the i18n configuration using `i18next` and `react-i18next`.

   ```javascript
   import i18n from 'i18next';
   import { initReactI18next } from 'react-i18next';

   i18n.use(initReactI18next).init({
     resources: {
       en: {
         translation: {
           greeting: "Hello",
           welcome_message: "Welcome to our application!",
         },
       },
       es: {
         translation: {
           greeting: "Hola",
           welcome_message: "¡Bienvenido a nuestra aplicación!",
         },
       },
     },
     lng: 'en',
     fallbackLng: 'en',
   });

   export default i18n;
   ```

3. Wrap your root component with the `I18nextProvider` and pass the `i18n` instance.

   ```javascript
   import { I18nextProvider } from 'react-i18next';
   import i18n from './i18n';

   ReactDOM.render(
     <I18nextProvider i18n={i18n}>
       <App />
     </I18nextProvider>,
     document.getElementById('root')
   );
   ```

4. Use the `useTranslation` hook to access the translated values in your components.

   ```javascript
   import React from 'react';
   import { useTranslation } from 'react-i18next';

   function Greeting() {
     const { t } = useTranslation();

     return (
       <div>
         {t('greeting')}
         {t('welcome_message')}
       </div>
     );
   }
   ```

With these steps, you can enable internationalization in your JavaScript MVC application, providing a more inclusive and accessible experience for your users.

#JavaScript #Internationalization #AngularJS #React