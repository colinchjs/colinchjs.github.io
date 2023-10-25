---
layout: post
title: "Aria-multiselectable attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [aria, aria]
comments: true
share: true
---

In the world of web accessibility, it is essential to ensure that users with disabilities can properly interact with web applications. The Web Accessibility Initiative – Accessible Rich Internet Applications (WAI-ARIA) provides a set of guidelines to help developers create accessible web content.

One important attribute in WAI-ARIA is the `aria-multiselectable` attribute. This attribute allows developers to indicate whether multiple items within a user interface element can be selected simultaneously. In this blog post, we will explore the `aria-multiselectable` attribute and its usage.

# The `aria-multiselectable` Attribute

The `aria-multiselectable` attribute is used to indicate whether multiple items within a user interface element can be selected at the same time. It is applicable to elements such as menus, lists, and grids.

The possible values for the `aria-multiselectable` attribute are:

- `false` (default): Only a single item can be selected at a time.
- `true`: Multiple items can be selected simultaneously.

By properly setting the `aria-multiselectable` attribute, assistive technologies can provide accurate information to users with disabilities, indicating whether they can select multiple items or only one.

# Usage Example

Let's consider a scenario where we have a dropdown menu with multiple options, and we want to allow users to select multiple items simultaneously. We can use the `aria-multiselectable` attribute in combination with the `role` attribute to achieve this.

```html
<div role="menu" aria-multiselectable="true">
  <button role="menuitem" tabindex="0">Option 1</button>
  <button role="menuitem" tabindex="-1">Option 2</button>
  <button role="menuitem" tabindex="-1">Option 3</button>
</div>
```

In the above example, we set the `aria-multiselectable` attribute to `"true"` to indicate that multiple options can be selected simultaneously within the dropdown menu.

# Conclusion

The `aria-multiselectable` attribute is a valuable tool in web accessibility, allowing developers to specify whether multiple items can be selected within a user interface element. By using this attribute correctly, we can ensure that users with disabilities have a seamless experience when interacting with web applications.

Remember to always refer to the WAI-ARIA documentation for proper usage guidelines and best practices.

Feel free to share your experiences or any questions you may have about the `aria-multiselectable` attribute in the comments section below.

# References

- [WAI-ARIA Authoring Practices - aria-multiselectable](https://www.w3.org/TR/wai-aria-practices-1.1/#aria-multiselectable)
- [WAI-ARIA Specification - aria-multiselectable](https://www.w3.org/TR/wai-aria-1.2/#aria-multiselectable)

#tags: webaccessibility aria wai-aria