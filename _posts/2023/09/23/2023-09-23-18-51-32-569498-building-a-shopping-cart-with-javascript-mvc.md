---
layout: post
title: "Building a shopping cart with JavaScript MVC"
description: " "
date: 2023-09-23
tags: []
comments: true
share: true
---

In today's digital era, e-commerce is at the forefront of business operations. A crucial aspect of any online store is a well-designed shopping cart. In this blog post, we will explore how to build a shopping cart using JavaScript Model-View-Controller (MVC) architecture.

## What is JavaScript MVC?

JavaScript MVC is an architectural pattern that helps organize code into three distinct components:

1. **Model**: The model represents the data and business logic of the application. In our case, it will hold information about the products added to the shopping cart.

2. **View**: The view handles the presentation layer and is responsible for rendering the user interface. It will display the products in the cart and allow users to interact with it.

3. **Controller**: The controller acts as the bridge between the model and the view. It receives user input and updates the model accordingly. It also updates the view based on changes in the model.

## Setting up the Project

Let's start by setting up a basic HTML skeleton and including the necessary JavaScript files:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Shopping Cart</title>
    <script src="model.js"></script>
    <script src="view.js"></script>
    <script src="controller.js"></script>
  </head>
  <body>
    <div id="shoppingCart"></div>
    <script>
      // Code to initialize the cart
      const cart = new Controller();
      cart.init();
    </script>
  </body>
</html>
```

## Implementing the Model

In the `model.js` file, we define our JavaScript class to represent the shopping cart model. It will have methods to add, remove, and update products in the cart:

```javascript
class Model {
  constructor() {
    this.products = [];
  }

  addProduct(product) {
    this.products.push(product);
  }

  removeProduct(product) {
    const index = this.products.indexOf(product);
    if (index > -1) {
      this.products.splice(index, 1);
    }
  }

  updateProduct(product, quantity) {
    product.quantity = quantity;
  }
}
```

## Creating the View

In the `view.js` file, we define our view class responsible for rendering the shopping cart UI. It will have methods to display the products and handle user interactions:

```javascript
class View {
  constructor(element) {
    this.element = element;
  }

  render(products) {
    this.element.innerHTML = '';
    products.forEach((product) => {
      const productElem = document.createElement('div');
      productElem.innerHTML = `
        <div>${product.name}</div>
        <div>${product.price}</div>
        <input type="number" value="${product.quantity}" onchange="controller.updateProduct(this, ${product.id})" />
        <button onclick="controller.removeProduct(${product.id})">Remove</button>
      `;
      this.element.appendChild(productElem);
    });
  }
}
```

## Implementing the Controller

In the `controller.js` file, we define our controller class responsible for handling user actions and updating the model and view accordingly:

```javascript
class Controller {
  constructor() {
    this.model = new Model();
    this.view = new View(document.getElementById('shoppingCart'));
  }

  init() {
    // Code to fetch products from the server and populate the model

    // Initial rendering of the view
    this.view.render(this.model.products);
  }

  addProduct(product) {
    this.model.addProduct(product);
    this.view.render(this.model.products);
  }

  removeProduct(id) {
    const product = this.model.products.find((p) => p.id === id);
    this.model.removeProduct(product);
    this.view.render(this.model.products);
  }

  updateProduct(input, id) {
    const product = this.model.products.find((p) => p.id === id);
    this.model.updateProduct(product, input.value);
    this.view.render(this.model.products);
  }
}
```

## Conclusion

Building a shopping cart with JavaScript MVC provides a structured approach to managing the data flow in an e-commerce application. By separating concerns into distinct components, it becomes easier to maintain and scale the codebase. Remember to consider the performance requirements of your application and optimize where necessary. With the code provided above, you have a solid foundation to build upon and create a robust shopping cart for your online store.

#javascript #mvc