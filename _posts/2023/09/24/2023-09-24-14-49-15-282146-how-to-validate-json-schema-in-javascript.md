---
layout: post
title: "How to validate JSON schema in JavaScript."
description: " "
date: 2023-09-24
tags: [JSON]
comments: true
share: true
---

JSON Schema is a powerful tool for validating and describing the structure of JSON data. In JavaScript, there are several libraries available that make it easy to validate JSON data against a JSON schema. In this blog post, we'll explore one such library called `ajv`.

## What is JSON Schema?

JSON Schema is a vocabulary that allows you to annotate and validate JSON documents. It provides a way to describe the expected structure, format, and constraints of JSON data.

## Using the `ajv` Library

`ajv` is a fast and powerful JSON schema validator for Node.js and browsers. To get started, you'll need to install `ajv` using a package manager such as npm or yarn:

```shell
npm install ajv
```

Once installed, you can use `ajv` to validate JSON data against a JSON schema. Here's an example:

```javascript
const Ajv = require("ajv");
const ajv = new Ajv();

// Define a JSON schema
const schema = {
  type: "object",
  properties: {
    name: { type: "string" },
    age: { type: "number" },
    email: { type: "string", format: "email" }
  },
  required: ["name", "age"]
};

// Compile the schema
const validate = ajv.compile(schema);

// Validate JSON data
const data = {
  name: "John Doe",
  age: 30,
  email: "john@example.com"
};

const isValid = validate(data);

if (isValid) {
  console.log("Data is valid");
} else {
  console.log("Data is invalid");
  console.log(validate.errors);
}
```

In the above code, we first require the `ajv` module and create an instance of the `Ajv` class. We then define a JSON schema that describes the expected structure of the JSON data. Next, we compile the schema using `ajv.compile()` and obtain a validation function. Finally, we pass the JSON data to the validation function and check the result.

## Conclusion

Validating JSON data against a JSON schema is an important step in ensuring data integrity. Using libraries like `ajv`, JavaScript developers can easily validate JSON data and handle validation errors. By leveraging the power of JSON Schema, you can build more robust and reliable applications.

#JSON #JavaScript #JSONSchema #Validation #ajv