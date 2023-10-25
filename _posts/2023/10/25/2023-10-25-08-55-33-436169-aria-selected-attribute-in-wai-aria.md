---
layout: post
title: "Aria-selected attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [WebAccessibility, WAIARIA]
comments: true
share: true
---

In the world of web accessibility, it's important to provide a robust and inclusive user experience for all individuals, including those with disabilities. One key aspect of web accessibility is the proper use of WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) attributes. In this blog post, we will explore the `aria-selected` attribute and its significance in enhancing the accessibility of web applications.

## Table of Contents
- [What is the `aria-selected` attribute?](#what-is-the-aria-selected-attribute)
- [Why is the `aria-selected` attribute important?](#why-is-the-aria-selected-attribute-important)
- [How to use the `aria-selected` attribute](#how-to-use-the-aria-selected-attribute)
- [Examples of `aria-selected` attribute usage](#examples-of-aria-selected-attribute-usage)
- [Conclusion](#conclusion)

## What is the `aria-selected` attribute?

The `aria-selected` attribute is a WAI-ARIA attribute that is used to indicate the current selection state of an element, such as a tab, a list item, or a checkbox. It informs assistive technologies, such as screen readers, about the active or selected item, allowing users to navigate and interact with the application effectively.

The `aria-selected` attribute can be applied to different HTML elements, including but not limited to `<button>`, `<li>`, `<option>`, `<input>`, and `<div>`, depending on the context and purpose of the selection.

## Why is the `aria-selected` attribute important?

By using the `aria-selected` attribute correctly, we can improve the accessibility of web applications by providing clear feedback and visual cues to users. Here are a few reasons why the `aria-selected` attribute is important:

1. **Enhanced navigation**: Assistive technologies can understand the current selection state, allowing users to navigate through selectable items more efficiently. For example, screen reader users can easily identify and interact with the selected tab within a tabbed interface.

2. **Clear feedback**: When an item is selected, providing the `aria-selected` attribute communicates its active state to users, regardless of their abilities. This helps users maintain better orientation and stay informed about their current selection.

3. **Keyboard accessibility**: When implementing keyboard navigation, using the `aria-selected` attribute ensures that users can easily identify and interact with selectable elements. Users can use the keyboard to navigate between items, and the `aria-selected` attribute indicates the currently active item.

## How to use the `aria-selected` attribute

To use the `aria-selected` attribute, you need to set its value appropriately based on the current selection state. The `aria-selected` attribute accepts one of three possible values:

- `"true"`: Indicates that the item is selected.
- `"false"`: Indicates that the item is not selected.
- `"undefined"` or not provided: Indicates that the selection state is not known or not applicable.

## Examples of `aria-selected` attribute usage

### Example 1: Tabs

```html
<div role="tablist">
  <button role="tab" aria-selected="true">Tab 1</button>
  <button role="tab" aria-selected="false">Tab 2</button>
  <button role="tab" aria-selected="false">Tab 3</button>
</div>
```

In this example, the `aria-selected` attribute is used to denote the currently selected tab. The first tab has the attribute set to `"true"`, while the other tabs have it set to `"false"`.

### Example 2: List items

```html
<ul role="listbox">
  <li role="option" aria-selected="true">Item 1</li>
  <li role="option" aria-selected="false">Item 2</li>
  <li role="option" aria-selected="false">Item 3</li>
</ul>
```

In this example, the `aria-selected` attribute is used to indicate the selected item within a list. The first list item has the attribute set to `"true"`, while the rest have it set to `"false"`.

## Conclusion

The `aria-selected` attribute plays a crucial role in enhancing the accessibility of web applications by providing important information about the current selection state. By using this attribute appropriately, we can create a more inclusive user experience for individuals with disabilities. When working on web development projects, remember to consider and implement the `aria-selected` attribute whenever there's a need to indicate selection within your user interface.

References:
- [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices/)
- [MDN Web Docs - aria-selected](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-selected_attribute) 

#WebAccessibility #WAIARIA