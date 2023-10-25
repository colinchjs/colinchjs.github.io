---
layout: post
title: "Aria-activedescendant attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [menu, accessibility]
comments: true
share: true
---

The `aria-activedescendant` attribute is a powerful feature of the Web Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) specification. This attribute is used to enhance the accessibility and usability of complex web applications by indicating the currently active element within a group of related elements.

## What is the `aria-activedescendant` attribute?

The `aria-activedescendant` attribute is an ARIA attribute that is often used in conjunction with other ARIA attributes, such as `aria-haspopup` and `aria-expanded`, to create more accessible and interactive web components. It is typically used within widgets, like lists, menus, and tabs, where there is a need to indicate which element is currently active or selected.

## How does it work?

When using the `aria-activedescendant` attribute, you need to assign a unique ID to each element within the related group. Then, you set the `aria-activedescendant` attribute on the parent element to the ID of the currently active element. This informs assistive technologies, such as screen readers, of the active element's ID.

When the active element changes, you simply update the value of the `aria-activedescendant` attribute with the new ID. This allows assistive technologies to announce the change and provide appropriate feedback to the user.

## Example usage

Let's consider a simple example of a dropdown menu using the `aria-activedescendant` attribute:

```html
<button id="menu-button" aria-haspopup="true" aria-expanded="false">
  Select an option
</button>

<ul id="menu" role="menu" aria-labelledby="menu-button">
  <li role="menuitem" id="option-1">Option 1</li>
  <li role="menuitem" id="option-2">Option 2</li>
  <li role="menuitem" id="option-3">Option 3</li>
</ul>
```

In this example, the `aria-haspopup` attribute indicates that the button has a popup menu associated with it, and the `aria-expanded` attribute shows whether the menu is currently expanded.

To indicate the active element within the menu, we can use the `aria-activedescendant` attribute:

```html
<button id="menu-button" aria-haspopup="true" aria-expanded="false" aria-activedescendant="option-1">
  Select an option
</button>

<ul id="menu" role="menu" aria-labelledby="menu-button">
  <li role="menuitem" id="option-1" aria-selected="true">Option 1</li>
  <li role="menuitem" id="option-2">Option 2</li>
  <li role="menuitem" id="option-3">Option 3</li>
</ul>
```

In this updated code, we have set the `aria-activedescendant` attribute on the button to "option-1", indicating that the first option is currently active. The `aria-selected` attribute on the active element further enhances its accessibility and provides additional information.

## Conclusion

The `aria-activedescendant` attribute is a useful tool for improving the accessibility of complex web applications. By using this attribute, you can ensure that assistive technologies correctly interpret which element is currently active, providing a better user experience for all users.

Remember, when designing and developing accessible web components, it's important to follow the WAI-ARIA specification and guidelines to ensure compatibility with assistive technologies and promote inclusivity.

**References:**
- [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices-1.2/#menu)
- [WAI-ARIA Specification](https://www.w3.org/TR/wai-aria-1.2/) 

#accessibility #WAIARIA