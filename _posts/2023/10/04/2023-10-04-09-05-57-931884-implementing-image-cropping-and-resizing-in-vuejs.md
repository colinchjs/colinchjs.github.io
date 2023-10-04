---
layout: post
title: "Implementing image cropping and resizing in Vue.js"
description: " "
date: 2023-10-04
tags: [introduction), getting]
comments: true
share: true
---

In this tutorial, we will explore how to implement image cropping and resizing functionality in a Vue.js application. Cropping and resizing images is a common requirement in many web applications, especially those that involve user-uploaded images.

## Table of Contents
- [Introduction](#introduction)
- [Getting Started](#getting-started)
- [Installing Dependencies](#installing-dependencies)
- [Setting Up the Cropping Component](#setting-up-the-cropping-component)
- [Cropping the Image](#cropping-the-image)
- [Resizing the Image](#resizing-the-image)
- [Conclusion](#conclusion)

## Introduction

The ability to crop and resize images is essential for applications that involve displaying images in various layouts or aspect ratios, such as profile pictures, thumbnails, or banners. Using a cropping and resizing feature allows users to customize their images to fit specific requirements.

In our example, we will use a popular image manipulation library called [Cropper.js](https://github.com/fengyuanchen/cropperjs) to handle the cropping functionality and [vue-image-size](https://github.com/adamdbradley/vue-image-size) library to get the original image's dimensions for resizing. 

## Getting Started

First, let's create a new Vue.js project using the Vue CLI. Open your terminal and run the following command:

```bash
vue create image-cropper
```

Choose the default preset and wait for the project to be created.

## Installing Dependencies

Next, install the required dependencies by running the following commands in your project's root directory:

```bash
cd image-cropper
npm install cropperjs vue-image-size
```

## Setting Up the Cropping Component

Create a new file called `ImageCropper.vue` in the `src/components` directory and add the following code:

```html
<template>
  <div>
    <input type="file" @change="onInputChange" accept="image/*" />
    <img ref="image" />
  </div>
</template>

<script>
import Cropper from 'cropperjs';
import { setImageSize } from 'vue-image-size';

export default {
  mounted() {
    this.$refs.image.onload = () => {
      this.cropper = new Cropper(this.$refs.image, {
        aspectRatio: 16 / 9,
        crop: this.onCrop,
      });
    };
  },
  methods: {
    onInputChange(e) {
      const file = e.target.files[0];
      setImageSize(file).then((size) => {
        const reader = new FileReader();
        reader.onload = (event) => {
          this.$refs.image.src = event.target.result;
        };
        reader.readAsDataURL(file);
        this.cropper.setAspectRatio(size.width / size.height);
      });
    },
    onCrop(event) {
      const canvas = this.cropper.getCroppedCanvas();
      // handle cropped image
    },
  },
};
</script>
```

In this code, we have created a basic component that consists of an input element for file selection and an img element for displaying the selected image.

We import the `Cropper` class from the `cropperjs` library and the `setImageSize` function from the `vue-image-size` library. Inside the `mounted` lifecycle hook, we create a new instance of `Cropper` by passing the img element and specifying the **aspect ratio** and the **callback function** to be called when cropping is done.

The `onInputChange` method is triggered when a file is selected. It reads the selected file, sets the `src` of the img element to the base64 data URL of the file, and sets the aspect ratio of the Cropper instance based on the dimensions of the original image.

The `onCrop` method is called when a user finishes cropping. Inside this method, you can handle the cropped image as per your application's requirements.

## Cropping the Image

Now that we have set up the Cropper component, we can add it to another component or a page in our application. For example, let's assume we have a component called `ProfilePictureUploader.vue` where we want to implement the image cropping functionality.

Open the `ProfilePictureUploader.vue` file, add the following code to import and use the `ImageCropper` component:

```html
<template>
  <div>
    <h1>Profile Picture Uploader</h1>
    <image-cropper />
  </div>
</template>

<script>
import ImageCropper from "@/components/ImageCropper.vue";

export default {
  components: {
    ImageCropper,
  },
};
</script>
```

In this example, we import the `ImageCropper` component and include it inside the `<image-cropper />` tag.

## Resizing the Image

To implement image resizing functionality, we can use the [`canvas.toDataURL`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLCanvasElement/toDataURL) method to get the base64-encoded image data. We can then create a new `Image` element in memory, set its `src` to the data URL, and adjust its dimensions.

Inside the `onCrop` method of the `ImageCropper` component, add the following code to resize the image:

```javascript
const canvas = this.cropper.getCroppedCanvas();

// Get the resized image data URL
const resizedDataURL = canvas.toDataURL('image/jpeg', 0.8);

// Create a new image element for resizing
const resizedImage = new Image();
resizedImage.onload = () => {
  // handle resized image
};
resizedImage.src = resizedDataURL;
```

In this example, we call `getCroppedCanvas` on the Cropper instance to get the cropped canvas. Then, we use `toDataURL` to get the base64-encoded image data with the desired image format and quality. We create a new `Image` element and set its `src` to the resized data URL. Finally, we handle the resized image inside the `onload` callback function.

## Conclusion

In this tutorial, we have learned how to implement image cropping and resizing functionality in a Vue.js application using the Cropper.js library. We set up a cropping component, integrated it into our application, and demonstrated how to handle the cropped and resized images.

By leveraging the power of Vue.js and the Cropper.js library, you can provide a user-friendly image manipulation experience in your web applications. Experiment with different options and enhancements to tailor the cropping and resizing functionality to your specific requirements.