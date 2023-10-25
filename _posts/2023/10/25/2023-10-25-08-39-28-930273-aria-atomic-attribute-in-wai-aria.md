---
layout: post
title: "Aria-atomic attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [Accessibility, WAIARIA]
comments: true
share: true
---

The Aria-atomic attribute is part of the Web Accessibility Initiative - Accessible Rich Internet Applications (WAI-ARIA) specification. It is used to enhance the accessibility of web content for users with disabilities, particularly those using assistive technologies.

## What is Aria-atomic?

The `aria-atomic` attribute is used to indicate whether an element's entire content requires updating in order to be accurately presented to the user. It is typically applied to dynamic or live regions of a web page where the content can change asynchronously.

The value of the `aria-atomic` attribute can be either `true` or `false`. 

- When set to `true`, it indicates that the entire content within the element must be updated together as a whole. This ensures that assistive technologies announce the content as a complete unit, without intermediate updates that could cause confusion.
- When set to `false` (the default value), it indicates that only the portion of the content that has changed needs to be updated.

The `aria-atomic` attribute can be applied to a wide range of HTML elements, such as `<div>`, `<span>`, `<p>`, or any other element that contains content that can change dynamically.

## Usage Example

Let's say we have a live chat application where new messages are added dynamically. Here's an example of how we can use the `aria-atomic` attribute to enhance accessibility:

```html
<div id="chat-messages" aria-live="polite" aria-atomic="true">
  <!-- Existing chat messages -->
  <p>Hi there!</p>
  <p>How can I assist you today?</p>

  <!-- New chat message -->
  <p>New message received: <span class="new-message">Hello!</span></p>
</div>
```

In the example above, the `aria-live="polite"` attribute is used to indicate that updates to the chat messages should be announced by assistive technologies without interrupting the user. The `aria-atomic="true"` attribute ensures that the entire content of the `<div>` element is announced whenever a new message is added, including the newly received message enclosed within the `<span>` element.

## Conclusion

The `aria-atomic` attribute is a valuable tool for improving the accessibility of web content, making it easier for users with disabilities to understand dynamic or live updates. By using this attribute appropriately, developers can ensure a more inclusive and user-friendly experience for all users.

For more information on ARIA attributes and accessibility best practices, please refer to the official [WAI-ARIA specification](https://www.w3.org/TR/wai-aria/) and the [Web Content Accessibility Guidelines (WCAG)](https://www.w3.org/WAI/standards-guidelines/wcag/).

:hashtag: #Accessibility, #WAIARIA