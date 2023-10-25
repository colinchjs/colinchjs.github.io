---
layout: post
title: "Aria-required attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [aria]
comments: true
share: true
---

In web development, creating accessible websites is crucial to ensure that all users, including those with disabilities, can effectively use and navigate through the content. The Web Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) provides a set of standards and techniques to enhance the accessibility of web applications.

One important concept in WAI-ARIA is the `aria-required` attribute, which is used to indicate that a form field must be filled out before the form can be submitted. In this blog post, we will take a closer look at how the `aria-required` attribute works and how to implement it in your web applications.

## What is the `aria-required` attribute?

The `aria-required` attribute is part of the set of Accessible Rich Internet Applications (ARIA) attributes defined by the WAI-ARIA specification. It is used to mark form fields as required for the user to complete before submitting the form.

When a form field has the `aria-required` attribute set to `true`, assistive technologies such as screen readers can detect and notify the user that the field is required. This helps to improve the user experience for individuals who rely on assistive technologies to navigate and interact with web content.

## How to use the `aria-required` attribute

To use the `aria-required` attribute, you need to add it to the HTML element representing the form field that you want to make required. The attribute can be added directly to the input element or any other form field element such as select or textarea.

Here's an example of an input field with the `aria-required` attribute:

```html
<input type="text" name="username" aria-required="true">
```

In this example, the `aria-required` attribute is set to `true` to indicate that the username field must be filled out before submitting the form.

It's important to note that the `aria-required` attribute alone does not enforce form validation. It serves as a hint to assistive technologies, but you still need to implement client-side or server-side validation to ensure that the required field is filled out correctly.

## Compatibility and accessibility considerations

The `aria-required` attribute is supported by most modern browsers and assistive technologies. However, it's essential to also include proper client-side validation to provide a consistent user experience across different devices and platforms.

When using the `aria-required` attribute, it's crucial to consider the context and provide clear instructions or error messages for the user. Simply marking a field as required may not be sufficient if users are not informed about why the field is required and what input is expected.

## Conclusion

Using the `aria-required` attribute in your web forms is an excellent way to enhance the accessibility of your web applications. By providing clear indications that specific form fields are required, you can ensure that all users, including those with disabilities, can understand and interact with your forms effectively.

Remember to combine the `aria-required` attribute with proper client-side validation and clear instructions to create a seamless and accessible form filling experience for all users. With these considerations in mind, you can create more inclusive web applications that cater to a wide range of users' needs.

References:
- [WAI-ARIA Authoring Practices: aria-required](https://www.w3.org/TR/wai-aria-practices/#aria-required)
- [MDN Web Docs: ARIA: aria-required](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-required_attribute)