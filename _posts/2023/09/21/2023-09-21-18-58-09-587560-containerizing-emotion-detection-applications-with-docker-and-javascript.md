---
layout: post
title: "Containerizing emotion detection applications with Docker and Javascript"
description: " "
date: 2023-09-21
tags: [dockerize, emotiondetection]
comments: true
share: true
---

Emotion detection is a popular application that utilizes machine learning algorithms to recognize and analyze human emotions based on facial expressions. Containerizing such applications with Docker allows for portability, scalability, and easy deployment across different environments.

In this blog post, we will explore how to containerize an emotion detection application using Docker and Javascript. We will start by setting up a basic emotion detection application, then proceed to containerize it with Docker for efficient deployment.

## Setting up the Emotion Detection Application

First, let's set up a basic emotion detection application using Javascript. We'll utilize the Face-api.js library, which provides face detection and emotion recognition capabilities.

1. Start by creating a new directory for your project and navigate into it:
```javascript
mkdir emotion-detection-app
cd emotion-detection-app
```

2. Initialize a new npm project and install the required dependencies:
```javascript
npm init -y
npm install face-api.js
```

3. Create an `index.html` file and include the necessary Javascript and CSS files:
```html
<!DOCTYPE html>
<html>
<head>
    <title>Emotion Detection App</title>
    <link rel="stylesheet" type="text/css" href="face-api.min.css">
</head>
<body>
    <h1>Emotion Detection App</h1>
    <video id="video" width="640" height="480" autoplay></video>
    <canvas id="canvas" width="640" height="480"></canvas>

    <script src="face-api.min.js"></script>
    <script src="app.js"></script>
</body>
</html>
```

4. Create an `app.js` file and write Javascript code to capture video stream, detect faces, and recognize emotions:
```javascript
const video = document.getElementById('video');
const canvas = document.getElementById('canvas');
const ctx = canvas.getContext('2d');

navigator.mediaDevices.getUserMedia({ video: true })
    .then(stream => {
        video.srcObject = stream;
    }).catch(error => {
        console.error('Error accessing webcam!', error);
    });

video.addEventListener('play', () => {
    setInterval(async () => {
        ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
        const faces = await faceapi.detectAllFaces(video).withFaceExpressions();

        faces.forEach(face => {
            const {x, y, width, height} = face.detection.box;
            const expressions = face.expressions;

            // Draw rectangle around face
            ctx.beginPath();
            ctx.lineWidth = 2;
            ctx.strokeStyle = 'red';
            ctx.rect(x, y, width, height);
            ctx.stroke();

            // Display predicted emotion
            const sortedEmotions = Object.entries(expressions)
                .sort(([, a], [, b]) => b - a);
            const [emotion, score] = sortedEmotions[0];
            ctx.fillStyle = 'white';
            ctx.fillText(`${emotion}: ${score}`, x, y > 10 ? y - 5 : y + height + 15);
        });
    }, 200);
});
```

## Containerizing with Docker

Now that we have set up our emotion detection application, let's containerize it with Docker for easy deployment and management.

1. Create a `Dockerfile` in the root directory of your project:
```Dockerfile
FROM node:14

WORKDIR /app
COPY package*.json ./

RUN npm install

COPY . .

CMD [ "npm", "start" ]
```

2. Build the Docker image:
```
docker build -t emotion-detection .
```

3. Run the Docker container:
```
docker run -p 3000:3000 emotion-detection
```

4. Access the application in your browser by navigating to `http://localhost:3000`.

## Conclusion

By containerizing the emotion detection application with Docker, we have achieved portability and scalability, making it easier to deploy and manage the application across different environments. Docker enables us to package all the dependencies and configurations into a single container, eliminating compatibility issues and streamlining the deployment process.

By following the steps outlined in this blog post, you can containerize your own applications and take advantage of the benefits offered by Docker. Try containerizing your favorite applications and experience the ease of deployment and management for yourself!

#dockerize #emotiondetection