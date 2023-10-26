---
layout: post
title: "Implementing a progress indicator with promises"
description: " "
date: 2023-10-26
tags: [JavaScript, Promises]
comments: true
share: true
---

In modern web development, asynchronous operations are very common. Promises are a JavaScript feature that provide a way to handle asynchronous code in a more elegant and readable manner. However, sometimes it is necessary to provide users with feedback on the progress of these operations. In this blog post, we will explore how to implement a progress indicator using promises in JavaScript.

## The Problem

Let's say we have a long running asynchronous operation, such as uploading a large file to a server. This operation might take several seconds or even minutes to complete. We want to show the user a progress indicator to let them know that the operation is still ongoing.

## The Solution

To implement a progress indicator with promises, we can take advantage of the `Promise` constructor and the built-in `fetch` function for making network requests.

1. Create a function that accepts a URL and returns a promise. This function will perform the long running operation (e.g., uploading a file) and periodically update the progress.

```javascript
function uploadFile(url) {
  return new Promise((resolve, reject) => {
    const xhr = new XMLHttpRequest();

    xhr.upload.addEventListener("progress", event => {
      if (event.lengthComputable) {
        const progress = (event.loaded / event.total) * 100;
        console.log(`Progress: ${progress}%`);
      }
    });

    xhr.addEventListener("load", () => {
      if (xhr.status >= 200 && xhr.status < 300) {
        resolve(xhr.responseText);
      } else {
        reject(new Error(`Request failed with status ${xhr.status}`));
      }
    });

    xhr.addEventListener("error", () => {
      reject(new Error("Request failed"));
    });

    xhr.open("POST", url, true);
    xhr.send();
  });
}
```

2. Use the `uploadFile` function to handle the file upload and update the progress indicator.

```javascript
const fileInput = document.getElementById("file-input");
const uploadButton = document.getElementById("upload-button");
const progressBar = document.getElementById("progress-bar");

uploadButton.addEventListener("click", () => {
  const file = fileInput.files[0];
  const url = "/upload";

  uploadFile(url)
    .then(response => {
      console.log("Upload complete: ", response);
    })
    .catch(error => {
      console.error("Upload failed: ", error);
    });
});
```

3. Update the progress indicator as the upload progresses.

```javascript
xhr.upload.addEventListener("progress", event => {
  if (event.lengthComputable) {
    const progress = (event.loaded / event.total) * 100;
    progressBar.style.width = `${progress}%`;
  }
});
```

By using the `Promise` constructor and the progress event provided by the `XMLHttpRequest` object, we can easily implement a progress indicator for asynchronous operations. The `uploadFile` function returns a promise that resolves when the upload is complete and rejects if there is an error. The progress event listener updates the progress bar on every progress event.

## Conclusion

Implementing a progress indicator with promises allows us to provide users with real-time feedback on long running operations. The combination of promises and progress events provides a powerful and elegant way to handle asynchronous code in JavaScript. By following the steps outlined in this blog post, you can easily implement a progress indicator in your own applications.

# References
- [MDN Web Docs - Using Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [MDN Web Docs - XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [MDN Web Docs - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)

#hashtags: #JavaScript #Promises