---
layout: post
title: "Creating and publishing private packages with package.json"
description: " "
date: 2023-09-17
tags: [privatepackages]
comments: true
share: true
---

When developing applications or libraries, it is common to separate reusable code into packages. While publishing packages publicly on platforms like npm is straightforward, there may be cases where you want to keep your code private, accessible only within your organization or specific projects. In this blog post, we will explore how to create and publish private packages using the package.json file.

### What is package.json?

The package.json file is a metadata file used in Node.js projects to manage dependencies, scripts, and other project configurations. It is commonly used to define the properties and settings of a package and its dependencies.

### Creating a Private Package

To create a private package, follow these steps:

1. Initialize a new Node.js project by running the following command in your project's root directory:

```bash
npm init
```

2. Follow the prompts to set up the package details such as name, version, description, and entry point. Pay attention to the "private" field and set it to `true`:

```json
{
  "name": "my-private-package",
  "version": "1.0.0",
  "description": "A private package example",
  "main": "index.js",
  "private": true,
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Your Name",
  "license": "MIT"
}
```

3. Inside your project's root directory, create the necessary files and folders for your package. Place your code, tests, and any other required files in the appropriate locations.

### Publishing a Private Package

To publish a private package, you can use the package registry provided by your organization or repository management services like GitHub Packages or Azure Artifacts. Here's an example of publishing a private package to GitHub Packages:

1. Create a Personal Access Token (PAT) on GitHub with the required permissions to read and write packages. Make sure to save the generated token securely.

2. Authenticate to GitHub Packages using your PAT by running the following command in your project's root directory:

```bash
npm login --registry=https://npm.pkg.github.com --scope=@<YOUR_GITHUB_USERNAME>
```

3. Publish your package by running the following command:

```bash
npm publish --access=public
```

Replace `public` with `restricted` if you want to limit the visibility to specific users or teams.

### Conclusion

Managing private packages with package.json enables you to encapsulate and share reusable code within your organization or projects. By setting the "private" field to `true`, you ensure that your package doesn't get accidentally published to public registries. With the flexibility of repository management services like GitHub Packages, you can easily establish a private package registry and control access to your packages.

#npm #privatepackages