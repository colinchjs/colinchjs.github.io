---
layout: post
title: "Building web components with Rollup.js and frameworks like Lit and Stencil"
description: " "
date: 2023-09-18
tags: [007bff, webcomponents]
comments: true
share: true
---

Web components are a powerful way to encapsulate and reuse UI elements in web applications. They provide a standardized way to create custom HTML elements with their own encapsulated styles and functionality. Rollup.js is a popular JavaScript module bundler that can be used to build web components, while frameworks like Lit and Stencil provide additional abstractions and tooling to simplify the development process.

## Why use Rollup.js for building web components?

Rollup.js is a highly efficient and flexible module bundler that can optimize your code for production. It is particularly well-suited for building web components due to its tree-shaking capabilities. Tree-shaking is the process of removing unused code from your application, resulting in smaller bundle sizes and faster load times. With Rollup.js, you can easily create a lean and optimized bundle for your web components.

## Getting started with Rollup.js, Lit, and Stencil

To get started with building web components, first, **install** Rollup.js globally on your machine:

```shell
npm install rollup --global
```

Next, initialize a new project, install Lit and Stencil, and configure Rollup.js:

1. **Create a new directory** for your project:

```shell
mkdir web-components
cd web-components
```

2. **Initialize** a new npm project:

```shell
npm init -y
```

3. **Install** Lit and Stencil as dependencies:

```shell
npm install lit stencil
```

4. **Create** a new `rollup.config.js` file in the root of your project:

```javascript
import { createConfig } from '@stencil/core';

export default createConfig({
  outputTargets: [
    {
      type: 'dist',
      esmLoaderPath: '../loader',
    },
    {
      type: 'www',
      serviceWorker: null, // disable service workers
    },
  ],
});
```

## Building a web component with Lit

[Lit](https://lit.dev/) is a lightweight, fast, and extensible library for building web components. With Lit, you can write web components using HTML templates and JavaScript expressions.

Here's an example of building a simple button web component using Lit:

```javascript
import { html, css, LitElement } from 'lit';

class MyButton extends LitElement {
  static styles = css`
    .button {
      background-color: #007bff;
      color: white;
      padding: 8px 16px;
      border-radius: 4px;
      font-size: 16px;
    }
  `;

  render() {
    return html`
      <button class="button">
        <slot></slot>
      </button>
    `;
  }
}

customElements.define('my-button', MyButton);
```

To **build** the web component using Rollup.js, run the following command:

```shell
rollup --config
```

## Building a web component with Stencil

[Stencil](https://stenciljs.com/) is a compiler for building fast and efficient web components. It provides a higher level of abstraction compared to Lit, offering features like JSX and TypeScript support.

To create a web component with Stencil, follow these steps:

1. **Create** a new directory for your Stencil component:

```shell
mkdir my-component
cd my-component
```

2. **Generate** a new Stencil project:

```shell
npx stencil init
```

3. **Create** a new `my-component.tsx` file in the `src/components` directory:

```tsx
import { Component, h } from '@stencil/core';

@Component({
  tag: 'my-component',
  styleUrl: 'my-component.css',
  shadow: true,
})
export class MyComponent {
  render() {
    return <div>
      <h1>Hello, Stencil!</h1>
      <slot></slot>
    </div>;
  }
}
```

4. **Build** the web component using Stencil:

```shell
npx stencil build
```

Stencil will generate a production-ready web component bundle in the `dist` directory.

## Conclusion

Rollup.js, Lit, and Stencil provide powerful tools and abstractions for building web components. With Rollup.js as the module bundler and frameworks like Lit and Stencil, you can create reusable and optimized web components with ease. Whether you prefer a lightweight approach with Lit or a more feature-rich solution with Stencil, these tools empower you to build modern and efficient web applications.

#webcomponents #rollup #lit #stencil