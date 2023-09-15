---
layout: post
title: "Implementing neural networks with JavaScript iterators"
description: " "
date: 2023-09-15
tags: [webdevelopment, machinelearning]
comments: true
share: true
---

Neural networks are powerful algorithms used in machine learning to solve complex problems like image recognition, natural language processing, and more. Traditionally, implementing neural networks required understanding complex mathematical operations and manually manipulating matrices. But with the rise of high-level programming languages like JavaScript, we can now implement neural networks using iterators, making the process more intuitive and less error-prone.

## Neural networks at a glance

Before we dive into the implementation details, let's quickly understand the basics of neural networks. A neural network is composed of interconnected layers of artificial neurons, called perceptrons. Each perceptron takes one or more inputs, applies a specific function called an activation function, and produces an output. The outputs from one layer are then passed as inputs to the next layer until the final output is obtained.

## Implementing neural networks with JavaScript iterators

JavaScript comes with built-in iterators, which are objects that allow us to loop over a collection of values. By leveraging iterators, we can easily implement the forward propagation step of a neural network, which calculates the output for a given set of inputs.

Let's start by defining a class called `NeuralNetwork`:

```javascript
class NeuralNetwork {
  constructor(weights, activation) {
    this.weights = weights;
    this.activation = activation;
  }

  *forwardPropagation(inputs) {
    let outputs = inputs;

    for (const layerWeights of this.weights) {
      outputs = layerWeights.map((weights, neuronIndex) => {
        const weightedSum = weights.reduce((sum, weight, inputIndex) => sum + weight * outputs[inputIndex], 0);
        return this.activation(weightedSum);
      });

      yield outputs;
    }
  }
}
```

In the above code, the `NeuralNetwork` constructor takes two arguments: `weights`, which represents the weights of each perceptron in each layer, and `activation`, which is the activation function to be applied. The `forwardPropagation` method implements the forward propagation process using an iterator.

Within the iterator loop, we calculate the weighted sum for each neuron in a layer by multiplying the inputs with the respective weights and summing them up. We then pass this sum through the activation function to obtain the output of each neuron. The outputs are stored in the `outputs` variable and yielded using the `yield` keyword.

Now, let's use our implemented neural network:

```javascript
const weights = [
  [[0.8, 0.2], [0.4, 0.6]],   // weights for layer 1 (2 neurons)
  [[0.3, 0.7]]                // weights for layer 2 (1 neuron)
];

const activation = (x) => 1 / (1 + Math.exp(-x)); // sigmoid activation function

const neuralNetwork = new NeuralNetwork(weights, activation);

const inputs = [0.5, 0.3]; // input values

for (const output of neuralNetwork.forwardPropagation(inputs)) {
  console.log(output);
}
```

In the above code, we create an instance of `NeuralNetwork` by providing the weights and the activation function. We also define the input values. By iterating over the `forwardPropagation` method, we can retrieve the outputs for each layer of the neural network.

## Conclusion

By leveraging JavaScript iterators, implementing neural networks becomes more intuitive and less error-prone. The example code provided demonstrates a simplified implementation of forward propagation. You can further extend this implementation to include backpropagation and train the network on a dataset. With JavaScript's flexibility and the power of neural networks, you can explore and solve exciting real-world problems. Happy coding!

#webdevelopment #machinelearning