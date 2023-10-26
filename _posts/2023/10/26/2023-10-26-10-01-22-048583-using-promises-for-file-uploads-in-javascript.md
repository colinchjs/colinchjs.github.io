---
layout: post
title: "Using promises for file uploads in Javascript"
description: " "
date: 2023-10-26
tags: [promises, promises]
comments: true
share: true
---

Uploading files in JavaScript can be a common task when building web applications. Newer JavaScript versions have introduced native Promise support, making it easier to handle asynchronous operations like file uploads. In this blog post, we'll explore how to use Promises for file uploads in JavaScript.

## Table of Contents
1. [Introduction to Promises](#introduction-to-promises)
2. [Uploading Files with Promises](#uploading-files-with-promises)
3. [Example Code](#example-code)
4. [Conclusion](#conclusion)

## Introduction to Promises

Promises are a valuable addition to JavaScript as they provide a more intuitive way to handle asynchronous operations. A Promise represents the eventual completion or failure of an asynchronous operation, and allows us to chain actions based on its result.

The Promise constructor takes a single function as an argument, which receives two parameters: `resolve`, used to indicate that the operation was successful, and `reject`, used to indicate that the operation failed. Promises have built-in methods like `.then()` and `.catch()` that allow us to handle the resolved or rejected states.

## Uploading Files with Promises

To upload a file using Promises, we can leverage the `fetch()` API, which is available in modern browsers. The `fetch()` function returns a Promise that resolves to the Response object representing the server's response.

First, we need to get the file data from an HTML input type of `file`. We can use the `FileReader` API to read the file contents. Then, we can create a new Promise and use the `fetch()` function to make a POST request to the server, sending the file data as the request body.

If the upload is successful, we can handle the response in the `.then()` method of the Promise. If there's an error, we can handle it in the `.catch()` method. This allows for a cleaner and more readable code structure.

## Example Code

Here's an example of how to upload a file using Promises in JavaScript:

```javascript
const fileInput = document.getElementById('file-input');

function uploadFile(file) {
  return new Promise((resolve, reject) => {
    const formData = new FormData();
    formData.append('file', file);

    fetch('/upload', {
      method: 'POST',
      body: formData
    })
      .then(response => {
        if (response.ok) {
          resolve('File uploaded successfully');
        } else {
          reject('Error uploading file');
        }
      })
      .catch(error => reject(error));
  });
}

fileInput.addEventListener('change', (event) => {
  const file = event.target.files[0];

  uploadFile(file)
    .then(response => console.log(response))
    .catch(error => console.error(error));
});
```

In the above code, we create a `uploadFile` function that returns a Promise. It creates a `FormData` object, appends the selected file, and uses the `fetch()` function to make a POST request to `/upload`. The response is then resolved or rejected based on the success status.

The event listener on the `fileInput` element waits for changes and triggers the file upload process when a new file is selected. The responses or errors are logged to the console.

## Conclusion

Using Promises for file uploads in JavaScript provides a cleaner and more maintainable approach. With Promises, we can handle the asynchronous nature of file uploads more easily, making the code more readable and reducing callback hell.

By leveraging the `fetch()` API and the Promise workflow, we can make file uploads in JavaScript more efficient and reliable.

[#javascript #promises](#javascript #promises)