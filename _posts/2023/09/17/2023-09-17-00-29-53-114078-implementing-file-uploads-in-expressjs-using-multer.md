---
layout: post
title: "Implementing file uploads in Express.js using multer"
description: " "
date: 2023-09-17
tags: [ExpressJs, FileUploads]
comments: true
share: true
---

File uploads are a common requirement for many web applications. If you are building a web application using Express.js, you can easily handle file uploads using the `multer` middleware.

## What is multer?

`multer` is a middleware for handling `multipart/form-data`, which is commonly used for file uploads. It allows you to handle file uploads and save them to a specified location on the server.

## Getting started

To use `multer`, you need to install it as a dependency in your Express.js project. Open your terminal and navigate to your project directory, then run the following command:

```bash
npm install multer
```

Once `multer` is installed, let's integrate it into our Express.js application.

## Setting up multer

First, we need to require `multer` and set up a storage destination for our uploaded files. Create a new file, `upload.js`, and add the following code:

```javascript
const multer = require('multer');

const storage = multer.diskStorage({
  destination: function (req, file, cb) {
    cb(null, 'uploads/') // specify the destination folder for uploaded files
  },
  filename: function (req, file, cb) {
    cb(null, Date.now() + '-' + file.originalname) // set a unique filename for the uploaded file
  }
});

const upload = multer({ storage: storage });

module.exports = upload; // export the multer configuration for use in other files
```

In this code, we set up the storage configuration for `multer`. The `destination` function specifies the folder where the uploaded files will be saved, and the `filename` function generates a unique filename for each uploaded file.

## Implementing file upload routes

Now that we have set up `multer`, let's create a route in our Express.js application to handle file uploads. In your main router file, add the following code:

```javascript
const express = require('express');
const router = express.Router();
const upload = require('./upload'); // import the multer configuration

// POST route for file upload
router.post('/upload', upload.single('file'), (req, res) => {
  // handle the uploaded file here
  res.status(200).send('File uploaded successfully.');
});

module.exports = router;
```

In this code, we define a POST route at the `/upload` endpoint. We use the `upload.single()` function from `multer` to handle the upload of a single file. The `'file'` parameter in `upload.single()` specifies the name attribute of the file input field in the HTML form.

## HTML form for file upload

To test our file upload functionality, we need to create an HTML form in a view file. Add the following code to your view file:

```html
<form action="/upload" method="POST" enctype="multipart/form-data">
  <input type="file" name="file" />
  <button type="submit">Upload</button>
</form>
```

In this code, we create a form with an input field of type `file`. The `enctype="multipart/form-data"` attribute is important to enable file uploads.

## Conclusion

With `multer`, handling file uploads in Express.js becomes a breeze. You can now easily receive and save uploaded files in your application. This capability opens up a wide range of possibilities for building file upload functionality in your web applications.

#ExpressJs #FileUploads