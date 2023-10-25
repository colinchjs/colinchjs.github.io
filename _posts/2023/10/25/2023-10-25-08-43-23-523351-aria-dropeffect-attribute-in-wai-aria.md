---
layout: post
title: "Aria-dropeffect attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: []
comments: true
share: true
---

The `aria-dropeffect` attribute is a part of the WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) specification. It is used to indicate the effect of a potential drag-and-drop operation on a target element.

## What is the `aria-dropeffect` attribute?

The `aria-dropeffect` attribute is used on an element that could potentially be a drop target. It helps assistive technologies and screen readers by providing information about the possible outcomes or effects of dropping an object onto the element. This attribute allows the screen reader to announce the possible actions that can be performed when an item is dropped.

The `aria-dropeffect` attribute can have the following values:

- `none`: Indicates that dropping an object onto the element will have no effect.
- `copy`: Indicates that a copy of the dropped object will be made.
- `move`: Indicates that the dropped object will be moved.
- `link`: Indicates that a link or association will be created between the dropped object and the target element.

Multiple values can be combined to represent different possible outcomes. For example, `aria-dropeffect="copy move"` indicates that the dropped object will be copied and moved.

## How to use the `aria-dropeffect` attribute?

To use the `aria-dropeffect` attribute, you need to add it to the target element. Here's an example using HTML:

```html
<div aria-dropeffect="copy">
  This is a drop target that will create a copy of the dropped object.
</div>
```

In this example, the `aria-dropeffect` attribute is set to "copy", indicating that dropping an object onto the `<div>` element will create a copy of the dropped object.

It's important to note that the `aria-dropeffect` attribute does not automatically enable drag-and-drop functionality. You still need to implement the necessary JavaScript and HTML events to handle the actual drag-and-drop operations.

## Conclusion

The `aria-dropeffect` attribute in the WAI-ARIA specification provides a way to communicate the possible outcomes or effects of a drag-and-drop operation on a target element. By using this attribute, you can enhance the accessibility of your web application and provide a better user experience for individuals using assistive technologies.

References:
- [WAI-ARIA specification](https://www.w3.org/TR/wai-aria/)
- [MDN Web Docs - aria-dropeffect attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-dropeffect_attribute)