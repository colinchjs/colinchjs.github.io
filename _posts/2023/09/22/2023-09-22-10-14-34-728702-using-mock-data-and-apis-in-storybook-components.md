---
layout: post
title: "Using mock data and APIs in Storybook components"
description: " "
date: 2023-09-22
tags: [MockData, MockAPIs]
comments: true
share: true
---

When developing UI components in Storybook, it can be helpful to use mock data or mock APIs to simulate real-world scenarios. This allows you to test and iterate on your components without relying on actual data or making unnecessary API requests. In this blog post, we will explore how to incorporate mock data and APIs into your Storybook components.

## Mock Data

Mock data is simulated data that resembles the structure and format of real data, but is not sourced from a live system. It can be used to populate your components during development and testing. Here's how you can incorporate mock data in your Storybook component:

1. First, create a `stories` folder inside your component directory, if it doesn't exist already.

2. Inside the `stories` folder, create a file named `Component.stories.js`. This file will contain your component's stories.

3. Import your component and any mock data that you want to populate it with.

```javascript
import React from 'react';
import Component from '../Component';

// Import your mock data
import { mockData } from './mockData';
```

4. Create a story using the `.storiesOf` function, passing the title of the story and the module where your component is defined.

```javascript
storiesOf('Component', module)
  .addDecorator((story) => <div style={{ padding: '20px' }}>{story()}</div>)
  .add('Default', () => (
    <Component data={mockData} />
  ));
```

5. Use the imported mock data to populate your component. You can pass the mock data as a prop to your component and render it accordingly.

```javascript
<Component data={mockData} />;
```

By using mock data, you can easily visualize how your component behaves with different data scenarios without the need for a live API.

## Mock APIs

In some cases, you may have components that rely on data fetched from an API. To avoid making actual network requests during development, you can use mock APIs. Here's how you can incorporate mock APIs into your Storybook components:

1. Create a `mockApi` folder inside your component directory.

2. Inside the `mockApi` folder, create a file named `api.js`. This file will contain your mock API functions.

```javascript
// api.js

export const fetchMockData = async () => {
  // Simulate an API response delay
  await new Promise((resolve) => setTimeout(resolve, 1000));

  // Return your mock data
  return { data: 'Mock API response' };
};
```

3. Update your component code to use the mock API functions.

```javascript
import React, { useEffect, useState } from 'react';
import { fetchMockData } from './mockApi/api';

const Component = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      const response = await fetchMockData();
      setData(response.data);
    };

    fetchData();
  }, []);

  if (!data) {
    return <div>Loading...</div>;
  }

  return <div>{data}</div>;
};

export default Component;
```

4. Update your Storybook stories to wrap your component with a decorator. This decorator can simulate the API response.

```javascript
storiesOf('Component', module)
  .addDecorator((story) => {
    const [data, setData] = useState(null);

    useEffect(() => {
      const fetchData = async () => {
        const response = await fetchMockData();
        setData(response.data);
      };

      fetchData();
    }, []);

    if (!data) {
      return <div>Loading...</div>;
    }

    return <div style={{ padding: '20px' }}>{story(data)}</div>;
  })
  .add('Default', (data) => <Component data={data} />);
```

By implementing mock data and mock APIs, you can develop and test your Storybook components more effectively, without relying on real data or making unnecessary API calls. This allows for faster iteration and a smoother development process. #MockData #MockAPIs