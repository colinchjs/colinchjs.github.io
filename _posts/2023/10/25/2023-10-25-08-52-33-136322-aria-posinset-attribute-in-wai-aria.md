---
layout: post
title: "Aria-posinset attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [webaccessibility]
comments: true
share: true
---

The ARIA-posinset attribute is part of the WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) specification. It is used to indicate the position or order of an element within a set of elements that share the same role and are controlled by a user interface component.

## Purpose of ARIA-posinset Attribute

The ARIA-posinset attribute helps users with disabilities to navigate and interact with web pages more effectively. It provides them with additional information about the position of specific elements within a group, enabling them to understand and access content in a structured manner.

## Usage

The ARIA-posinset attribute should be used in conjunction with the ARIA-setsize attribute, which defines the total number of elements in the set. Together, these attributes provide a numerical context for the position of an element within a group.

```html
<div role="list" aria-setsize="5">
  <div role="listitem" aria-posinset="3">Item 3</div>
</div>
```

In the example above, we have a list containing five items. The third item is marked with the ARIA-posinset attribute set to 3, indicating its position within the set.

## Accessibility Benefits

By incorporating the ARIA-posinset attribute, web developers can enhance the accessibility of their applications by providing assistive technologies with the information they need to present the content in a meaningful way to users. This attribute, when used correctly, helps improve the navigation experience for individuals using screen readers or other assistive devices.

## Summary

The ARIA-posinset attribute in WAI-ARIA allows web developers to specify the position of an element within a set of related elements. This attribute is particularly useful for improving web accessibility by providing users with disabilities the necessary context to navigate and interact with content more effectively.

For more information on ARIA-posinset and other WAI-ARIA attributes, please refer to the [WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.2/).

###### #webaccessibility #wai-aria