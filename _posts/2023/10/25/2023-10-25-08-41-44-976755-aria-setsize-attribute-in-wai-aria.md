---
layout: post
title: "Aria-setsize attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: []
comments: true
share: true
---

The **aria-setsize** attribute is part of the WAI-ARIA (Web Accessibility Initiative - Accessible Rich Internet Applications) specification. This attribute is used to indicate the total number of items within a set or container, such as a list or carousel.

## What is WAI-ARIA?

WAI-ARIA is a set of accessibility guidelines and techniques developed by the World Wide Web Consortium (W3C). It provides a way to enhance the accessibility of web content and applications for people with disabilities, including those using assistive technologies.

WAI-ARIA defines a set of roles, properties, and states that can be added to HTML elements to convey additional semantic information to assistive technologies.

## Introduction to aria-setsize

The **aria-setsize** attribute is used to specify the total number of items within a set or container. It is primarily used in conjunction with the **aria-posinset** attribute, which indicates the position of a specific item within the set.

By providing the total number of items using **aria-setsize**, assistive technologies can present more accurate information to users. For example, a screen reader can announce the total number of items and the current position, allowing users to navigate through the set more effectively.

## Usage example

Let's consider a simple list of items as an example:

```html
<ul role="list">
  <li role="listitem" aria-posinset="1" aria-setsize="5">Item 1</li>
  <li role="listitem" aria-posinset="2" aria-setsize="5">Item 2</li>
  <li role="listitem" aria-posinset="3" aria-setsize="5">Item 3</li>
  <li role="listitem" aria-posinset="4" aria-setsize="5">Item 4</li>
  <li role="listitem" aria-posinset="5" aria-setsize="5">Item 5</li>
</ul>
```

In this example, each list item is assigned a **role** of "listitem", indicating its purpose within the list. The **aria-posinset** attribute specifies the position (from 1 to 5) of each item within the set, and the **aria-setsize** attribute indicates that there are a total of 5 items in the set.

## Considerations and best practices

- Ensure that you set the **role** attribute appropriately on the container and individual items. In the example above, the **role** attributes "list" and "listitem" are used to define the list and list items, respectively.

- Always provide a meaningful value for **aria-setsize**. It should reflect the actual number of items in the set or container.

- Make sure to update the **aria-setsize** attribute dynamically if the number of items changes dynamically. This can be done using JavaScript or any other programming language as per your application requirements.

- Test the accessibility of your application using assistive technologies, such as screen readers, to ensure that the use of **aria-setsize** is properly conveyed to users with disabilities.

## Conclusion

The **aria-setsize** attribute is a valuable tool in making web content and applications more accessible. By accurately indicating the total number of items within a set or container, it helps users navigate and understand complex information more effectively when using assistive technologies.

Implementing WAI-ARIA guidelines, including the use of **aria-setsize**, not only improves the accessibility of your application but also enhances the overall user experience.