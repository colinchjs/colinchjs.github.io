---
layout: post
title: "Aria-valuenow attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: []
comments: true
share: true
---

WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) is a set of standards that provide guidelines for creating accessible web content and applications. One important attribute in WAI-ARIA is `aria-valuenow`, which helps in conveying the current value of a user interface component like a progress bar or a slider.

The `aria-valuenow` attribute is used to provide a current numeric value for a range widget or a similar component that can be adjusted via user interaction. It is typically combined with other parallel attributes like `aria-valuemin` and `aria-valuemax` to define the minimum and maximum values of the range or progress.

Here's an example of how `aria-valuenow` can be used in a progress bar:

```html
<div role="progressbar" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100">
  <span class="sr-only">50% Complete</span>
</div>
```

In the example above, the `aria-valuenow` attribute is set to "50", indicating that the progress bar is currently filled to 50%. The `aria-valuemin` attribute defines the minimum value (0) and `aria-valuemax` defines the maximum value (100) of the progress bar. The `<span>` element with the class "sr-only" is used to provide an accessible text alternative that informs screen readers about the current progress.

By using the `aria-valuenow` attribute, developers can enhance the accessibility of user interface components and ensure that users with disabilities can fully understand and interact with them.

For more information on WAI-ARIA and its attributes, refer to the [W3C WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.1/).

#webdevelopment #accessibility