---
layout: post
title: "Creating a custom useMediaRecorder hook for recording media"
description: " "
date: 2023-10-11
tags: [react, mediarecorder]
comments: true
share: true
---

In this tutorial, we will create a custom React hook called `useMediaRecorder` that provides a simple way to record media using the browser's MediaRecorder API. This hook will make it easy to handle media recording functionality in your React applications.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Setting up the project](#setting-up-the-project)
- [Creating the useMediaRecorder hook](#creating-the-usemediarecorder-hook)
- [Using the useMediaRecorder hook](#using-the-usemediarecorder-hook)
- [Conclusion](#conclusion)

## Prerequisites
Make sure you have the latest version of Node.js and npm installed on your system. You should also have a basic understanding of React and its hooks.

## Setting up the project
Let's start by setting up a new React project using Create React App. Open your terminal and run the following command:

```
npx create-react-app media-recorder-app
cd media-recorder-app
```

## Creating the useMediaRecorder hook
Create a new file called `useMediaRecorder.js` in the `src` directory. This file will contain the implementation of our custom hook.

```javascript
import { useState, useEffect } from 'react';

const useMediaRecorder = () => {
  const [isRecording, setIsRecording] = useState(false);
  const [mediaChunks, setMediaChunks] = useState([]);
  const [mediaBlob, setMediaBlob] = useState(null);
  const [errorMessage, setErrorMessage] = useState('');

  let mediaRecorder;

  useEffect(() => {
    const startRecording = () => {
      setIsRecording(true);
      setMediaChunks([]);
      setMediaBlob(null);

      navigator.mediaDevices.getUserMedia({ audio: true, video: true })
        .then(stream => {
          mediaRecorder = new MediaRecorder(stream);
          mediaRecorder.ondataavailable = (e) => {
            if (e.data.size > 0) {
              setMediaChunks(prevChunks => [...prevChunks, e.data]);
            }
          };
          mediaRecorder.onstop = () => {
            const blob = new Blob(mediaChunks, { type: mediaChunks[0].type });
            setMediaBlob(blob);
            setIsRecording(false);
          };
          mediaRecorder.start();
        })
        .catch(error => {
          setErrorMessage('Failed to access media devices');
          setIsRecording(false);
        });
    };

    const stopRecording = () => {
      if (mediaRecorder) {
        mediaRecorder.stop();
      }
    };

    return () => {
      if (mediaRecorder && mediaRecorder.state === 'recording') {
        mediaRecorder.stop();
      }
    };
  }, [mediaChunks]);

  return { isRecording, mediaBlob, startRecording, stopRecording, errorMessage };
};

export default useMediaRecorder;
```

In this hook, we utilize the `useState` and `useEffect` hooks from React. We maintain several state variables: `isRecording`, `mediaChunks`, `mediaBlob`, and `errorMessage`. The `isRecording` state is used to track whether recording is currently in progress. `mediaChunks` stores the media data chunks as they are recorded. `mediaBlob` is the final recorded media blob that can be used for further processing. `errorMessage` holds any error message encountered during recording.

Inside the `useEffect` hook, we define functions to start and stop the recording. We also handle the scenarios where the recording is manually stopped by the user or when the component unmounts. The hook uses the `getUserMedia` API to request access to audio and video devices and creates a `MediaRecorder` instance to handle the recording.

## Using the useMediaRecorder hook
Now let's use the `useMediaRecorder` hook in a component to see it in action. Open the `src/App.js` file and replace the existing code with the following:

```javascript
import React from 'react';
import useMediaRecorder from './useMediaRecorder';

const App = () => {
  const { isRecording, mediaBlob, startRecording, stopRecording, errorMessage } = useMediaRecorder();

  return (
    <div>
      <button onClick={startRecording} disabled={isRecording}>
        {isRecording ? 'Recording...' : 'Start recording'}
      </button>
      <button onClick={stopRecording} disabled={!isRecording}>
        Stop recording
      </button>
      {errorMessage && <p>{errorMessage}</p>}
      {mediaBlob && (
        <video
          src={URL.createObjectURL(mediaBlob)}
          controls
          style={{ marginTop: '20px' }}
        />
      )}
    </div>
  );
};

export default App;
```

In this component, we destructure the returned values from the `useMediaRecorder` hook. We provide a simple user interface with two buttons: "Start recording" and "Stop recording". The `isRecording` variable is used to enable or disable the buttons accordingly. The `mediaBlob` variable is used to display the recorded media as a video element when available. If any error occurs during recording, it will be displayed as a paragraph.

Save the changes and run the application with the following command:

```
npm start
```

You should now see the application running in your browser. Click the "Start recording" button to start recording your audio and video. Once you stop recording, the recorded media will be displayed as a video element.

## Conclusion
In this tutorial, we have created a custom React hook called `useMediaRecorder` that provides a simple way to record media using the browser's MediaRecorder API. This hook allows for easy integration of media recording functionality into your React applications. Feel free to extend the hook to handle additional recording options or apply further processing to the recorded media. Happy coding!

\#react #mediarecorder