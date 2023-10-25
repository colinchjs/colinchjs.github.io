---
layout: post
title: "Aria-sort attribute in WAI-ARIA."
description: " "
date: 2023-10-25
tags: [webaccessibility, aria]
comments: true
share: true
---

When it comes to making web content more accessible, the Web Accessibility Initiative's Accessible Rich Internet Applications (WAI-ARIA) guidelines provide valuable tools and techniques. One such tool is the `aria-sort` attribute, which can be used to define the sorting order of a table column.

## What is the `aria-sort` attribute?

The `aria-sort` attribute is a WAI-ARIA attribute that can be applied to the `<th>` (table header) element in an HTML table. It informs assistive technologies about the current sorting order of a table column.

## How does the `aria-sort` attribute work?

The `aria-sort` attribute accepts three possible values:

1. `"none"`: This is the default value and indicates that the table column is not currently sorted.
2. `"ascending"`: This value denotes that the table column is sorted in ascending order.
3. `"descending"`: This value indicates that the table column is sorted in descending order.

When the user interacts with the table header to change the sorting order, you should dynamically update the `aria-sort` attribute to reflect the new sort order.

## Why is the `aria-sort` attribute important?

By using the `aria-sort` attribute, you enhance the accessibility of your web content, especially tables that display large amounts of data. This attribute helps assistive technologies understand the current sorting order, allowing users relying on screen readers or other assistive devices to navigate and comprehend the table information more effectively.

## Example usage of the `aria-sort` attribute

Let's consider an example that demonstrates the usage of the `aria-sort` attribute:

```html
<table>
  <thead>
    <tr>
      <th aria-sort="none">Name</th>
      <th aria-sort="ascending">Age</th>
      <th aria-sort="none">Location</th>
    </tr>
  </thead>
  <tbody>
    <!-- table data rows -->
  </tbody>
</table>
```

In this example, the "Name" column is not sorted, the "Age" column is sorted in ascending order, and the "Location" column is not sorted. By providing these attributes, you give assistive technologies the necessary information to convey the sorting order to users.

## Conclusion

The `aria-sort` attribute is a valuable tool in making tables more accessible to users with disabilities. By using this attribute in combination with other WAI-ARIA techniques, you can ensure that your web content provides an inclusive experience for all users.

For more information on WAI-ARIA and web accessibility, refer to the [W3C WAI-ARIA specification](https://www.w3.org/TR/wai-aria/).

#hashtags: #webaccessibility #aria