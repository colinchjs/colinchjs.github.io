---
layout: post
title: "Integrating JavaScript Module Federation with Angular projects in Webpack 5"
description: " "
date: 2023-09-18
tags: [techblog, JavascriptModuleFederation]
comments: true
share: true
---

![Webpack](https://miro.medium.com/max/1280/1*oPFJHXl3Mt4VvbaUblRsQg.png)

JavaScript Module Federation is a feature introduced in Webpack 5 that allows for the sharing of code between microfrontends. In an Angular project, this can be incredibly useful for creating a modular architecture and separating different parts of the application into independent modules that can be composed together.

## What is Module Federation?

Module Federation is a concept in which different parts of a larger application are developed and deployed independently. Each part is self-contained and can be built and packaged as its own module. With Module Federation, these modules can then be dynamically loaded and composed into a single app at runtime.

## Setting up Angular with Module Federation

To integrate Module Federation into an Angular project, we first need to update our Webpack configuration.

### Install Webpack 5

Make sure you have the latest version of Webpack installed by running the following command:

```shell
npm install --save-dev webpack@latest
```

### Update Webpack configuration

In the root of your Angular project, create a `webpack.config.js` file if it doesn't exist already. Inside this file, we need to configure Module Federation.

```javascript
const ModuleFederationPlugin = require('webpack/lib/container/ModuleFederationPlugin');

module.exports = {
  // ... other configuration options
  
  plugins: [
    new ModuleFederationPlugin({
      name: 'myApp',
      library: { type: 'var', name: 'myApp' },
      filename: 'remoteEntry.js',
      exposes: {
        './AppModule': './src/app/app.module.ts',
      },
      shared: {
        '@angular/core': { singleton: true, strictVersion: true },
        '@angular/common': { singleton: true, strictVersion: true },
        // add any other shared modules here
      },
    }),
  ],
};
```

In the configuration code above, we are setting the name of our app (in this case, 'myApp') and specifying the entry point for the module (`app.module.ts`) that we want to expose. We also define which modules should be shared between different microfrontends.

### Building and running the app

To build and run the app, we need to update our `angular.json` file. Modify the `"build"` and `"serve"` configurations to use the Webpack configuration file.

```json
"architect": {
  "build": {
    "builder": "@angular-builders/custom-webpack:browser",
    "options": {
      "customWebpackConfig": {
        "path": "./webpack.config.js"
      },
      ...
    },
    ...
  },
  "serve": {
    "builder": "@angular-builders/custom-webpack:dev-server",
    "options": {
      "browserTarget": "your-app:build"
    },
    ...
  },
  ...
}
```

Now you can build and run your Angular project as usual:

```shell
ng build
ng serve
```

## Conclusion

Integrating JavaScript Module Federation with Angular projects in Webpack 5 allows for the creation of modular and independent microfrontends. By leveraging this feature, developers can build complex and scalable applications that are easier to maintain and update.

#techblog #JavascriptModuleFederation