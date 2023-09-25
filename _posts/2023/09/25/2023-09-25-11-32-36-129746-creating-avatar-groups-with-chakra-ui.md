---
layout: post
title: "Creating avatar groups with Chakra UI"
description: " "
date: 2023-09-25
tags: [React, ChakraUI]
comments: true
share: true
---

Avatars are a common element in user interfaces that display user profile pictures or initials. However, in some cases, it is necessary to display a group of avatars together, such as in a team or chat interface. Chakra UI, a popular React component library, provides an easy way to create avatar groups with just a few lines of code.

In this tutorial, we will walk through the process of creating avatar groups using Chakra UI and React. Let's get started!

## Installing Chakra UI

The first step is to install Chakra UI in your React project. You can install it via npm or yarn by running the following command:

```bash
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```bash
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Importing the Required Components

To create avatar groups, we need to import a few Chakra UI components in our React component. Open the file where you want to create the avatar group and import the necessary components as shown below:

```jsx
import { Avatar, AvatarGroup } from "@chakra-ui/react";
```

## Creating the Avatar Group

Next, we need to create the avatar group and populate it with individual avatar components. Within your component's render method or functional component, create an `AvatarGroup` component and add `Avatar` components as children. Here's an example:

```jsx
function AvatarGroupExample() {
  return (
    <AvatarGroup size="md" max={3}>
      <Avatar name="John Doe" src="https://example.com/avatar1.jpg" />
      <Avatar name="Jane Smith" src="https://example.com/avatar2.jpg" />
      <Avatar name="Adam Johnson" src="https://example.com/avatar3.jpg" />
      <Avatar name="Emily Wilson" src="https://example.com/avatar4.jpg" />
    </AvatarGroup>
  );
}
```

In the example above, we are creating an `AvatarGroup` component and adding four `Avatar` components as children. We have specified the `size` prop as "md" to set the size of the avatars, and the `max` prop as 3 to limit the number of visible avatars (any additional avatars will be hidden).

## Customizing the Avatar Group

Chakra UI provides a variety of properties and props to customize the appearance and behavior of the avatar group. You can explore the [Chakra UI documentation](https://chakra-ui.com/docs) to discover all available options, such as changing the size, border color, or adding tooltips.

## Conclusion

In this tutorial, we have learned how to create avatar groups using Chakra UI and React. By leveraging the `AvatarGroup` and `Avatar` components, we can easily display a group of avatars in our user interface. Customize the appearance and behavior according to your needs using the various props provided by Chakra UI.

Start incorporating avatar groups into your React applications and create visually appealing user interfaces. Happy coding!

\#React \#ChakraUI