---
layout: post
title: "Aria-grabbed attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [accessibility, webdevelopment]
comments: true
share: true
---

Web Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) is a set of guidelines designed to make web content more accessible for people with disabilities. One important attribute introduced by WAI-ARIA is the `aria-grabbed` attribute. In this blog post, we will explore the purpose and usage of the `aria-grabbed` attribute.

## Table of Contents
- [Introduction to `aria-grabbed`](#introduction-to-aria-grabbed)
- [Usage of `aria-grabbed`](#usage-of-aria-grabbed)
- [Conclusion](#conclusion)

## Introduction to `aria-grabbed`

The `aria-grabbed` attribute is used to indicate whether an element is currently selected or grabbed. It is primarily used in drag-and-drop interactions or elements that can be selected or manipulated through user interaction.

By setting the value of `aria-grabbed` to "true", the assistive technologies will interpret the element as currently selected or grabbed. Conversely, setting the value to "false" will indicate that the element is not selected or grabbed.

## Usage of `aria-grabbed`

To use the `aria-grabbed` attribute, you need to add it to an element that is selectable or draggable by the user. The value of the attribute should be set dynamically based on the user's interaction with the element.

Here's an example usage of `aria-grabbed` in HTML:

```html
<div id="draggable-element" role="button" tabindex="0" aria-grabbed="false">
  Drag me
</div>
```

In the above example, the `div` element with the id "draggable-element" is made draggable by using the `role` attribute with the value "button". The `aria-grabbed` attribute is initially set to "false" indicating that the element is not yet grabbed by the user.

When the user starts dragging the element, you can dynamically update the `aria-grabbed` attribute to "true" using JavaScript to indicate that the element is grabbed.

```javascript
const draggableElement = document.getElementById("draggable-element");

draggableElement.addEventListener("dragstart", () => {
  draggableElement.setAttribute("aria-grabbed", "true");
});

draggableElement.addEventListener("dragend", () => {
  draggableElement.setAttribute("aria-grabbed", "false");
});
```

By updating the `aria-grabbed` attribute, screen reader users will receive live updates about the status of the element, ensuring a more inclusive experience.

## Conclusion

The `aria-grabbed` attribute is a valuable addition to WAI-ARIA as it improves the accessibility of web applications that involve draggable or selectable elements. By using this attribute appropriately, developers can provide more information to assistive technologies and ensure users with disabilities can fully engage with the web content.

To learn more about WAI-ARIA and other accessibility best practices, refer to the [WAI-ARIA specification](https://www.w3.org/TR/wai-aria/).

\#accessibility \#webdevelopment