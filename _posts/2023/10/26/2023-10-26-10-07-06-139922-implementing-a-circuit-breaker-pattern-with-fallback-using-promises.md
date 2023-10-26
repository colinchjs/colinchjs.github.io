---
layout: post
title: "Implementing a circuit breaker pattern with fallback using promises"
description: " "
date: 2023-10-26
tags: []
comments: true
share: true
---

In distributed systems, failures can occur due to various reasons such as network issues, service unavailability, or high system load. To handle such scenarios and prevent cascading failures, we can use the Circuit Breaker pattern.

The Circuit Breaker pattern is a design pattern that helps in improving the resilience of an application by monitoring the success and failure rates of remote service calls. If the failure rate crosses a threshold, the Circuit Breaker trips and performs fallback actions instead of making additional calls to the failing service.

In this blog post, we will explore how to implement a Circuit Breaker pattern with fallback using promises in JavaScript.

## Understanding Promises

Promises are a way to handle asynchronous operations in JavaScript. They represent a value that may be available now or in the future. Promises provide a cleaner and more readable way to handle asynchronous operations compared to callbacks.

A Promise can have three states:

1. **Pending**: The initial state of a promise before it is fulfilled or rejected.
2. **Fulfilled**: The state when a promise is successfully resolved with a value.
3. **Rejected**: The state when a promise fails to be resolved with a reason or an error.

## Implementing the Circuit Breaker Pattern

To implement the Circuit Breaker pattern, we need to create a wrapper around the remote service call, which monitors the success and failure rates. If the failure rate crosses a certain threshold, the circuit breaker trips and triggers the fallback action.

```javascript
class CircuitBreaker {
  constructor(serviceCall, failureThreshold, recoveryTime) {
    this.serviceCall = serviceCall;
    this.failureThreshold = failureThreshold;
    this.recoveryTime = recoveryTime;
    this.failureCount = 0;
    this.isCircuitOpen = false;
    this.lastFailureTime = null;
  }

  async callService(params) {
    if (this.isCircuitOpen) {
      const currentTime = Date.now();
      if (currentTime - this.lastFailureTime >= this.recoveryTime) {
        this.isCircuitOpen = false;
        this.failureCount = 0;
      } else {
        throw new Error('Service unavailable');
      }
    }

    try {
      const result = await this.serviceCall(params);
      this.failureCount = 0;
      return result;
    } catch (error) {
      this.failureCount++;
      if (this.failureCount >= this.failureThreshold) {
        this.isCircuitOpen = true;
        this.lastFailureTime = Date.now();
      }
      throw new Error('Service unavailable');
    }
  }
}
```

In the above code, we have created a `CircuitBreaker` class that takes three parameters: `serviceCall` (the function to call the remote service), `failureThreshold` (the maximum number of failures to tolerate), and `recoveryTime` (the time to wait before trying the service again after tripping the circuit).

The `callService` method of `CircuitBreaker` handles the service call. It checks if the circuit is open, and if so, it checks if the recovery time has elapsed. If the recovery time has passed, it resets the circuit. If the circuit is closed or after resetting the circuit, it makes the actual service call.

If the service call succeeds, we reset the failure count. If the service call fails, we increment the failure count. If the failure count crosses the threshold, we trip the circuit and set the circuit open, recording the failure time.

## Using the Circuit Breaker

To use the Circuit Breaker, we need to create an instance of it and wrap our service call with it.

```javascript
const serviceCall = async (params) => {
  // Make the remote service call
};

const circuitBreaker = new CircuitBreaker(serviceCall, 3, 5000);

try {
  const result = await circuitBreaker.callService(params);
  console.log(result);
} catch (error) {
  // Handle the fallback action
}
```

In the above code, we define our `serviceCall` function, which represents making the actual remote service call. We create an instance of `CircuitBreaker` with the `serviceCall` function, a failure threshold of 3 (maximum 3 failures allowed), and a recovery time of 5000 milliseconds (5 seconds). We then make the service call using the `callService` method of the `circuitBreaker` instance. If the call succeeds, we log the result. If the call fails, we handle the fallback action.

## Conclusion

By implementing the Circuit Breaker pattern with fallback using promises, we can improve the resilience of our applications and handle failures in a more controlled manner. The Circuit Breaker pattern helps prevent cascading failures and provides a mechanism to recover from service outages.

Using promises in JavaScript makes the implementation of the Circuit Breaker pattern with fallback straightforward and more readable. Promises provide a cleaner way to handle asynchronous operations and handle errors.

Remember to choose the appropriate `failureThreshold` and `recoveryTime` values based on the characteristics of your system and the service you are calling.

## References
- [Circuit Breaker pattern](https://martinfowler.com/bliki/CircuitBreaker.html)
- [JavaScript Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)