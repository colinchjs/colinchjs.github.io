---
layout: post
title: "Implementing real-time logging with Azure Event Hubs in Node.js"
description: " "
date: 2023-10-01
tags: [azure, logging]
comments: true
share: true
---

In this blog post, we will explore how to implement real-time logging with Azure Event Hubs in a Node.js application. Azure Event Hubs is a scalable and highly available event streaming platform that enables you to build real-time applications and process large amounts of data in real-time.

## Prerequisites

Before getting started, make sure you have the following:

- Node.js installed on your machine
- An Azure subscription
- An Azure Event Hubs namespace and Event Hub created

## Setting up the Node.js application

To begin, let's set up a basic Node.js application. Create a new directory for your project and navigate to it using the terminal.

```javascript
npm init -y
```

This command initializes a new Node.js project with default settings.

Install the required package for connecting to Azure Event Hubs:

```javascript
npm install @azure/event-hubs
```

This package provides a client library for interacting with Azure Event Hubs from Node.js.

## Sending real-time logs to Azure Event Hubs

Now, let's implement the code to send real-time logs to Azure Event Hubs.

First, import the necessary modules and instantiate an `EventHubProducerClient`:

```javascript
const { EventHubProducerClient } = require("@azure/event-hubs");

const connectionString = "YOUR_EVENT_HUBS_CONNECTION_STRING";
const eventHubName = "YOUR_EVENT_HUB_NAME";

async function sendLogs() {
  const producerClient = new EventHubProducerClient(connectionString, eventHubName);

  // Your code to send logs

  await producerClient.close();
}

sendLogs();
```

Replace `YOUR_EVENT_HUBS_CONNECTION_STRING` and `YOUR_EVENT_HUB_NAME` with your actual Event Hubs connection string and Event Hub name.

To send logs, use the `sendBatch` method of the `EventHubProducerClient`:

```javascript
const logs = ["Log 1", "Log 2", "Log 3"];

async function sendLogs() {
  // ...

  const batchOptions = {
    partitionKey: "YOUR_PARTITION_KEY"
  };

  const batch = await producerClient.createBatch(batchOptions);

  for (const log of logs) {
    if (!batch.tryAdd({ body: log })) {
      await producerClient.sendBatch(batch);
      batch.clear();

      if (!batch.tryAdd({ body: log })) {
        throw new Error(`Unable to add log ${log}`);
      }
    }
  }

  await producerClient.sendBatch(batch);

  // ...
}

sendLogs();
```

Replace `YOUR_PARTITION_KEY` with a value to determine which partition to send the logs to.

## Receiving real-time logs from Azure Event Hubs

To receive the logs in real-time, we need to create a consumer client.

First, import the necessary modules and instantiate an `EventHubConsumerClient`:

```javascript
const {
  EventHubConsumerClient,
  earliestEventPosition,
  latestEventPosition,
} = require("@azure/event-hubs");

async function receiveLogs() {
  const consumerGroup = "$Default";
  const consumerClient = new EventHubConsumerClient(consumerGroup, connectionString, eventHubName);

  // Your code to receive logs

  await consumerClient.close();
}

receiveLogs();
```

Replace `YOUR_EVENT_HUBS_CONNECTION_STRING` and `YOUR_EVENT_HUB_NAME` with your actual Event Hubs connection string and Event Hub name.

To receive logs, use the `subscribe` method of the `EventHubConsumerClient`:

```javascript
async function receiveLogs() {
  // ...

  const subscription = consumerClient.subscribe({
    processEvents: async (events, context) => {
      for (const event of events) {
        console.log(event.body);
      }

      await context.updateCheckpoint(events[events.length - 1]);
    },
    processError: async (error, context) => {
      console.error(error);
    }
  });

  // ...
}

receiveLogs();
```

This code will continuously receive and log the events from the Event Hub. You can perform any custom logic on the received logs within the `processEvents` function.

## Conclusion

In this tutorial, we learned how to implement real-time logging with Azure Event Hubs in a Node.js application. We covered how to send logs to Azure Event Hubs and how to receive logs in real-time using the Event Hub client libraries.

By leveraging the power of Azure Event Hubs, you can build scalable and real-time logging solutions for your Node.js applications. Start exploring Azure Event Hubs and unleash the full potential of real-time event streaming.

#azure #logging