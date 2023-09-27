---
layout: post
title: "Building a job board with Javascript and GraphQL"
description: " "
date: 2023-09-27
tags: [graphql]
comments: true
share: true
---

In today's tech-driven world, job boards have become essential for companies and job seekers alike. Creating a job board from scratch can be a daunting task, but with JavaScript and GraphQL, the process becomes much simpler and more efficient. In this blog post, we will guide you through the process of building a job board using these powerful technologies. #javascript #graphql

## Prerequisites

To get started, you will need to have some basic understanding of JavaScript and GraphQL. Familiarity with front-end development and RESTful APIs will also be helpful.

## Setting Up the Project

First, create a new directory for your project and navigate to it in your terminal. Then, initialize a new npm project by running the following command:

```bash
npm init -y
```

Next, install the necessary dependencies by executing the following commands:

```bash
npm install express express-graphql graphql
```

## Building the Back-End

The back-end of our job board will be responsible for handling the data and providing it to the front-end. We will be using Express.js and GraphQL to create the API. Create a new file called `server.js` and add the following code:

```javascript
const express = require('express');
const { graphqlHTTP } = require('express-graphql');
const { buildSchema } = require('graphql');

// Define the schema
const schema = buildSchema(`
  type Job {
    id: ID!
    title: String!
    description: String!
    company: String!
  }

  type Query {
    jobs: [Job]
  }
`);

// Define the resolver
const root = {
  jobs: () => {
    // Implement logic to fetch jobs from the database or any other data source
    return [
      {
        id: 1,
        title: 'Front-end Developer',
        description: '...',
        company: 'ABC Inc.',
      },
      {
        id: 2,
        title: 'Backend Developer',
        description: '...',
        company: 'XYZ Corp.',
      },
    ];
  },
};

// Create an Express server
const app = express();

// Define the GraphQL endpoint
app.use(
  '/graphql',
   graphqlHTTP({
    schema: schema,
    rootValue: root,
    graphiql: true,
  })
);

// Start the server
app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```

The code above defines a simple GraphQL schema with a `Job` type and a `jobs` query. A resolver is implemented to fetch the jobs from a data source, which in this case is a hardcoded array. The Express server is then set up, and the GraphQL endpoint is exposed.

## Creating the Front-End

Now that we have our back-end set up, let's move on to the front-end development. We'll be using the popular JavaScript framework React to build the user interface. In your terminal, run the following command to create a new React project:

```bash
npx create-react-app job-board
```
Change your working directory to the newly created project folder using `cd job-board`. Replace the code in `src/App.js` with the following code:

```javascript
import React, { useEffect, useState } from 'react';

function App() {
  const [jobs, setJobs] = useState([]);

  useEffect(() => {
    fetch('/graphql', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify({ query: '{ jobs { title, description, company } }' }),
    })
      .then((response) => response.json())
      .then((data) => setJobs(data.data.jobs));
  }, []);

  return (
    <div>
      <h1>Job Board</h1>
      {jobs.map((job) => (
        <div key={job.id}>
          <h2>{job.title}</h2>
          <p>Description: {job.description}</p>
          <p>Company: {job.company}</p>
        </div>
      ))}
    </div>
  );
}

export default App;
```

In the code above, we have defined a simple React component that fetches the jobs from the GraphQL API and renders them on the page. The `useEffect` hook is used to fetch the data when the component mounts. The fetched jobs are stored in the `jobs` state variable, and a simple list is rendered on the page.

## Conclusion

Congratulations! You have successfully built a job board using JavaScript and GraphQL. This is just a basic implementation, and there is a lot more that can be customized and enhanced. You can add features like search functionality, sorting, and job filtering to make your job board even more powerful. Keep exploring and expanding your project to meet your specific requirements. Happy coding!