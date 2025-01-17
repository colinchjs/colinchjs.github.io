---
layout: post
title: "Using Rollup.js for building static websites with frameworks like Hugo and Jekyll"
description: " "
date: 2023-09-18
tags: [RollupJS, StaticWebsite]
comments: true
share: true
---

Rollup.js is a powerful module bundler that can be used to optimize and bundle your JavaScript modules. While it's commonly used for building frontend applications, it can also be leveraged to enhance the development process of static websites built with popular frameworks like Hugo and Jekyll.

In this blog post, we will explore how Rollup.js can be integrated into the build process of static websites, offering benefits such as code splitting, tree-shaking, and improved performance.

## Why Use Rollup.js with Hugo and Jekyll?

Hugo and Jekyll are known for their simplicity and ease of use in building static websites. However, they have limited support for optimizing JavaScript modules. By integrating Rollup.js into the build process, we can take advantage of its advanced features to improve the performance of our static websites.

## Integrating Rollup.js with Hugo

Here's how you can integrate Rollup.js into your Hugo-based static website:

1. Install Rollup.js by running the following command:

```bash
npm install rollup --save-dev
```

2. Create a `rollup.config.js` file in the root of your Hugo project with the following sample configuration:

```javascript
import { nodeResolve } from '@rollup/plugin-node-resolve';
import { babel } from '@rollup/plugin-babel';

export default {
  input: 'src/main.js',
  output: {
    file: 'dist/bundle.js',
    format: 'iife',
    sourcemap: true,
  },
  plugins: [
    nodeResolve(),
    babel({
      babelHelpers: 'bundled',
      exclude: 'node_modules/**',
    }),
  ],
};
```

3. Update your Hugo configuration file (`config.toml`) to generate the necessary JavaScript file and include it in your static website:

```toml
[build]
  [build.processing.js]
    disableMinification = true

[[build.postProcessors]]
  name = "js"
  [build.postProcessors.options]
    minify = true
```

4. Add a `main.js` file in your `src` folder with your JavaScript code:

```javascript
import { sayHello } from './utils';

sayHello();
```

5. Run Rollup.js to bundle your JavaScript files:

```bash
npx rollup -c
```

Now, your Hugo website will include an optimized JavaScript bundle generated by Rollup.js.

## Integrating Rollup.js with Jekyll

Integrating Rollup.js with Jekyll is similar to the process with Hugo. Here are the steps for integrating Rollup.js with Jekyll:

1. Install Rollup.js by running the following command:

```bash
npm install rollup --save-dev
```

2. Create a `rollup.config.js` file in the root of your Jekyll project with a similar configuration as shown in the Hugo example above.

3. Update your Jekyll configuration file (`_config.yml`) to include the generated JavaScript bundle in your static website:

```yaml
plugins:
  - jekyll-assets
  - jekyll-sitemap
  - jekyll-feed
  - jekyll-seo-tag

assets:
  sources:
    - _assets

  js_compressor: rollup

jekyll-assets:
  sources:
    - _assets
```

4. Add a `main.js` file in your `_assets` folder with your JavaScript code, similar to the Hugo example.

5. Run Rollup.js to bundle your JavaScript files:

```bash
npx rollup -c
```

With Rollup.js integrated into Jekyll, your website will now benefit from optimized JavaScript code.

## Conclusion

Rollup.js can greatly enhance the development process and performance of static websites built with frameworks like Hugo and Jekyll. By leveraging advanced features such as code splitting and tree-shaking, you can optimize your JavaScript code and improve your website's load times.

Consider integrating Rollup.js into your build process to take full advantage of these benefits and optimize your static websites. #RollupJS #StaticWebsite