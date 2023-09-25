---
layout: post
title: "React.js i18n and l10n with react-intl"
description: " "
date: 2023-09-25
tags: [react, reactjs]
comments: true
share: true
---

React.js is a popular JavaScript library for building user interfaces. When creating multi-language applications, it's essential to have a solid internationalization (i18n) and localization (l10n) solution. One of the widely used packages for achieving this in React.js is `react-intl`.

## What is react-intl?

`react-intl` is an open-source library that provides internationalization and localization capabilities for React.js applications. It offers a set of components, utilities, and formatting functions for handling translations, dates, numbers, and other locale-specific content.

## Getting Started

To start using `react-intl`, you need to install it as a dependency in your React.js project. Open your terminal and run the following command:

```shell
npm install react-intl
```

or if you prefer yarn, you can use:

```shell
yarn add react-intl
```

Once installed, you can import the necessary modules and start using them in your React components.

## Setting up translation messages

The first step is to define translation messages for different languages. You can store these messages in JSON format or use a separate file for each language. Let's create a file named `messages.js`, and define some example translation messages:

```jsx
// messages.js

import { defineMessages } from 'react-intl';

export default defineMessages({
  welcomeMessage: {
    id: 'app.welcome',
    defaultMessage: 'Welcome to my React app!',
  },
  goodbyeMessage: {
    id: 'app.goodbye',
    defaultMessage: 'Goodbye, see you later!',
  },
});
```

Here, we use the `defineMessages` function from `react-intl` to define our messages. Each message has an `id` which serves as a unique identifier, and a `defaultMessage` which is the default translation in case a matching translation is not found.

## Using react-intl components

React-intl provides various components that make it easy to handle translations within your React.js components. Here are a few examples:

### 1. FormattedMessage

The `FormattedMessage` component is used to display translated messages. It takes an `id` prop which corresponds to the `id` of the translation message. Here's an example usage:

```jsx
import { FormattedMessage } from 'react-intl';
import messages from './messages';

const MyComponent = () => (
  <div>
    <h1>
      <FormattedMessage {...messages.welcomeMessage} />
    </h1>
    <p>
      <FormattedMessage {...messages.goodbyeMessage} />
    </p>
  </div>
);

export default MyComponent;
```

### 2. FormattedNumber

The `FormattedNumber` component is used to format numbers according to the current locale. It takes a `value` prop representing the number to format. Here's an example usage:

```jsx
import { FormattedNumber } from 'react-intl';

const MyNumberComponent = () => (
  <p>
    <FormattedNumber value={1000} style="currency" currency="USD" />
  </p>
);

export default MyNumberComponent;
```

### 3. FormattedDate

The `FormattedDate` component is used to format dates according to the current locale. It takes a `value` prop representing the date, and an optional `format` prop to customize the date format. Here's an example usage:

```jsx
import { FormattedDate } from 'react-intl';

const MyDateComponent = () => (
  <p>
    <FormattedDate value={new Date()} year="numeric" month="long" day="numeric" />
  </p>
);

export default MyDateComponent;
```

## Localization (l10n)

`react-intl` also provides utilities for handling localization, such as detecting the user's browser locale and switching between different locales. You can use the `IntlProvider` component to set the desired locale for your application. 

```jsx
import { IntlProvider } from 'react-intl';
import messages from './messages';

const App = () => (
  <IntlProvider locale="en" messages={messages}>
    // Your app components
  </IntlProvider>
);

export default App;
```

By passing the `locale` prop to `IntlProvider`, you can specify the desired locale, such as "en" for English or "fr" for French. The `messages` prop should contain the translation messages for the specified locale.

## Conclusion

`react-intl` is a powerful library for implementing internationalization and localization in React.js applications. It provides a convenient way to handle translations, numbers, dates, and more. By combining `react-intl` with the right tools and techniques, you can create multi-language applications that cater to global audiences.

#react #reactjs