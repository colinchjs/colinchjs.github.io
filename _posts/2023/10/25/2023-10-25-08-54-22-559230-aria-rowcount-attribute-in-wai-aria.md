---
layout: post
title: "Aria-rowcount attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [grid, webaccessibility]
comments: true
share: true
---

In the realm of web accessibility, the Web Accessibility Initiative – Accessible Rich Internet Applications (WAI-ARIA) provides a set of attributes that can be used to make web content more accessible to people with disabilities. One such attribute is `aria-rowcount`, which is specifically used to provide information about the number of rows in a table-like structure.

## What is `aria-rowcount`?

The `aria-rowcount` attribute is used to indicate the total number of rows present in a table-like structure on a webpage. This attribute is useful for assistive technologies like screen readers, which can use it to inform users about the size of a data table or grid.

## How to use `aria-rowcount`?

To use the `aria-rowcount` attribute, simply add it to the element representing the table or grid structure. The value of the attribute should be a positive integer representing the total number of rows.

For example, consider the following HTML markup representing a simple table:

```html
<table aria-rowcount="5">
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>John Doe</td>
    <td>25</td>
  </tr>
  <tr>
    <td>Jane Smith</td>
    <td>30</td>
  </tr>
  <tr>
    <td>Mike Johnson</td>
    <td>40</td>
  </tr>
  <tr>
    <td>Sarah Thompson</td>
    <td>35</td>
  </tr>
</table>
```

In this example, the `aria-rowcount` attribute is set to `5` to indicate that the table has a total of 5 rows.

## Benefits of using `aria-rowcount`

By using the `aria-rowcount` attribute, you provide important information to assistive technologies, enabling them to accurately convey the size and structure of a table-like element to users with disabilities. This improves the overall accessibility of your website and ensures that all users can effectively interact with your content.

## Conclusion

The `aria-rowcount` attribute is a valuable tool in enhancing web accessibility, specifically in providing information about the number of rows in a table-like structure. By including this attribute in your HTML markup, you can make your web content more inclusive to individuals with disabilities.

References:
- [WAI-ARIA Authoring Practices](https://www.w3.org/TR/wai-aria-practices-1.1/#grid)
- [MDN Web Docs - aria-rowcount](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-rowcount_attribute) 

#webaccessibility #WAIARIA