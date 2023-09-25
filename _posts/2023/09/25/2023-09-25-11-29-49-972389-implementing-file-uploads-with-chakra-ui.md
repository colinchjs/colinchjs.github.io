---
layout: post
title: "Implementing file uploads with Chakra UI"
description: " "
date: 2023-09-25
tags: [react, fileupload]
comments: true
share: true
---

In this tutorial, we will explore how to implement file uploads using the Chakra UI library. Chakra UI is a simple and customizable UI component library for React. Using Chakra UI, we can easily create a user-friendly file upload component in just a few steps.

## Prerequisites
Before we get started, make sure you have the following prerequisites:
- Basic knowledge of React and JavaScript
- Node.js and npm installed on your machine


## Setting Up Chakra UI
First, let's set up a new React project with Chakra UI. Open your terminal and navigate to the directory where you want to create the project. Run the following commands:

```shell
npx create-react-app file-upload-chakra
cd file-upload-chakra
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

Chakra UI requires Emotion as its styling engine, so we need to install it along with the necessary dependencies.


## Setting Up File Upload Component
Next, let's create a new file called `FileUploader.js` in the `src` directory. Open the file and add the following code:

```javascript
import { Box, Button } from '@chakra-ui/react';

const FileUploader = ({ onFileSelect }) => {
  const fileInputRef = useRef(null);

  const handleFileSelect = () => {
    fileInputRef.current.click();
  };

  const handleFileInputChange = (e) => {
    const file = e.target.files[0];
    onFileSelect(file);
  };

  return (
    <Box>
      <Button onClick={handleFileSelect}>Select File</Button>
      <input
        type="file"
        ref={fileInputRef}
        style={{ display: 'none' }}
        onChange={handleFileInputChange}
      />
    </Box>
  );
};

export default FileUploader;
```

In the code above, we have created a reusable `FileUploader` component that displays a `Select File` button. When the button is clicked, it triggers the file input selection by programmatically clicking the hidden file input element. The selected file is then passed to the `onFileSelect` callback function provided as a prop.

Make sure to save the file.


## Using the File Upload Component
Now let's use the `FileUploader` component in our `App.js` file. Open `src/App.js` and replace the default code with the following:

```javascript
import { ChakraProvider } from '@chakra-ui/react';
import FileUploader from './FileUploader';

function App() {
  const handleFileSelect = (file) => {
    // Handle the selected file here
    console.log(file);
  };

  return (
    <ChakraProvider>
      <div className="App">
        <FileUploader onFileSelect={handleFileSelect} />
      </div>
    </ChakraProvider>
  );
}

export default App;
```

In the code above, we import the `ChakraProvider` from Chakra UI to wrap our entire application. Then, we import and render the `FileUploader` component, passing the `handleFileSelect` function as a prop to handle the selected file.

## Conclusion
That's it! You have successfully implemented file uploads using Chakra UI. Now you can further customize the file uploader component according to your needs.

Chakra UI provides a rich set of components that can be easily styled and customized. You can explore the Chakra UI documentation to learn more about available components and their usage.

#react #fileupload