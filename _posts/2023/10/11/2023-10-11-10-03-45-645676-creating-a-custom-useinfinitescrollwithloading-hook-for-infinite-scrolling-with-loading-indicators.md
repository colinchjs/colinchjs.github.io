---
layout: post
title: "Creating a custom useInfiniteScrollWithLoading hook for infinite scrolling with loading indicators"
description: " "
date: 2023-10-11
tags: [react, scrolling]
comments: true
share: true
---

Infinite scrolling is a popular UI pattern that allows content to be loaded dynamically as users scroll down a page. Adding loading indicators to indicate that more content is being loaded enhances the user experience. In this blog post, we will discuss how to create a custom `useInfiniteScrollWithLoading` hook in React, which combines infinite scrolling functionality with loading indicators.

## Table of Contents
- [Introduction](#introduction)
- [Setting up the Project](#setting-up-the-project)
- [Implementing the `useInfiniteScrollWithLoading` Hook](#implementing-the-useinfinitescrollwithloading-hook)
- [Using the Hook in a Component](#using-the-hook-in-a-component)
- [Conclusion](#conclusion)

## Introduction
Infinite scrolling can be achieved by using the `Intersection Observer API`, which allows us to observe when an element enters or exits the viewport. Additionally, we can use loading indicators, such as spinners or progress bars, to show that content is being loaded.

## Setting up the Project
To get started, make sure you have Node.js and npm installed on your machine. Create a new React project using the `create-react-app` CLI or any other method you prefer.

Once your project is set up, let's install the required dependencies:

```shell
npm install react@latest react-dom@latest
```

## Implementing the `useInfiniteScrollWithLoading` Hook
Create a new file called `useInfiniteScrollWithLoading.js` and define the custom hook:

```javascript
import { useEffect, useRef, useState } from 'react';

const useInfiniteScrollWithLoading = (loadMore) => {
  const [isLoading, setIsLoading] = useState(false);
  const loaderRef = useRef(null);

  useEffect(() => {
    const options = {
      root: null,
      rootMargin: '20px',
      threshold: 0.8,
    };

    const handleIntersection = (entries) => {
      const target = entries[0];
      if (target.isIntersecting && !isLoading) {
        setIsLoading(true);
        loadMore();
      }
    };

    const observer = new IntersectionObserver(handleIntersection, options);

    if (loaderRef.current) {
      observer.observe(loaderRef.current);
    }

    return () => {
      if (loaderRef.current) {
        observer.unobserve(loaderRef.current);
      }
    };
  }, [isLoading, loadMore]);

  return [loaderRef, isLoading];
};

export default useInfiniteScrollWithLoading;
```

The `useInfiniteScrollWithLoading` hook takes a `loadMore` function as a parameter, which will be called when the loader element is intersected with the viewport. It returns a reference to the loader element (`loaderRef`) and a boolean value indicating whether content is currently being loaded (`isLoading`).

## Using the Hook in a Component
Now, let's see how we can use the `useInfiniteScrollWithLoading` hook in a component. Assume we have an `ArticleList` component that displays a list of articles. When the user scrolls to the bottom of the page, we want to load more articles and display a loading spinner while the request is being processed.

```javascript
import React, { useState } from 'react';
import useInfiniteScrollWithLoading from './useInfiniteScrollWithLoading';

const ArticleList = () => {
  const [articles, setArticles] = useState([]);
  const [currentPage, setCurrentPage] = useState(1);

  const loadMoreArticles = async () => {
    // Simulating an API call to fetch more articles
    const response = await fetch(`https://api.example.com/articles?page=${currentPage + 1}`);
    const newArticles = await response.json();
    
    // Update the state with the new articles
    setArticles([...articles, ...newArticles]);
    setCurrentPage(currentPage + 1);
  };

  const [loaderRef, isLoading] = useInfiniteScrollWithLoading(loadMoreArticles);

  return (
    <div>
      {articles.map((article) => (
        // Render each article item
        <div key={article.id}>{article.title}</div>
      ))}
      {/* Render the loading indicator */}
      {isLoading && <div ref={loaderRef}>Loading...</div>}
    </div>
  );
};

export default ArticleList;
```

In this example, the `loadMoreArticles` function is responsible for fetching more articles from an API and updating the list of articles in the state. We pass this function as a parameter to the `useInfiniteScrollWithLoading` hook.

We then render each article item and display the loading indicator by checking the value of `isLoading`. The `loaderRef` is assigned to the `ref` attribute of the loading element, allowing the Intersection Observer to observe it.

## Conclusion
In this blog post, we discussed how to create a custom `useInfiniteScrollWithLoading` hook in React to implement infinite scrolling with loading indicators. By combining the `Intersection Observer API` with loading indicators, we can enhance the user experience by providing real-time feedback when more content is being loaded. Feel free to customize the hook to suit your specific needs and add additional features. Happy scrolling!

**#react #scrolling**

[Click here to download the source code for this project.](https://github.com/example-user/infinite-scrolling-with-loading-indicators)