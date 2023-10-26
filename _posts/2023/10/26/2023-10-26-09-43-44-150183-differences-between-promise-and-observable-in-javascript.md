---
layout: post
title: "Differences between Promise and Observable in Javascript"
description: " "
date: 2023-10-26
tags: [asynchronous]
comments: true
share: true
---

In JavaScript, both Promises and Observables are used for handling asynchronous operations and managing data streams. While they have some similarities, there are also significant differences between the two. In this blog post, we will explore these differences and understand when to use Promises and when to use Observables in JavaScript.

## Table of Contents
- [Promises](#promises)
- [Observables](#observables)
- [Differences](#differences)
  - [Eager vs Lazy](#eager-vs-lazy)
  - [Multiple vs Single Value](#multiple-vs-single-value)
  - [Cancellation](#cancellation)
  - [Operators and Transformation](#operators-and-transformation)
- [Conclusion](#conclusion)

## Promises

Promises are a built-in feature in JavaScript that allow us to handle asynchronous operations. They represent a single value that may not be available immediately and are commonly used for making AJAX requests and handling asynchronous data. Promises have three states: **pending**, **fulfilled**, and **rejected**. Once a Promise is fulfilled or rejected, it will no longer change its state.

Here's an example of using a Promise to fetch data:

```javascript
const myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    if (Math.random() < 0.5) {
      resolve('Data fetched successfully!');
    } else {
      reject('Error fetching data!');
    }
  }, 2000);
});

myPromise.then((data) => {
  console.log(data);
}).catch((error) => {
  console.error(error);
});
```

## Observables

Observables, on the other hand, are part of the ReactiveX library and provide a way to represent streams of data that change over time. They are more powerful than Promises as they allow us to handle multiple values over time, giving us more flexibility in handling data streams. Observables are also cancellable.

Here's an example of using an Observable to represent a stream of data:

```javascript
import { Observable } from 'rxjs';

const myObservable = new Observable((observer) => {
  let counter = 0;
  setInterval(() => {
    observer.next(counter++);
  }, 1000);
});

const subscription = myObservable.subscribe((data) => {
  console.log(data);
});

setTimeout(() => {
  subscription.unsubscribe();
}, 5000);
```

## Differences

### Eager vs Lazy

Promises are eager, meaning they are executed immediately upon creation. This makes them suitable for one-time asynchronous operations. On the other hand, Observables are lazy, meaning they are only executed when there is a subscriber. This makes Observables suitable for continuous data streams.

### Multiple vs Single Value

Promises represent a single value that may be resolved or rejected. Once the Promise is settled, it cannot emit more values. Observables, however, can emit multiple values over time. They can emit values indefinitely until they are unsubscribed.

### Cancellation

Promises cannot be cancelled once they are executed. Once a Promise is settled, it will run to completion. On the other hand, Observables can be cancelled by unsubscribing from them. This allows for more granular control over resources and can help prevent memory leaks.

### Operators and Transformation

Observables come with a rich set of operators that allow us to transform and manipulate the data stream. We can perform operations such as filtering, mapping, and reducing the data emitted by the Observable. Promises, on the other hand, do not have built-in operators for data transformation.

## Conclusion

In summary, Promises and Observables are both useful for handling asynchronous operations in JavaScript, but they have different characteristics. Promises are suitable for one-time operations and represent a single value, while Observables are suitable for continuous streams of data and can emit multiple values. Observables also offer cancellation and a range of operators for data transformation. Choosing between Promises and Observables depends on the specific requirements of your application and the nature of the data you are working with.

Make sure to follow us for more tech-related posts! #javascript #asynchronous