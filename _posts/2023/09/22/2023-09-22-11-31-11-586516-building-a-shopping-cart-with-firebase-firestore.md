---
layout: post
title: "Building a shopping cart with Firebase Firestore"
description: " "
date: 2023-09-22
tags: [Firebase, Firestore]
comments: true
share: true
---

In this tutorial, we will explore how to build a shopping cart using Firebase Firestore. Firestore is a flexible and scalable NoSQL document database that integrates seamlessly with Firebase, making it a great choice for building modern web and mobile applications.

## Prerequisites

Before we get started, make sure you have the following:

- A Firebase project set up
- Firebase CLI installed

## Setting up Firestore

To use Firestore in your project, you need to enable it in the Firebase console. Follow these steps:

1. Go to the Firebase console and select your project.
2. Click on "Firestore Database" from the left-hand menu.
3. Click on "Create database" and choose the location.
4. Select "Start in test mode" for simplicity (you can secure it in production).

## Creating the Shopping Cart Schema

Now that Firestore is set up, we can define the schema for our shopping cart. We'll use two collections: `products` and `cartItems`.

### products collection

The `products` collection will store information about all available products. Each document in the collection will have the following fields:

- `name`: The name of the product.
- `price`: The price of the product.
- `quantity`: The available quantity of the product.

### cartItems collection

The `cartItems` collection will store information about the items in the shopping cart. Each document in the collection will have the following fields:

- `productId`: The ID of the product in the `products` collection.
- `quantity`: The quantity of the product in the cart.
- `userId`: The ID of the user who added the item to the cart.

## Building the Shopping Cart Functionality

To build the shopping cart functionality, we'll use Firebase Firestore and a frontend framework like React or Vue.js. The implementation will involve:

1. Displaying the list of products with their information from the `products` collection.
2. Adding the selected product to the `cartItems` collection with the user ID and quantity.
3. Updating the quantity of the selected product in the `products` collection.
4. Displaying the items in the shopping cart with their quantity and total price.
5. Updating the quantity or removing items from the cart.

### Example Code (React)

```jsx
import React, { useState, useEffect } from "react";
import { db } from "./firebase";

function ShoppingCart() {
  const [products, setProducts] = useState([]);
  const [cartItems, setCartItems] = useState([]);

  useEffect(() => {
    const unsubscribe = db.collection("products").onSnapshot((snapshot) => {
      const productsData = snapshot.docs.map((doc) => ({
        id: doc.id,
        ...doc.data(),
      }));
      setProducts(productsData);
    });

    return () => unsubscribe();
  }, []);

  const addToCart = (productId, quantity) => {
    db.collection("cartItems").add({
      productId,
      quantity,
      userId: "exampleUserId", // replace with actual user ID
    });
  };

  // rest of the code

  return (
    // JSX components for displaying products and cart items
  );
}

export default ShoppingCart;
```

## Conclusion

By leveraging the power of Firebase Firestore, we can easily build a shopping cart with real-time updates and seamless integration. It provides a scalable solution for managing and storing cart items across different users. Feel free to explore more features and customize your shopping cart based on your application's requirements.

#Firebase #Firestore