---
layout: post
title: "React.js integration with GraphQL"
description: " "
date: 2023-09-25
tags: [reactjs, graphql]
comments: true
share: true
---

React.js has become one of the most popular JavaScript libraries for building user interfaces. Its component-based architecture and declarative syntax make it a perfect choice for creating dynamic and interactive web applications. On the other hand, GraphQL is a query language for APIs that offers a more efficient and flexible way to request and retrieve data from servers. Combining React.js with GraphQL can provide a powerful and efficient solution for building modern web applications. In this article, we will explore how to integrate React.js with GraphQL.

## Setting up a GraphQL Server

Before we can integrate React.js with GraphQL, we need to have a GraphQL server setup. There are various options available for setting up a GraphQL server, including popular options like Apollo Server, Relay, and Prisma.

For simplicity, let's consider using Apollo Server. First, install Apollo Server package by running the following command:

```shell
npm install apollo-server graphql
```

Then, create a file named `server.js` and add the following code:

```javascript
const { ApolloServer } = require('apollo-server');
const { typeDefs, resolvers } = require('./schema');

const server = new ApolloServer({ typeDefs, resolvers });

server.listen().then(({ url }) => {
  console.log(`GraphQL server ready at ${url}`);
});
```

In the code above, we import `ApolloServer` from the `apollo-server` package and define the `typeDefs` and `resolvers` by importing them from a separate `schema.js` file. Finally, we create an instance of `ApolloServer` and start the server.

## Creating a React.js Application

Once the GraphQL server is set up, we can start integrating React.js with it.

To create a React.js application, make sure you have Node.js and npm installed. Then, open your terminal and run the following command:

```shell
npx create-react-app react-graphql-app
```

This command will create a new directory named `react-graphql-app` with a basic React.js application structure.

After that, navigate to the project directory by running:

```shell
cd react-graphql-app
```

## Installing Apollo Client

To connect our React.js application with the GraphQL server, we need to install Apollo Client. Apollo Client is a flexible GraphQL client library that makes it easy to work with GraphQL APIs in React applications.

Install Apollo Client by running the following command:

```shell
npm install @apollo/client graphql
```

## Integrating Apollo Client with React

Now, let's integrate Apollo Client with React by creating a new file named `ApolloProvider.js` in the `src` directory, and add the following code:

```javascript
import { ApolloClient, InMemoryCache, ApolloProvider } from '@apollo/client';

const client = new ApolloClient({
  uri: 'http://localhost:4000',
  cache: new InMemoryCache(),
});

const ApolloAppProvider = ({ children }) => {
  return (
    <ApolloProvider client={client}>
      {children}
    </ApolloProvider>
  );
};

export default ApolloAppProvider;
```

In the code above, we import the necessary Apollo Client components: `ApolloClient`, `InMemoryCache`, and `ApolloProvider`. We create a new instance of `ApolloClient` and pass the GraphQL server's URL (`uri`) and an instance of `InMemoryCache` to it. Finally, we wrap our application with `ApolloProvider` and pass the `client` as a prop.

## Writing GraphQL Queries in React Components

With Apollo Client integrated, we can now use GraphQL queries in our React components. Let's say we want to fetch a list of books from the GraphQL server. We can create a new component named `BookList.js` in the `src` directory, and add the following code:

```javascript
import { gql, useQuery } from '@apollo/client';

const GET_BOOKS = gql`
  query GetBooks {
    books {
      id
      title
      author
    }
  }
`;

const BookList = () => {
  const { loading, error, data } = useQuery(GET_BOOKS);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error!</p>;

  return (
    <div>
      {data.books.map((book) => (
        <div key={book.id}>
          <h3>{book.title}</h3>
          <p>{book.author}</p>
        </div>
      ))}
    </div>
  );
};

export default BookList;
```

In the code above, we import `gql` and `useQuery` from `@apollo/client`. The `GET_BOOKS` constant defines our GraphQL query using the `gql` function. We then use the `useQuery` hook to execute the query and retrieve the result. Finally, we render the list of books if the data is successfully fetched.

## Conclusion

Integrating React.js with GraphQL can significantly simplify the process of fetching and managing data in web applications. With tools like Apollo Client, it becomes even easier to make network requests and retrieve data from a GraphQL server seamlessly. By following the steps mentioned above, you can start building powerful and efficient React.js applications with GraphQL. Happy coding!

#reactjs #graphql