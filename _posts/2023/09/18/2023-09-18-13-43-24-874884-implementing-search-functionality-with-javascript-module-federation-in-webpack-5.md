---
layout: post
title: "Implementing search functionality with JavaScript Module Federation in Webpack 5"
description: " "
date: 2023-09-18
tags: [modulefederation]
comments: true
share: true
---

In modern web applications, it's common to have multiple microfrontends that are developed and deployed independently. Webpack 5 introduced a new feature called Module Federation, which enables the sharing of code between different applications or microfrontends. In this blog post, we will explore how to implement search functionality using JavaScript Module Federation in Webpack 5.

## What is Module Federation?

Module Federation is a feature in Webpack 5 that allows you to dynamically load and share code across multiple applications or microfrontends. It allows you to split your application into multiple independently deployable pieces, while ensuring that they can still communicate with each other and share code.

## Implementing search functionality

To implement search functionality using Module Federation, we need to create two microfrontends. The first microfrontend will be responsible for rendering the search bar and handling the search events, while the second microfrontend will be responsible for rendering the search results.

Here's how we can implement this:

### 1. Create the search bar microfrontend

In this microfrontend, we will create a search bar component that listens for search events and emits them using a custom event.

```javascript
// search-bar.js
import './search-bar.css';

export function createSearchBar() {
  const searchBar = document.createElement('div');
  searchBar.classList.add('search-bar');

  const input = document.createElement('input');
  input.type = 'text';
  input.placeholder = 'Search...';
  input.addEventListener('input', handleInput);

  searchBar.appendChild(input);

  function handleInput(event) {
    const searchTerm = event.target.value;
    const searchEvent = new CustomEvent('search', { detail: searchTerm });
    window.dispatchEvent(searchEvent);
  }

  return searchBar;
}
```

### 2. Create the search results microfrontend

In this microfrontend, we will listen for the search events emitted by the search bar microfrontend and render the search results.

```javascript
// search-results.js
import './search-results.css';

export function createSearchResults() {
  const searchResults = document.createElement('div');
  searchResults.classList.add('search-results');

  window.addEventListener('search', handleSearch);

  function handleSearch(event) {
    const searchTerm = event.detail;
    
    // Do search and render results
    // ...
  }

  return searchResults;
}
```

### 3. Set up Module Federation in Webpack config

In your Webpack configuration, you need to set up the Module Federation plugin to enable sharing of the search bar and search results code between microfrontends.

```javascript
// webpack.config.js
const ModuleFederationPlugin = require('webpack/lib/container/ModuleFederationPlugin');

module.exports = {
  // ...
  plugins: [
    new ModuleFederationPlugin({
      name: 'searchMicrofrontend',
      remotes: {
        searchBar: 'searchBar@http://localhost:3001/remoteEntry.js',
        searchResults: 'searchResults@http://localhost:3002/remoteEntry.js',
      },
    }),
  ],
};
```

### 4. Use the microfrontends in the main application

In your main application, you can now use the search bar and search results microfrontends.

```javascript
// main.js
import { createSearchBar } from 'searchMicrofrontend/searchBar';
import { createSearchResults } from 'searchMicrofrontend/searchResults';

const searchBarContainer = document.getElementById('search-bar-container');
searchBarContainer.appendChild(createSearchBar());

const searchResultsContainer = document.getElementById('search-results-container');
searchResultsContainer.appendChild(createSearchResults());
```

## Conclusion

JavaScript Module Federation in Webpack 5 provides a powerful mechanism for implementing search functionality in a microfrontend architecture. By creating separate microfrontends for the search bar and search results, and using Module Federation, we can easily share code and communicate between these microfrontends. This approach allows for better modularity and scalability in web applications.

#javascript #modulefederation