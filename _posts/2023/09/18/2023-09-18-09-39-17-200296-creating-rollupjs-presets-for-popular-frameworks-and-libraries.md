---
layout: post
title: "Creating Rollup.js presets for popular frameworks and libraries"
description: " "
date: 2023-09-18
tags: [RollupJS, bundling]
comments: true
share: true
---

Rollup.js is a powerful bundler that enables developers to package their JavaScript code into efficient and optimized bundles. While Rollup.js is highly configurable, it can be overwhelming to set it up for different frameworks and libraries. To simplify the process, we can create presets that include the necessary configurations for popular frameworks and libraries. In this blog post, we'll explore how to create Rollup.js presets and provide examples for some popular frameworks and libraries.

## Why use presets?
Using presets for Rollup.js offers several advantages. It simplifies the setup process by providing pre-configured options specific to a framework or library, reducing the need for developers to dig into extensive documentation. Presets also ensure consistency across projects using the same framework or library. With presets, developers can get started quickly and focus on building great applications without spending too much time on configuring the build system.

## Creating a Rollup.js preset
To create a Rollup.js preset, we need to define the necessary plugins and configurations for a specific framework or library. Let's take a look at an example of creating a preset for React:

1. **Install Rollup.js**: First, make sure Rollup.js is installed globally or within your project folder using the following command:
```
npm install --global rollup
```

2. **Create a configuration file**: Next, create a `rollup.config.js` file in your project directory and define the necessary Rollup.js configurations.
```javascript
import resolve from '@rollup/plugin-node-resolve';
import babel from '@rollup/plugin-babel';

export default {
  input: 'src/index.js',
  output: {
    file: 'dist/bundle.js',
    format: 'umd',
  },
  plugins: [
    resolve(),
    babel({
      babelHelpers: 'bundled',
      exclude: 'node_modules/**',
    }),
  ],
};
```

3. **Define the preset**: Now, create a new file named `rollup-preset-react.js` (you can name it based on the framework or library). Import the existing `rollup.config.js` file and modify it according to the specific needs of the framework.
```javascript
import baseConfig from './rollup.config.js';
import { terser } from 'rollup-plugin-terser';
import replace from 'rollup-plugin-replace';

export default {
  ...baseConfig,
  plugins: [
    ...baseConfig.plugins,
    terser(),
    replace({
      'process.env.NODE_ENV': JSON.stringify('production'),
    }),
  ],
};
```

4. **Using the preset**: Now that we have our React preset ready, we can use it for React-based projects. Create a new `rollup.config.js` file and import the preset.
```javascript
import reactPreset from './rollup-preset-react.js';

export default reactPreset;
```

## Available presets
Here are some examples of available Rollup.js presets for popular frameworks and libraries:

- [rollup-preset-react](https://github.com/example/rollup-preset-react): A preset for creating React applications.
- [rollup-preset-vue](https://github.com/example/rollup-preset-vue): A preset for creating Vue.js applications.
- [rollup-preset-angular](https://github.com/example/rollup-preset-angular): A preset for creating Angular applications.
- [rollup-preset-lodash](https://github.com/example/rollup-preset-lodash): A preset for bundling projects that use Lodash.

## Conclusion
Rollup.js presets provide an easy and efficient way to configure Rollup.js for popular frameworks and libraries. By using presets, developers can eliminate the complexity of setting up the bundler and focus on building their applications. Creating and sharing presets within the community can contribute to a more streamlined development process. Whether you are working with React, Vue.js, Angular, or other popular libraries, using Rollup.js presets can greatly enhance your development experience.

#RollupJS #bundling