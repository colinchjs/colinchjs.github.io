---
layout: post
title: "Using JavaScript Module Federation with Vue.js applications in Webpack 5"
description: " "
date: 2023-09-18
tags: [F63E02, vuejs]
comments: true
share: true
---

JavaScript Module Federation is a powerful feature introduced in Webpack 5, which allows you to share and consume code dynamically between different applications. If you are building a Vue.js application and want to take advantage of this feature, this blog post will guide you through the process.

## What is JavaScript Module Federation?

JavaScript Module Federation is a module system built into Webpack that enables you to build applications composed of independently developed modules. With module federation, you can expose modules from one application and consume them in another application without complex setup or configurations.

## Setting up a Vue.js application with Webpack 5

Before we dive into using JavaScript Module Federation, let's first set up a basic Vue.js application with Webpack 5. Here are the steps:

1. Create a new Vue.js project using the Vue CLI:

```
vue create my-app
```

2. Select the default preset or customize it according to your needs.

3. Once the project is created, navigate to the project directory:

```
cd my-app
```

4. Install the necessary dependencies:

```
npm install
```

5. Start the development server:

```
npm run serve
```

Now that we have set up our Vue.js application, let's see how we can leverage JavaScript Module Federation.

## Using JavaScript Module Federation in Vue.js

1. Install the necessary dependencies for JavaScript Module Federation:

```
npm install webpack@5.4.0 webpack-cli@4.2.0 webpack-dev-server@3.11.0 -D
```

2. Create a new Webpack configuration file named `webpack.config.js` in the root directory of your project:

```javascript
const { VueLoaderPlugin } = require('vue-loader');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ModuleFederationPlugin = require('webpack').container.ModuleFederationPlugin;

module.exports = {
  entry: './src/main.js',
  output: {
    publicPath: 'http://localhost:8080/',
  },
  resolve: {
    extensions: ['.js', '.vue'],
  },
  module: {
    rules: [
      {
        test: /\.vue$/,
        loader: 'vue-loader',
      },
      // other loaders for JavaScript, CSS, etc.
    ],
  },
  plugins: [
    new VueLoaderPlugin(),
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
    new ModuleFederationPlugin({
      name: 'myApp',
      filename: 'remoteEntry.js',
      exposes: {
        './Button': './src/components/Button.vue',
      },
    }),
  ],
};
```

In this configuration file, we have included the necessary plugins and loaders for Vue.js, as well as the `ModuleFederationPlugin` from Webpack. We have also defined an `exposes` object, which specifies the components that we want to expose for consumption in other applications.

3. Update the `main.js` file in the `src` directory:

```javascript
import { createApp } from 'vue';
import App from './App.vue';

createApp(App).mount('#app');
```

4. Create a new component named `Button.vue` in the `src/components` directory:

```vue
<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'Button',
};
</script>

<style>
.btn {
  background-color: #F63E02;
  color: #fff;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
</style>
```

5. Run the development server again:

```
npm run serve
```

Now, when you access your Vue.js application, you should be able to see the `Button` component, which we exposed using JavaScript Module Federation.

## Conclusion

In this blog post, we learned how to set up a Vue.js application with Webpack 5 and leverage JavaScript Module Federation to share and consume components in different applications. JavaScript Module Federation is a powerful feature that enhances the modularity and reusability of your code, allowing you to build more scalable and maintainable applications.

#vuejs #javascript #webpack #modularity #code-sharing