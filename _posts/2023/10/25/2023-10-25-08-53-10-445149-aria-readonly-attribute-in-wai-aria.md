---
layout: post
title: "Aria-readonly attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [readonly]
comments: true
share: true
---

## Introduction

The Web Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) is a set of guidelines and specifications that enable developers to create web applications that are more accessible to people with disabilities. One of the attributes defined in WAI-ARIA is the `aria-readonly` attribute, which is used to indicate whether an element is read-only or editable.

In this blog post, we will explore the `aria-readonly` attribute, its purpose, and how it can be used to enhance web accessibility.

## Understanding the `aria-readonly` attribute

The `aria-readonly` attribute is used to indicate whether an element is read-only or editable. It is part of the WAI-ARIA specification and is commonly used in combination with other elements, such as text inputs and form fields.

The attribute can have two possible values:

- `true`: Indicates that the element is read-only.
- `false` or not present: Indicates that the element is editable.

By using the `aria-readonly` attribute, developers can make it clear to assistive technologies and users whether an element can be modified or not. This is particularly useful for individuals with visual impairments or motor disabilities who rely on screen readers or other assistive technologies to navigate and interact with web content.

## Implementing the `aria-readonly` attribute

To implement the `aria-readonly` attribute in your HTML markup, you simply need to add it to the relevant element. For example, if you have a text input field that should be read-only, you can add the attribute as follows:

```html
<input type="text" aria-readonly="true" value="This is a read-only field">
```

In this example, the text input field will be marked as read-only, both visually and programmatically. Screen readers and other assistive technologies will announce the read-only status to the user, preventing them from editing the field.

Similarly, if you want to mark an element as editable, you can omit the `aria-readonly` attribute or set it to `false`:

```html
<input type="text" value="This field is editable">
```

It's important to note that the `aria-readonly` attribute is not a replacement for the `readonly` attribute in HTML. The `readonly` attribute is used for native form elements, while the `aria-readonly` attribute is used to enhance accessibility for custom elements or when scripting behavior needs to be communicated.

## Conclusion

The `aria-readonly` attribute is a valuable tool in web accessibility, allowing developers to indicate whether an element is read-only or editable. By using this attribute, developers can improve the user experience for individuals with disabilities who rely on assistive technologies.

Remember to always test your implementation with different assistive technologies and ensure that the expected behavior is achieved. By following the WAI-ARIA guidelines, we can create more inclusive and accessible web applications.

References:
- [WAI-ARIA Authoring Practices: readonly](https://www.w3.org/TR/wai-aria-practices/#readonly)
- [Accessible Rich Internet Applications (WAI-ARIA) 1.2](https://www.w3.org/TR/wai-aria-1.2/)