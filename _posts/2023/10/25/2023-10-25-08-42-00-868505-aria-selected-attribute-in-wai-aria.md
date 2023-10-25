---
layout: post
title: "Aria-selected attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: []
comments: true
share: true
---

The `aria-selected` attribute is part of the Web Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) specification. It is used to denote the selected state of an element in an accessible web application.

## What is WAI-ARIA?

WAI-ARIA stands for Web Accessibility Initiative - Accessible Rich Internet Applications. It is a specification developed by the World Wide Web Consortium (W3C) to enhance the accessibility of web content and applications for people with disabilities. WAI-ARIA provides a set of attributes that can be added to HTML elements to convey additional information to assistive technologies.

## The `aria-selected` attribute

The `aria-selected` attribute is used to indicate the selected state of an element. It is typically used in interactive components like tabs, lists, and menus to indicate which item or option is currently selected.

### Usage

To apply the `aria-selected` attribute to an element, you can set it to either `true`, `false`, or `undefined`. Here's an example of how to use it in a list:

```html
<ul>
  <li role="option" aria-selected="true">Item 1</li>
  <li role="option" aria-selected="false">Item 2</li>
  <li role="option" aria-selected="false">Item 3</li>
</ul>
```

In this example, the first `<li>` element is marked as selected with `aria-selected="true"`, while the others are marked as not selected with `aria-selected="false"`.

### Accessibility implications

The `aria-selected` attribute helps assistive technologies convey the selected state of an element to users with disabilities. Screen readers can announce the selected item, and users with mobility impairments can navigate more efficiently using assistive technologies.

It is important to ensure that the selected state is also visually indicated to users. This can be done using CSS styles or by using different visual cues such as highlighting or changing the color of the selected item.

### References

- [W3C WAI-ARIA Specification](https://www.w3.org/TR/wai-aria/)
- [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices-1.2/)

## Conclusion

By using the `aria-selected` attribute in your accessible web applications, you can provide clear feedback to users about the selected state of elements. This attribute plays a crucial role in improving the accessibility and usability of your website or application for people with disabilities.