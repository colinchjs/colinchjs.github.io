---
layout: post
title: "Conditional rendering in Vue.js"
description: " "
date: 2023-10-04
tags: []
comments: true
share: true
---

Conditional rendering is a powerful feature in Vue.js that allows you to selectively render HTML elements based on certain conditions. This is useful when you want to display or hide certain parts of your application based on the state of your data.

## v-if Directive

The `v-if` directive is used to conditionally render elements in Vue.js. It evaluates the expression provided and only adds or removes the element from the DOM based on the result.

```vue
<template>
  <div>
    <h1 v-if="showTitle">Welcome to my Vue.js app!</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showTitle: true
    };
  }
};
</script>

```

In the code above, the `<h1>` element is conditionally rendered based on the value of the `showTitle` property in the component's data object. If `showTitle` is `true`, the element will be added to the DOM. Otherwise, it will be removed.

## v-else Directive

You can also use the `v-else` directive to specify an alternate conditionally rendered element to display when the preceding `v-if` or `v-else-if` statement evaluates to `false`.

```vue
<template>
  <div>
    <h1 v-if="showTitle">Welcome to my Vue.js app!</h1>
    <h2 v-else>Sorry, the title is not available.</h2>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showTitle: true
    };
  }
};
</script>
```

In the code above, if `showTitle` is `false`, the `<h2>` element will be rendered.

## v-else-if Directive

The `v-else-if` directive can be used to chain multiple conditions and specify different elements to render based on the result of those conditions.

```vue
<template>
  <div>
    <h1 v-if="status === 'loading'">Loading...</h1>
    <h2 v-else-if="status === 'error'">Oops, an error occurred.</h2>
    <p v-else>Content loaded successfully.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      status: 'loading'
    };
  }
};
</script>
```

In the code above, the element to render is determined based on the value of the `status` property. If `status` is `"loading"`, a loading message is displayed. If it is `"error"`, an error message is displayed. Otherwise, a success message is displayed.

## Conclusion

Conditional rendering in Vue.js provides a convenient way to control the visibility of elements based on certain conditions. By using the `v-if`, `v-else`, and `v-else-if` directives, you can easily toggle the display of elements in your Vue.js application.