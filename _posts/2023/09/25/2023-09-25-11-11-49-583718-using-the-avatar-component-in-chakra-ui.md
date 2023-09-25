---
layout: post
title: "Using the Avatar component in Chakra UI"
description: " "
date: 2023-09-25
tags: []
comments: true
share: true
---

Chakra UI is a popular UI component library for React applications. It provides a set of accessible and customizable components that can be easily integrated into your projects. One useful component in Chakra UI is the Avatar component, which allows you to display profile pictures or user avatars in your application.

## Installation

You can install Chakra UI in your React project using npm or yarn. Here's how you can install Chakra UI:

```shell
npm install @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

or

```shell
yarn add @chakra-ui/react @emotion/react @emotion/styled framer-motion
```

## Usage

After installing Chakra UI, you can start using the Avatar component in your React components. Import the necessary components from Chakra UI, and then you can use the Avatar component in your code. Here's an example:

```jsx
import { Avatar } from '@chakra-ui/react';

function UserProfile() {
  return (
    <Avatar
      name="John Doe"
      src="https://example.com/avatar.jpg"
      size="md"
    />
  );
}
```

In the example above, we import the Avatar component from Chakra UI and use it inside the `UserProfile` component. The `name` prop specifies the name of the user, which can be used as a fallback if the `src` prop is not provided or the image fails to load. The `src` prop specifies the URL of the user's avatar image. The `size` prop determines the size of the avatar, which can be set to `"sm"`, `"md"`, `"lg"`, or a custom value.

## Customization

The Avatar component in Chakra UI is highly customizable. You can apply custom styles and add additional props to modify its appearance and behavior. Here are some examples of how you can customize the Avatar component:

### Change the background color and text color

```jsx
<Avatar
  name="John Doe"
  src="https://example.com/avatar.jpg"
  size="md"
  bg="blue.500"
  color="white"
/>
```

### Add a border

```jsx
<Avatar
  name="John Doe"
  src="https://example.com/avatar.jpg"
  size="md"
  border="2px solid red"
/>
```

### Add a box shadow

```jsx
<Avatar
  name="John Doe"
  src="https://example.com/avatar.jpg"
  size="md"
  boxShadow="md"
/>
```

### Use initials instead of an image

```jsx
<Avatar
  name="John Doe"
  size="md"
>
  JD
</Avatar>
```

## Conclusion

The Avatar component in Chakra UI provides an easy way to display user avatars or profile pictures in your React application. With its customization options, you can easily tailor the Avatar component to fit your design requirements.