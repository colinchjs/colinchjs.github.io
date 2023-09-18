---
layout: post
title: "Exploring Rollup.js plugins for adding CSS, images, and fonts to your JavaScript bundle"
description: " "
date: 2023-09-18
tags: [rollupjs, webdevelopment]
comments: true
share: true
---

Rollup.js is a popular JavaScript module bundler that allows you to bundle your code into a single file for better performance. While Rollup.js is primarily used for JavaScript, it also supports various plugins that make it easy to incorporate other assets like CSS, images, and fonts into your bundles. In this blog post, we will explore some of the most useful Rollup.js plugins for managing CSS, images, and fonts.

## Rollup-plugin-css-only

The `rollup-plugin-css-only` plugin allows you to import CSS files directly into your JavaScript code. It takes care of bundling the CSS into your final bundle and injecting it into the document whenever the JavaScript code is executed.

```javascript
import css from 'rollup-plugin-css-only';

export default {
  input: 'src/main.js',
  output: {
    file: 'dist/bundle.js',
    format: 'esm'
  },
  plugins: [
    css({ output: 'dist/main.css' }),
  ]
};
```

With this plugin configuration, whenever you import a CSS file in your JavaScript code, the CSS will be bundled and saved as `main.css` in the `dist` folder.

## Rollup-plugin-img

The `rollup-plugin-img` plugin allows you to import and optimize various image formats into your JavaScript bundles. It automatically optimizes the images and provides efficient loading mechanisms.

```javascript
import img from 'rollup-plugin-img';

export default {
  input: 'src/main.js',
  output: {
    file: 'dist/bundle.js',
    format: 'cjs'
  },
  plugins: [
    img({
      include: ['**/*.png', '**/*.jpg', '**/*.gif', '**/*.jpeg'],
      limit: 8192,
      emitFiles: true,
      output: 'dist/images',
    }),
  ],
};
```

In this configuration, the plugin will process and optimize images with the specified extensions (png, jpg, gif, jpeg) and place them in the `dist/images` folder. The `limit` option specifies the maximum file size in bytes for inlining images as data URLs.

## Rollup-plugin-fonts

The `rollup-plugin-fonts` plugin allows you to import font files into your JavaScript bundles. It automatically handles font file formats and generates CSS code that references the font files correctly.

```javascript
import fonts from 'rollup-plugin-fonts';

export default {
  input: 'src/main.js',
  output: {
    file: 'dist/bundle.js',
    format: 'iife'
  },
  plugins: [
    fonts({
      formats: ['woff2', 'woff'],
      output: 'dist/fonts',
    }),
  ],
};
```

With this configuration, the plugin will convert the font files to the specified formats (woff2, woff) and store them in the `dist/fonts` folder. It will also generate CSS code that references these font files.

## Conclusion

Rollup.js, with its powerful plugin ecosystem, provides robust solutions for incorporating CSS, images, and fonts into your JavaScript bundles. The `rollup-plugin-css-only`, `rollup-plugin-img`, and `rollup-plugin-fonts` plugins showcased in this blog post are just a few examples of the extensive plugin library available. By utilizing these plugins, you can streamline your development process and improve the performance of your web applications.

\#rollupjs #webdevelopment