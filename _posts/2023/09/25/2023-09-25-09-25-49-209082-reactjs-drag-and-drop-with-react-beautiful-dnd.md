---
layout: post
title: "React.js drag and drop with react-beautiful-dnd"
description: " "
date: 2023-09-25
tags: [ReactJS, DragAndDrop]
comments: true
share: true
---

Drag and drop functionality is a common requirement in many web applications. React.js makes it easy to add this functionality with the help of popular libraries like react-beautiful-dnd. In this blog post, we will explore how to implement drag and drop functionality in React.js using react-beautiful-dnd.

## What is react-beautiful-dnd?

react-beautiful-dnd is a powerful and flexible drag and drop library for React.js. It provides a simple and intuitive API to enable drag and drop functionality in your application. It handles the complexities of managing the state and rendering of draggable and droppable components, making it easier for developers to implement drag and drop features.

## Getting Started

To get started with react-beautiful-dnd, you'll need to install the package via npm or yarn:

```
npm install react-beautiful-dnd
```

or

```
yarn add react-beautiful-dnd
```

Once installed, you can import the necessary components from react-beautiful-dnd:

```jsx
import { DragDropContext, Droppable, Draggable } from 'react-beautiful-dnd';
```

## Using react-beautiful-dnd

To use react-beautiful-dnd, you need to wrap your draggable and droppable components inside a `DragDropContext`.

```jsx
<DragDropContext onDragEnd={handleDragEnd}>
  <Droppable droppableId="droppable">
    {(provided) => (
      <div ref={provided.innerRef} {...provided.droppableProps}>
        {items.map((item, index) => (
          <Draggable key={item.id} draggableId={item.id} index={index}>
            {(provided) => (
              <div
                ref={provided.innerRef}
                {...provided.draggableProps}
                {...provided.dragHandleProps}
              >
                {item.content}
              </div>
            )}
          </Draggable>
        ))}
        {provided.placeholder}
      </div>
    )}
  </Droppable>
</DragDropContext>
```

In the above example, we have a list of items that we want to make draggable. We wrap them inside a `Droppable` component and provide a unique `droppableId`. For each item in the list, we wrap it inside a `Draggable` component and provide a unique `draggableId` and the current index. The `onDragEnd` function is called when the drag and drop operation is completed.

## Handling Drag and Drop Events

To handle drag and drop events, we need to define the `onDragEnd` function. This function will receive an object containing the source and destination information of the drag and drop operation.

```jsx
const handleDragEnd = (result) => {
  if (!result.destination) {
    return;
  }

  const itemsCopy = Array.from(items);
  const [reorderedItem] = itemsCopy.splice(result.source.index, 1);
  itemsCopy.splice(result.destination.index, 0, reorderedItem);

  setItems(itemsCopy);
};
```

In the `handleDragEnd` function, we first check if the drop destination is valid. If it is, we create a copy of the items array, remove the dragged item from the source index, and insert it into the destination index. Finally, we update the state with the new order of items.

## Summary

Implementing drag and drop functionality in React.js is made easy with the help of libraries like react-beautiful-dnd. We learned how to use react-beautiful-dnd to create draggable and droppable components and handle drag and drop events. With this knowledge, you can now enhance your React.js applications with user-friendly drag and drop features.

#ReactJS #DragAndDrop #ReactBeautifulDnd