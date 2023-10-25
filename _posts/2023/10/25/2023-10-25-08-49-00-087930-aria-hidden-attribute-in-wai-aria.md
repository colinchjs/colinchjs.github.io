---
layout: post
title: "Aria-hidden attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [webdevelopment, accessibility]
comments: true
share: true
---

Accessibility is an essential aspect of web development, ensuring that websites and web applications are usable by individuals with disabilities. WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) provides a set of attributes to improve the accessibility of web content. One such attribute is `aria-hidden`.

## What is `aria-hidden`?

`aria-hidden` is an attribute in WAI-ARIA that developers can add to elements in their HTML markup to specify whether those elements should be visible to assistive technologies such as screen readers. When an element has the `aria-hidden` attribute set to `true`, it indicates that the content is not relevant or should not be presented to screen reader users.

## Usage

To add the `aria-hidden` attribute to an HTML element, you need to include it in the element's tag as follows:

```html
<div aria-hidden="true">
   This content will be hidden from assistive technologies.
</div>
```

The attribute value `true` tells assistive technologies that the content inside the element is not relevant or should be hidden. If you want to make the content visible again, you can set the `aria-hidden` attribute value to `false` or remove the attribute altogether.

## Purpose and Benefits

The `aria-hidden` attribute is useful in various scenarios where content should be visually hidden but can still be interacted with programmatically. Some use cases include:

1. **Hidden elements in modals**: When displaying a modal dialog, it is often necessary to hide the rest of the page content to focus user attention. Using `aria-hidden="true"` on the content outside the modal ensures that assistive technologies ignore it.

2. **Content expansions**: In cases where content is dynamically loaded or expanded, using `aria-hidden="true"` initially can prevent assistive technologies from announcing the hidden content until it becomes visible.

3. **Content filtering**: When implementing content filtering or search functionalities, using `aria-hidden="true"` on filtered out or hidden elements prevents assistive technologies from announcing them.

## Conclusion

The `aria-hidden` attribute is a powerful tool in WAI-ARIA to control the visibility of HTML elements for assistive technologies. By selectively hiding content that is not relevant or should not be announced to screen reader users, we can improve the accessibility and user experience of our websites and web applications.

For more information on ARIA attributes and accessibility best practices, refer to the [WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.2/) and the [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/).

#webdevelopment #accessibility