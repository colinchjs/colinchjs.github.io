---
layout: post
title: "Implementing a search bar with Chakra UI"
description: " "
date: 2023-09-25
tags: [ChakraUI, React]
comments: true
share: true
---

In this post, we will explore how to implement a search bar using Chakra UI, a popular component library for React. The search bar is a common feature in many web applications, allowing users to quickly search and filter data. We will go through the steps of setting up Chakra UI, creating the search bar component, and handling user input.

## Setting up Chakra UI

First, we need to install the Chakra UI package and its dependencies. Open your project directory in the terminal and run the following command:

```shell
npm install @chakra-ui/react @emotion/react@^11 @emotion/styled@^11 framer-motion@^4
```

Next, import the required Chakra UI components in your project. Open your entry file (e.g., `index.js` or `App.js`) and add the following import statements:

```javascript
import { ChakraProvider, CSSReset } from "@chakra-ui/react";
```

Wrap your main component with the `ChakraProvider` component and add the `CSSReset` component to reset any browser-specific styles:

```jsx
<ChakraProvider>
  <CSSReset />
  {/* Your main component */}
</ChakraProvider>
```

## Creating the search bar component

Now let's create the search bar component. Create a new file called `SearchBar.js` and add the following code:

```jsx
import { Input, InputGroup, InputLeftElement } from "@chakra-ui/react";
import { HiSearch } from "react-icons/hi";

const SearchBar = () => {
  return (
    <InputGroup>
      <InputLeftElement
        pointerEvents="none"
        children={<HiSearch color="gray.300" />}
      />
      <Input type="text" placeholder="Search..." />
    </InputGroup>
  );
};

export default SearchBar;
```

In the code above, we use the `InputGroup`, `Input`, and `InputLeftElement` components from Chakra UI. We also import the `HiSearch` icon from the `react-icons` library to display a search icon on the left side of the input field.

## Using the search bar component

To use the search bar component in your application, import it into your desired component and render it. For example, in your `App.js`, add the following code:

```jsx
import SearchBar from "./SearchBar";

const App = () => {
  return (
    <div>
      <SearchBar />
      {/* Rest of your application */}
    </div>
  );
};

export default App;
```

Now, when you run your application, you should see a search bar with an input field and a search icon.

## Handling user input

To make the search bar functional, we need to handle user input. In the `SearchBar.js` file, modify the `Input` component as follows:

```jsx
<Input type="text" placeholder="Search..." onChange={handleInputChange} />
```

In your `SearchBar` component, define the `handleInputChange` function:

```jsx
const handleInputChange = (event) => {
  const searchText = event.target.value;
  // You can perform any search logic here
};
```

By using the `onChange` event handler, you can access the user's input and perform any search logic, such as filtering data or making API calls.

That's it! You have successfully implemented a search bar with Chakra UI. You can customize the appearance and behavior of the search bar component further according to your project requirements.

#ChakraUI #React