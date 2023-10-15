---
layout: post
title: "Localization and internationalization with suspense in React"
description: " "
date: 2023-10-16
tags: []
comments: true
share: true
---

React has become one of the most popular front-end JavaScript libraries for building user interfaces. When developing applications, one common requirement is to support multiple languages and locales. This is where localization and internationalization (i18n) come into play. In this blog post, we will explore how to implement localization and internationalization with the help of React's Suspense feature.

## What is Localization and Internationalization?

Localization refers to the process of adapting an application to different languages, cultures, and regions. It involves translating text, adapting layouts, and handling various date and number formats based on the user's preferences. Internationalization, on the other hand, is the design and development process of enabling an application to be easily localized.

## React Suspense

React Suspense is a feature introduced in React 16.6 to handle components that may have asynchronous dependencies. It allows you to "suspend" rendering until the required data is fetched. Suspense comes in handy when dealing with asynchronous language or locale data loading.

## Introduction to react-intl

To implement localization and internationalization in React, we can utilize the `react-intl` library. `react-intl` provides a set of components and utilities for working with internationalized data. It offers features such as formatting dates, numbers, and pluralization, along with handling translations.

## Setting up react-intl and Language Context

First, let's install the required dependencies:

```shell
npm install react-intl
```

Next, we need to set up a `LanguageContext` using React's Context API. This context will be responsible for providing the selected language to the entire application. Here's an example implementation of the `LanguageContext`:

```javascript
import React, { createContext, useState } from 'react';

export const LanguageContext = createContext();

const LanguageContextProvider = ({ children }) => {
  const [language, setLanguage] = useState('en');

  const changeLanguage = (newLanguage) => {
    setLanguage(newLanguage);
  };

  return (
    <LanguageContext.Provider value={{ language, changeLanguage }}>
      {children}
    </LanguageContext.Provider>
  );
};

export default LanguageContextProvider;
```

## Localization with react-intl

With `react-intl`, we can define language-specific messages and render them based on the selected language. Let's look at an example of how to use `react-intl` for localization:

```javascript
import { FormattedMessage, IntlProvider } from 'react-intl';
import { useContext } from 'react';
import { LanguageContext } from './LanguageContext';

const App = () => {
  const { language } = useContext(LanguageContext);

  const messages = {
    en: {
      greeting: 'Hello, World!',
    },
    fr: {
      greeting: 'Bonjour, le Monde!',
    },
  };

  return (
    <IntlProvider locale={language} messages={messages[language]}>
      <div>
        <p>
          <FormattedMessage id="greeting" />
        </p>
      </div>
    </IntlProvider>
  );
};

export default App;
```

In the above example, we define the messages for English and French inside the `messages` object. The `FormattedMessage` component is used to display the localized text based on the selected language. The `id` prop of the `FormattedMessage` component corresponds to the unique message key.

## Suspense and Async Language Loading

Now, let's explore how to use Suspense to load language data asynchronously. First, we need to define a custom `LanguageLoader` component that will be responsible for fetching the required language data. Here's an example implementation:

```javascript
import { useEffect, useState } from 'react';

const LanguageLoader = ({ language, children }) => {
  const [languageData, setLanguageData] = useState(null);

  useEffect(() => {
    const fetchLanguageData = async () => {
      const response = await fetch(`/api/languages/${language}`);
      const data = await response.json();
      setLanguageData(data);
    };

    fetchLanguageData();
  }, [language]);

  return <>{languageData ? children : null}</>;
};

export default LanguageLoader;
```

In the above example, we fetch the language data based on the selected language using an API endpoint. Inside the `LanguageLoader`, we render the children only if the language data is available.

To implement Suspense, we wrap our `App` component with the `Suspense` component and provide a fallback UI to display while the language data is being loaded:

```javascript
import { Suspense } from 'react';
import LanguageLoader from './LanguageLoader';
import App from './App';

const LocalizationApp = () => {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <LanguageLoader>
        <App />
      </LanguageLoader>
    </Suspense>
  );
};

export default LocalizationApp;
```

With this setup, React Suspense will handle the loading of language data. The `fallback` component will be displayed while the language data is being fetched.

## Conclusion

Localization and internationalization are essential aspects of building globalized applications. React provides great support for implementing these features with the help of tools like `react-intl` and the Suspense feature. By following the steps discussed in this blog post, you can easily add localization and internationalization to your React applications.

---
References:

- React Suspense: [https://reactjs.org/docs/concurrent-mode-suspense.html](https://reactjs.org/docs/concurrent-mode-suspense.html)
- react-intl GitHub repository: [https://github.com/formatjs/formatjs](https://github.com/formatjs/formatjs)