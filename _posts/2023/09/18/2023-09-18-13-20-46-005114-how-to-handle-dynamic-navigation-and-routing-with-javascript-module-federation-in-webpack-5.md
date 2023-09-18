---
layout: post
title: "How to handle dynamic navigation and routing with JavaScript Module Federation in Webpack 5"
description: " "
date: 2023-09-18
tags: [ModuleFederation, DynamicRouting]
comments: true
share: true
---

JavaScript Module Federation is a powerful feature introduced in Webpack 5 that allows us to dynamically load and share modules across multiple applications. One of the common use cases is dynamic navigation and routing, where different modules contribute their own routes to a central routing configuration.

In this blog post, we will explore how to handle dynamic navigation and routing using JavaScript Module Federation in Webpack 5.

## Setting up the project

Before we dive into the implementation, let's set up a basic project structure. We'll assume you have a basic understanding of Webpack 5 and the concepts of Module Federation. Here are the steps to set up the project:

1. Create a new directory for your project.
2. Initialize a new npm project using `npm init`.
3. Install webpack and the necessary loaders and plugins: 

```bash
npm install webpack webpack-cli webpack-dev-server html-webpack-plugin@next
```

4. Create a basic webpack configuration file `webpack.config.js` and set up the necessary loaders and plugins.

## Implementing dynamic navigation and routing

Once the project is set up, we can start implementing the dynamic navigation and routing using JavaScript Module Federation.

### Step 1: Create a navigation module

First, create a module that will handle the navigation and routing for your application. This module will be responsible for rendering the navigation menu and dynamically loading the appropriate module based on the selected route.

Here's an example of how you can create a `Navigation` module:

```javascript
import { routes } from './routes';

function navigateTo(route) {
  // Load the module associated with the selected route
  import(route.modulePath)
    .then(module => {
      // Render the module's content
      module.render();
    })
    .catch(error => {
      console.error(`Error loading module: ${route.modulePath}`, error);
    });
}

export function renderNavigation() {
  // Render the navigation menu
  const navigationMenu = document.getElementById('navigation-menu');
  navigationMenu.innerHTML = '';

  routes.forEach(route => {
    const menuItem = document.createElement('li');
    menuItem.innerText = route.title;
    menuItem.addEventListener('click', () => navigateTo(route));

    navigationMenu.appendChild(menuItem);
  });
}
```
Here, we have a `routes` array that defines the available routes for the application. Each route object contains a `modulePath` property, which represents the path to the module that should be loaded when the route is selected.

The `navigateTo` function dynamically imports the module associated with the selected route and renders its content. If an error occurs while loading the module, it will be logged to the console.

The `renderNavigation` function renders the navigation menu based on the routes array. Each menu item is created as a list item (`li`) and has a click event listener that triggers the `navigateTo` function.

### Step 2: Configure Module Federation

Next, we need to configure Module Federation in the main application to enable dynamic module loading. The main application will be responsible for loading the `Navigation` module and integrating it into the application.

```javascript
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  // ...
  plugins: [
    new HtmlWebpackPlugin({
      template: './src/index.html',
    }),
  ],
  // ...
  experiments: {
    asyncWebAssembly: true,
    importAsync: true,
    importAwait: true,
    importType: "commonjs",
  },
  output: {
    // ...
    uniqueName: 'mainApp',
  },
  // ...
  moduleFederation: {
    name: 'mainApp',
    filename: 'remoteEntry.js',
    exposes: {
      './Navigation': './src/navigation.js',
    },
    shared: ["react", "react-dom"],
  },
};
```

In the webpack configuration above, we configure `moduleFederation` with the following key properties:

- `name`: The name of the main application.
- `filename`: The name of the remote entry file that will be generated for the main application.
- `exposes`: The module that we want to expose to other applications. In this case, we expose the `Navigation` module as `./Navigation`.
- `shared`: An array of modules that should be shared between the main application and the dynamically loaded modules. In this example, we're sharing `react` and `react-dom`.

### Step 3: Implement the main application

Finally, we need to implement the main application that will load the `Navigation` module and integrate it into the UI. 

Here's an example of how you can integrate the `Navigation` module into the main application:

```javascript
import('./remoteEntry.js')
  .then(() => {
    const NavigationModule = require('mainApp/Navigation');

    NavigationModule.renderNavigation();
  })
  .catch(error => {
    console.error('Error loading remoteEntry.js', error);
  });
```

In this code snippet, we first load the `remoteEntry.js` file using dynamic import. Once the file is loaded, we require the `Navigation` module using the `mainApp/Navigation` import path.

Finally, we call the `renderNavigation` function from the `Navigation` module to integrate the navigation menu into the main application's UI.

## Conclusion

In this blog post, we explored how to handle dynamic navigation and routing using JavaScript Module Federation in Webpack 5. We learned how to create a navigation module that dynamically loads other modules based on selected routes, configure Module Federation in the main application, and integrate the navigation module into the UI.

With JavaScript Module Federation, you can build highly scalable and modular applications that can share and load modules dynamically. This enables you to create more flexible and maintainable applications with a better user experience.

#ModuleFederation #DynamicRouting