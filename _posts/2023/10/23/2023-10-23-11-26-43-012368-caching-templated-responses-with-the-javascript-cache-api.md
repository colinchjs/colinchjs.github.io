---
layout: post
title: "Caching templated responses with the JavaScript Cache API"
description: " "
date: 2023-10-23
tags: [references]
comments: true
share: true
---

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [Caching Templated Responses](#caching-templated-responses)
- [Retrieving Cached Responses](#retrieving-cached-responses)
- [Updating and Deleting Cached Responses](#updating-and-deleting-cached-responses)
- [Conclusion](#conclusion)

## Introduction
The Cache API is a part of the broader set of browser features known as Service Workers. It allows us to programmatically manage a cache of responses and store them in the browser for offline usage or faster access. By caching templated responses, we can reduce network requests and provide users with a smoother experience.

## Getting Started
Before we can start caching templated responses, we need to register a Service Worker in our web application. This can be done by creating a new JavaScript file, registering it in the HTML file, and implementing the caching logic inside the Service Worker.

```javascript
// service-worker.js

self.addEventListener('install', (event) => {
  event.waitUntil(
    caches.open('my-cache').then((cache) => {
      return cache.addAll([
        'index.html',
        'style.css',
        'script.js'
        // Add more files to cache as needed
      ]);
    })
  );
});

self.addEventListener('fetch', (event) => {
  event.respondWith(
    caches.match(event.request).then((response) => {
      return response || fetch(event.request);
    })
  );
});
```

In the above code snippet, we first open a cache named 'my-cache' in the `install` event handler. We then add the necessary files, such as `index.html`, `style.css`, and `script.js`, to the cache. This ensures that these files will be available offline.

Next, in the `fetch` event handler, we intercept all network requests and try to match them with the cached responses. If a match is found, we return the cached response; otherwise, we fetch the response from the network.

## Caching Templated Responses
To cache templated responses, we can modify the `fetch` event handler in the Service Worker. Let's say we have a server endpoint `/api/products` that returns a JSON object of products. We can fetch this data, store it in the cache, and then serve the cached response in subsequent requests.

```javascript
self.addEventListener('fetch', (event) => {
  if (event.request.url.includes('/api/products')) {
    event.respondWith(
      caches.match(event.request).then((response) => {
        if (response) {
          return response;
        }
        return fetch(event.request).then((fetchResponse) => {
          return caches.open('my-cache').then((cache) => {
            cache.put(event.request, fetchResponse.clone());
            return fetchResponse;
          });
        });
      })
    );
  } else {
    event.respondWith(
      caches.match(event.request).then((response) => {
        return response || fetch(event.request);
      })
    );
  }
});
```

In the above code snippet, we first check if the requested URL contains `/api/products`. If it does, we try to match the request with a cached response. If a match is found, we return the cached response. Otherwise, we fetch the response from the network, store it in the cache, and then return it to the client.

## Retrieving Cached Responses
To retrieve cached responses, we can use the `Cache.match()` method. This method takes a request object and returns a promise that resolves to the matching response.

```javascript
caches.match(request).then((response) => {
  if (response) {
    // Use the cached response
  } else {
    // Fetch from the network
  }
});
```

By using `Cache.match()`, we can check if a response is already cached and use it if available. If not, we can make a network request to fetch the response.

## Updating and Deleting Cached Responses
Updating and deleting cached responses can be done using the `Cache.put()` and `Cache.delete()` methods, respectively. These methods allow us to add new responses to the cache or remove existing ones.

```javascript
caches.open('my-cache').then((cache) => {
  cache.put(request, response);
});

caches.open('my-cache').then((cache) => {
  cache.delete(request);
});
```

By using these methods, we can keep our cache up-to-date and remove obsolete or invalid responses.

## Conclusion
The JavaScript Cache API provides powerful caching capabilities for web applications. By caching templated responses, we can significantly improve performance and reduce network requests. In this blog post, we explored how to get started with the Cache API, cache templated responses, retrieve cached responses, and update/delete cached responses. By utilizing these techniques, we can create faster and more efficient web applications.

*Please note that the Cache API has specific limitations and is not supported in all browsers. Make sure to check the current browser support and fallback mechanisms for older browsers.*

#references
- [MDN Web Docs: Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache)
- [Google Developers: Service Workers: an Introduction](https://developers.google.com/web/fundamentals/primers/service-workers)