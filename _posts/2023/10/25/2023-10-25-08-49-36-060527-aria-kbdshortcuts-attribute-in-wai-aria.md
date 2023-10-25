---
layout: post
title: "Aria-kbdshortcuts attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [References]
comments: true
share: true
---

In the context of web accessibility, WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) plays a crucial role in making web content more inclusive to people with disabilities. One of the attributes defined by WAI-ARIA is the `aria-kbdshortcuts` attribute. This attribute allows developers to convey keyboard shortcuts associated with an element to assistive technologies.

## What is the `aria-kbdshortcuts` attribute?

The `aria-kbdshortcuts` attribute is an optional attribute that can be added to any HTML element. It is used to provide information about the keyboard shortcuts that trigger an action on or for that particular element. This attribute helps users who rely on keyboard navigation or assistive technologies to quickly understand and interact with the web content.

## How to use the `aria-kbdshortcuts` attribute

To effectively use the `aria-kbdshortcuts` attribute, follow these guidelines:

1. Identify the specific elements within your web application that have associated keyboard shortcuts.
2. Add the `aria-kbdshortcuts` attribute to those elements.
3. Set the value of the attribute to a string representation of the keyboard shortcuts, separated by commas.

Here's an example of how to use the `aria-kbdshortcuts` attribute on a button element:

```html
<button aria-kbdshortcuts="Ctrl+Shift+S">Save</button>
```

In this example, the `aria-kbdshortcuts` attribute is set to `Ctrl+Shift+S`, indicating that pressing the specified key combination triggers the save action associated with the button.

## Considerations when using `aria-kbdshortcuts`

When using the `aria-kbdshortcuts` attribute, keep the following considerations in mind:

- Ensure that the keyboard shortcuts you provide are standardized and commonly used. This helps users who are already familiar with such shortcuts to navigate your web application efficiently.
- Avoid conflicting or overlapping keyboard shortcuts within your application to prevent confusion or unexpected behavior.
- Provide a clear and concise description of the associated action elsewhere in the content to complement the keyboard shortcut.

## Conclusion

The `aria-kbdshortcuts` attribute is a valuable addition to the WAI-ARIA specification, allowing developers to enhance the accessibility of their web applications. By providing clear and accurate information about keyboard shortcuts, users relying on assistive technologies or keyboard navigation can easily interact with the content. When used correctly alongside well-designed application flows, the `aria-kbdshortcuts` attribute can greatly improve the overall usability of your web application.

#References
- [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices-1.1/#kbd_general_ex)
- [MDN Web Docs - aria-kbdshortcuts](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-kbdshortcuts_attribute)