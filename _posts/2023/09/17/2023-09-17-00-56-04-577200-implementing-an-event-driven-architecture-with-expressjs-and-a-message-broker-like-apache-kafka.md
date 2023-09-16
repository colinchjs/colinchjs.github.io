---
layout: post
title: "Implementing an event-driven architecture with Express.js and a message broker like Apache Kafka"
description: " "
date: 2023-09-17
tags: [eventdriven, expressjs, apachekafka]
comments: true
share: true
---

In recent years, event-driven architectures have gained popularity in designing scalable and loosely coupled systems. Event-driven architecture allows components to communicate asynchronously through events, enabling better modularity, extensibility, and maintainability.

In this blog post, we will explore how to implement an event-driven architecture with Express.js and Apache Kafka, a popular distributed messaging system. We will build a simple example to demonstrate how events can be produced and consumed using Kafka.

## Prerequisites

To follow along with this tutorial, you will need:

- Node.js and npm installed on your machine.
- An Apache Kafka cluster set up. You can install Kafka locally using the official documentation or use a cloud-based Kafka provider like Confluent Cloud.

## Setting Up the Project

Let's start by setting up a new Express.js project and installing the necessary dependencies.

1. Create a new directory for your project and navigate into it:
```bash
$ mkdir express-kafka-example
$ cd express-kafka-example
```

2. Initialize a new npm project:
```bash
$ npm init -y
```

3. Install the required dependencies:
```bash
$ npm install express kafka-node
```

## Producing Events

First, let's set up a basic Express.js server that will produce events.

1. Create a new file named `producer.js`:

```javascript
const express = require('express');
const app = express();
const kafka = require('kafka-node');
const Producer = kafka.Producer;
const client = new kafka.KafkaClient();
const producer = new Producer(client);
const topic = 'example-topic';

app.get('/', (req, res) => {
  const message = 'Hello, Kafka!';

  const payloads = [
    {
      topic: topic,
      messages: message
    }
  ];

  producer.send(payloads, (err, data) => {
    if (err) {
      console.error('Error sending event:', err);
      res.status(500).send('Error sending event');
    } else {
      console.log('Event sent:', data);
      res.status(200).send('Event sent successfully');
    }
  });
});

app.listen(3000, () => {
  console.log('Producer server listening on port 3000');
});
```

2. Start the producer server:
```bash
$ node producer.js
```

Now, if you navigate to `http://localhost:3000` in your browser, the server will produce an event to the Kafka cluster.

## Consuming Events

Next, let's build a consumer that will consume events from the same Kafka topic.

1. Create another file named `consumer.js`:

```javascript
const kafka = require('kafka-node');
const Consumer = kafka.Consumer;
const client = new kafka.KafkaClient();
const consumer = new Consumer(client, [
  {
    topic: 'example-topic'
  }
]);

consumer.on('message', (message) => {
  console.log('Received event:', message.value);
});

console.log('Consumer listening for events');
```

2. Start the consumer:
```bash
$ node consumer.js
```

Now, whenever an event is produced by the Express.js server, the consumer will receive and log the event message in the console.

## Conclusion

In this blog post, we have seen how to implement an event-driven architecture using Express.js and Apache Kafka. We explored how to produce events from an Express.js server and consume them using a Kafka consumer. This architecture allows for loose coupling and scalability, making it easier to build robust and extensible systems.

By leveraging the power of event-driven architectures, you can design systems that are more resilient, scalable, and maintainable. So go ahead and experiment with event-driven approaches in your projects to unlock their full potential!

#eventdriven #expressjs #apachekafka