---
layout: post
title: "How to create a custom registry in package.json"
description: " "
date: 2023-09-17
tags: [registry]
comments: true
share: true
---

When working with Node.js and npm, the package registry is an essential component that allows you to manage and distribute your packages. By default, npm uses the public npm registry to install packages. However, there may be cases where you want to publish your packages to a custom registry, such as an internal company registry or a private registry.

In this blog post, we will guide you through the steps to create a custom registry in the `package.json` file. This will allow you to install and publish packages to your own private registry.

## Step 1: Initializing a new package

To get started, you need to have a Node.js project with an existing `package.json` file. If you don't have one yet, you can create a new package by running the following command in your project directory:

```
npm init
```

This command will prompt you to provide information about your package, such as name, version, description, etc. Once you've completed the prompts, it will generate a `package.json` file in your project directory.

## Step 2: Adding a custom registry to package.json

To add a custom registry to your `package.json` file, you need to modify the `"publishConfig"` field. This field allows you to specify the registry URL and authentication details.

Open your `package.json` file in a text editor and add the following code snippet:

```json
"publishConfig": {
  "registry": "<registry-url>"
}
```

Replace `<registry-url>` with the URL of your custom registry. If your registry requires authentication, you can also provide the necessary credentials within the `publishConfig` object.

For example, if you have a custom registry at `https://my-custom-registry.com`, your `package.json` should look like this:

```json
"publishConfig": {
  "registry": "https://my-custom-registry.com"
}
```

## Step 3: Publishing to the custom registry

Once you have added the custom registry to your `package.json` file, you can publish your packages to the registry using the regular `npm publish` command. When you run `npm publish`, npm will use the registry specified in the `publishConfig` field to upload your package.

For example, to publish your package to the custom registry, navigate to your project directory in the terminal and run:

```
npm publish
```

## Conclusion

By following these simple steps, you can easily create a custom registry in your `package.json` file. This allows you to manage packages in your own private or internal registry, providing greater control and flexibility in package distribution.

Remember to **backup your `package.json` file** and ensure the custom registry is accessible to avoid any disruptions in package management.

#npm #registry