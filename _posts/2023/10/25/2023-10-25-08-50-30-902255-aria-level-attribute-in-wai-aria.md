---
layout: post
title: "Aria-level attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: []
comments: true
share: true
---

WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) is a set of guidelines developed by the World Wide Web Consortium (W3C) to enhance the accessibility of web content for people with disabilities.

One of the attributes provided by WAI-ARIA is the `aria-level` attribute, which is used to indicate the hierarchical level of an element within a structure. It is particularly useful in situations where the order of the elements in the HTML source code does not reflect the desired visual presentation.

## How does `aria-level` work?

The `aria-level` attribute accepts a numerical value that represents the level of the element within a hierarchical structure. The value starts from 1 for the highest-level element and increments by 1 for each subsequent level.

For example, if you have a set of headings (e.g., `<h1>` to `<h6>`), you can use the `aria-level` attribute to adjust the hierarchical relationship of headings that are visually presented out of order. By setting appropriate `aria-level` values, you can ensure the correct reading order and accessibility for assistive technologies.

## When to use `aria-level`?

While it is generally recommended to ensure the HTML heading order reflects the visual presentation, there are scenarios where `aria-level` becomes necessary. Here are a few examples:

1. **Tabbed interfaces**: In tabbed interfaces, the content of each tab may be loaded in a different order in the HTML source code. To maintain the correct reading order, the `aria-level` attribute can be used on the tab panels to correct the hierarchy.

2. **Collapsible sections**: When sections of content are collapsible or expandable, the `aria-level` attribute can be used to ensure that the nested headings within these sections are read in the proper order.

3. **Grids or tables**: In complex data tables or grids, the `aria-level` attribute can be used to specify the hierarchical relationship between header cells and data cells, especially when the order is different than the visual presentation.

## Conclusion

The `aria-level` attribute is a powerful tool in WAI-ARIA to ensure that the hierarchy of elements is properly conveyed to assistive technologies, even when the visual presentation order doesn't match the HTML source order. Though it should be used judiciously and only when necessary, it can significantly improve the accessibility of web content for users with disabilities.

For more information on the `aria-level` attribute and other accessibility-related guidelines, refer to the [W3C WAI-ARIA documentation](https://www.w3.org/TR/wai-aria/).

*Tags: accessibility, WAI-ARIA*