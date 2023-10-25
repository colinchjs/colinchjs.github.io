---
layout: post
title: "Aria-setsize attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: []
comments: true
share: true
---

WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) is a set of guidelines that helps developers in making web applications more accessible to people with disabilities. One of the key attributes in WAI-ARIA is the `aria-setsize` attribute, which plays an important role in improving the accessibility of web content.

## What is the `aria-setsize` attribute?

The `aria-setsize` attribute is part of the WAI-ARIA specification and is used to indicate the number of items in a set or container. It provides crucial information to assistive technologies, such as screen readers, by letting them know the total number of items available and their position in the set.

## How to use the `aria-setsize` attribute?

To use the `aria-setsize` attribute, you need to include it as part of the HTML markup for the element representing an item in the set. Here's an example of how to use it:

```html
<ul role="list">
  <li role="listitem" aria-setsize="3" aria-posinset="1">Item 1</li>
  <li role="listitem" aria-setsize="3" aria-posinset="2">Item 2</li>
  <li role="listitem" aria-setsize="3" aria-posinset="3">Item 3</li>
</ul>
```

In the above example, we have a list with three items. Each item has the `aria-setsize` attribute set to 3 to indicate that there are a total of three items in the list. The `aria-posinset` attribute is used to specify the position of each item within the set.

## Why is the `aria-setsize` attribute important?

The `aria-setsize` attribute is important for accessibility because it helps assistive technologies to provide better context and navigation options for users. For example, a screen reader can use the `aria-setsize` attribute to inform the user that there are three items in the list and let them know their position (e.g., "Item 2 of 3").

By using the `aria-setsize` attribute correctly, developers can ensure that all users, including those using assistive technologies, can access and navigate web content more effectively.

## Conclusion

The `aria-setsize` attribute is a valuable tool provided by the WAI-ARIA guidelines for improving accessibility in web applications. By using this attribute, developers can provide important information about the total number of items in a set and their position within the set to assistive technologies. This helps ensure that all users, regardless of their abilities, can fully engage with web content.

_References:_

- [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices/)
- [MDN Web Docs - aria-setsize](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-setsize_attribute)