---
layout: post
title: "Using the Cache API in a service worker"
description: " "
date: 2023-10-23
tags: [caching]
comments: true
share: true
---

A service worker is a script that runs in the background of a web page and handles network requests, among other things. One of the powerful features of service workers is the ability to cache requests and responses using the Cache API. In this blog post, we will explore how to use the Cache API in a service worker to improve the performance and offline capabilities of a web application.

## Table of Contents
- [Introduction to the Cache API](#introduction-to-the-cache-api)
- [Caching Requests](#caching-requests)
- [Retrieving Cached Responses](#retrieving-cached-responses)
- [Updating the Cache](#updating-the-cache)
- [Cleaning up the Cache](#cleaning-up-the-cache)
- [Conclusion](#conclusion)

## Introduction to the Cache API

The Cache API provides a way to store assets, such as HTML, CSS, JavaScript files, images, and more, in a cache storage. This allows the service worker to serve these assets directly from the cache, rather than making a network request every time. 

To use the Cache API, we first need to open a cache using the `caches.open()` method. This method returns a promise that resolves to a cache object. We can then use this cache object to store and retrieve assets.

```javascript
// Open a cache
caches.open('my-cache').then(function(cache) {
  // Perform caching operations
});
```

## Caching Requests

To cache a request, we can use the `cache.put()` method. this method takes two parameters: the request and the response. Once a request is cached, we can later retrieve and serve the response from the cache.

```javascript
// Cache a request
cache.put(request, response);
```

Typically, we would use the service worker's `fetch` event to intercept network requests and cache the responses. Here's an example of how to cache a GET request using the service worker:

```javascript
self.addEventListener('fetch', function(event) {
  event.respondWith(
    fetch(event.request).then(function(response) {
      // Clone the response as it can only be consumed once
      var responseClone = response.clone();
      
      // Open the cache
      caches.open('my-cache').then(function(cache) {
        // Cache the response
        cache.put(event.request, responseClone);
      });
      
      // Return the response
      return response;
    })
  );
});
```

## Retrieving Cached Responses

To retrieve a cached response, we can use the `cache.match()` method. This method takes a request as a parameter and returns a promise that resolves to the matching response from the cache.

```javascript
// Retrieve a cached response
cache.match(request).then(function(response) {
  if (response) {
    // Use the cached response
  } else {
    // Network fallback
  }
});
```

In the context of the service worker, we can use the `fetch` event to intercept network requests and serve the responses from the cache if available. Here's an example:

```javascript
self.addEventListener('fetch', function(event) {
  event.respondWith(
    caches.match(event.request).then(function(response) {
      if (response) {
        // Use the cached response
        return response;
      } else {
        // Fallback to network
        return fetch(event.request);
      }
    })
  );
});
```

## Updating the Cache

To update the cache with the latest versions of assets, we can use the `cache.put()` method to overwrite the existing cached responses. This can be done by intercepting network requests and updating the cache with the new responses.

```javascript
self.addEventListener('fetch', function(event) {
  event.respondWith(
    caches.open('my-cache').then(function(cache) {
      return fetch(event.request).then(function(response) {
        // Update the cache with the latest response
        cache.put(event.request, response.clone());
        
        // Return the response
        return response;
      });
    })
  );
});
```

## Cleaning up the Cache

Over time, the cache can accumulate outdated and unused assets. To clean up the cache, we can use the `cache.delete()` method to remove specific cached responses.

```javascript
// Delete a cached response
cache.delete(request);
```

We can also use the `cache.keys()` method to retrieve all the cache keys and iterate over them to delete the desired entries.

```javascript
// Clean up the cache
caches.open('my-cache').then(function(cache) {
  cache.keys().then(function(keys) {
    keys.forEach(function(key) {
      cache.delete(key);
    });
  });
});
```

## Conclusion

The Cache API in service workers provides a powerful mechanism for caching and serving assets. By intelligently using the Cache API, we can improve the performance and offline capabilities of our web applications. With careful management of the cache, we can ensure that our applications always have the latest versions of assets and deliver a fast and reliable user experience.

## References
- [MDN Web Docs - Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
- [MDN Web Docs - Cache](https://developer.mozilla.org/en-US/docs/Web/API/Cache)
- [Google Developers - Caching Files with Service Worker](https://developers.google.com/web/fundamentals/primers/service-workers#caching_files_with_service_worker)