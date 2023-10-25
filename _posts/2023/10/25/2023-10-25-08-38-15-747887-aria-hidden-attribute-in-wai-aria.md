---
layout: post
title: "Aria-hidden attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [aria]
comments: true
share: true
---

The WAI-ARIA (Web Accessibility Initiative-Accessible Rich Internet Applications) specification provides guidelines for making web content and applications more accessible to people with disabilities. One important attribute prescribed by WAI-ARIA is the `aria-hidden` attribute.

## What is the `aria-hidden` attribute?

The `aria-hidden` attribute is used to indicate to assistive technologies, such as screen readers, whether an element should be visible or not to the user. When applied to an element, the `aria-hidden` attribute can have two values:

- `aria-hidden="true"`: Indicates that the element and all of its descendants should be removed from the accessibility tree. This means that the element and its contents will not be perceivable to assistive technologies.
- `aria-hidden="false"`: Indicates that the element and its contents should be included in the accessibility tree and be perceivable to assistive technologies.

## Why is the `aria-hidden` attribute important?

The `aria-hidden` attribute is crucial for web accessibility because it allows developers to control the visibility of certain elements on a webpage for assistive technology users. By using `aria-hidden`, developers can hide elements that are purely decorative or redundant, reducing the cognitive load for users with disabilities and allowing them to focus on the core content.

Additionally, using `aria-hidden` correctly improves the efficiency of screen readers, as they can skip over hidden elements and provide a better browsing experience for users.

## How to use the `aria-hidden` attribute?

To use the `aria-hidden` attribute, simply apply it to the HTML element you want to hide. Here's an example:

```html
<p aria-hidden="true">This paragraph contains decorative text.</p>
```

In this example, the `<p>` element with the `aria-hidden` attribute set to "true" will be excluded from the accessibility tree, ensuring that screen readers won't read its content to the user.

Remember that it's important to use `aria-hidden` responsibly and only apply it to elements that don't provide meaningful information to assistive technology users.

## Conclusion

The `aria-hidden` attribute plays a vital role in web accessibility, allowing developers to control the visibility of elements for assistive technology users. By using this attribute effectively, we can improve the browsing experience for people with disabilities by reducing clutter and focusing on the essential content. Remember to use `aria-hidden` responsibly and test your webpages with screen readers to ensure proper accessibility.

**References:**
- WAI-ARIA Authoring Practices: https://www.w3.org/TR/wai-aria-practices-1.2/#aria_hidden
- WebAIM: Using ARIA: https://webaim.org/techniques/aria/