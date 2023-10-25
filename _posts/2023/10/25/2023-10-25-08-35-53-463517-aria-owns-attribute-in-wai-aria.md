---
layout: post
title: "Aria-owns attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [aria, webaccessibility]
comments: true
share: true
---

In the world of web accessibility, WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) plays a significant role in making web content more accessible to people with disabilities. One of the powerful attributes that WAI-ARIA introduces is the `aria-owns` attribute.

## What is the `aria-owns` attribute?
The `aria-owns` attribute is used to establish a parent-child relationship between two elements in the web document. It specifies that an element owns another element (or a group of elements) programmatically. This relationship is important for screen readers and assistive technologies to understand the connection between the elements and improve the accessibility of the web page.

## Usage of `aria-owns` attribute
Let's say we have an unordered list (`<ul>`) with a customized dropdown menu as its child elements. Normally, screen readers will not recognize the association between the button that activates the dropdown and the dropdown itself. To overcome this, we can use the `aria-owns` attribute.

```html
<ul>
  <li>
    <button id="dropdownButton">Open Dropdown</button>
    <div id="dropdownMenu" role="menu">
      <!-- Dropdown menu content -->
    </div>
  </li>
</ul>
```

Here, we want to establish a relationship between the button with id `dropdownButton` and the div with id `dropdownMenu`.

To achieve this, we can add the `aria-owns` attribute to the button and set its value to the id of the dropdown menu:

```html
<button id="dropdownButton" aria-owns="dropdownMenu">Open Dropdown</button>
```

By doing this, we specify that the button with `id="dropdownButton"` owns the dropdown menu with `id="dropdownMenu"`. Screen readers will then understand the association and provide a more cohesive experience for users.

## Conclusion
The `aria-owns` attribute is a powerful tool in WAI-ARIA that helps establish parent-child relationships between elements on a web page. By using this attribute effectively, we can significantly improve the accessibility of our web content and provide a more inclusive user experience for all users.

<!-- References -->
## References
- [WAI-ARIA Authoring Practices - aria-owns](https://www.w3.org/TR/wai-aria-practices-1.2/#aria-owns) 
- [MDN Web Docs - aria-owns](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-owns_attribute) 
- [WebAIM - WAI-ARIA 1.2](https://webaim.org/standards/aria/) 
- [W3C WAI-ARIA Specification](https://www.w3.org/TR/wai-aria-1.2/) 

#webaccessibility #aria-owns