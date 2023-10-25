---
layout: post
title: "Aria-invalid attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [webaccessibility]
comments: true
share: true
---

When it comes to web accessibility, it is essential to provide accurate and meaningful information to users with disabilities. One way to achieve this is by using the WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) specification, which defines a set of attributes that can be added to HTML elements to enhance their accessibility.

One such attribute is `aria-invalid`, which is used to indicate to assistive technologies that an input field or form element contains invalid or incorrect information. This attribute can be set to three different values: `true`, `false`, or `grammar`.

* `aria-invalid="true"`: This value indicates that the input field or form element contains invalid or incorrect information. By setting this value, assistive technologies can provide feedback to the user, such as an error message or indication of the invalid input.

* `aria-invalid="false"`: This value indicates that the input field or form element contains valid information. It is used to remove any previous indication of invalid input and let the user know that their input is correct.

* `aria-invalid="grammar"`: This value indicates that the input field or form element contains a grammatical error. It is used when the user's input is syntactically incorrect or does not adhere to the grammar rules of the language being used.

Here's an example of how `aria-invalid` can be used with an HTML input element:

```html
<input type="text" aria-invalid="true" aria-describedby="error-message" />
<div id="error-message">Please enter a valid email address.</div>
```

In the example above, the `aria-invalid` attribute is set to `"true"`, indicating that the input field contains invalid information. The `aria-describedby` attribute is used to associate the input field with an error message, which will be read by assistive technologies to inform the user of the invalid input.

It's important to note that the `aria-invalid` attribute alone does not provide any visual styling or error validation. It is up to the developer to implement appropriate visual cues and error handling based on the value of `aria-invalid`.

By using the `aria-invalid` attribute in combination with other web accessibility techniques, developers can ensure that users with disabilities receive accurate and meaningful information when interacting with web forms and input fields.

References:
- [WAI-ARIA Specification](https://www.w3.org/TR/wai-aria/)
- [Using ARIA](https://www.w3.org/TR/using-aria/) 

#webaccessibility #WAI-ARIA