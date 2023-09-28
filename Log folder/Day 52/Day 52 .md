# Day 52

Tags: GraphQL
Date: September 5, 2023
Status: Done

Task of the day 

- GraphQL

---

**Introduction to GraphQL**

GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

- GraphQL is a language designed for client applications to fetch the exact data needed from an API.
- GraphQL allows client applications to describe the type and shape of data required from a backend API.
- GraphQL enables client applications to call a single endpoint for any type of request.
- **GraphQL is like SQL, but for the front end.**

Now imagine that you need to build these three frontend components:

- A Profile component that shows user information
- A Post component that displays a post, its link, and the author’s name
- An Author component that shows a user’s details and list of post titles by the user

All these components require different shapes of data. With a traditional REST API, each different shape of data would require its own endpoint or require tacking numerous, ugly query parameters to the endpoint. For example, when the front end would request user data, there would be no way of specifying if you only want the ID and email of the user (no name), or you just want the name of the user. The API returns all of the user data. Good luck if your user data contains more parameters than the example above.

Requests are made using a special format that is used to describe the data The best way to learn this format is to write some GraphQL queries. Let’s pick the three components in the last section and write queries for their respective data requests in GraphQL.

[Introduction to GraphQL](https://thenewstack.io/introduction-to-graphql/)

---

[How to Execute a Simple GraphQL Query](https://thenewstack.io/how-to-execute-a-simple-graphql-query/)

**The Fullstack Tutorial for GraphQL**

[How to GraphQL - The Fullstack Tutorial for GraphQL](https://www.howtographql.com/)

---

### ****GraphQL With React Tutorial - Apollo Client****

- Increased mobile usage creates need for efficient data loading
- Variety of different frontend frameworks and platforms on the client-side
- Fast development speed & expectation for rapid feature development

### **GraphQL is the better REST**

**Data Fetching with REST vs GraphQL**

With a REST API, you would typically gather the data by accessing multiple endpoints. In the example, these could be `/users/<id>` endpoint to fetch the initial user data. Secondly, there’s likely to be a `/users/<id>/posts` endpoint that returns all the posts for a user. The third endpoint will then be the `/users/<id>/followers` that returns a list of followers per user.

### **Benefits of a Schema & Type System**

GraphQL uses a strong type system to define the capabilities of an API. All the types that are exposed in an API are written down in a *schema* using the GraphQL Schema Definition Language (SDL). This schema serves as the contract between the client and the server to define how a client can access the data.

Once the schema is defined, the teams working on frontend and backends can do their work without further communication since they both are aware of the definite structure of the data that’s sent over the network.

Frontend teams can easily test their applications by mocking the required data structures. Once the server is ready, the switch can be flipped for the client apps to load the data from the actual API.

### ****Core Concepts****

In this chapter, you’ll learn about some fundamental language constructs of GraphQL. That includes a first glimpse at the syntax for defining *types* as well as sending *queries* and *mutations*.

GraphQL has its own type system that’s used to define the *schema* of an API. The syntax for writing schemas is called [Schema Definition Language](https://www.prisma.io/blog/graphql-sdl-schema-definition-language-6755bcb9ce51) (SDL).

**Fetching Data with Queries**

When working with REST APIs, data is loaded from specific endpoints. Each endpoint has a clearly defined structure of the information that it returns. This means that the data requirements of a client are effectively *encoded* in the URL that it connects to.

The approach that’s taken in GraphQL is radically different. Instead of having multiple endpoints that return fixed data structures, GraphQL APIs typically only expose *a single endpoint*. This works because the structure of the data that’s returned is not fixed. Instead, it’s completely flexible and lets the client decide what data is actually needed.

That means that the client needs to send more *information* to the server to express its data needs - this information is called a *query*.

**Queries with Arguments**

In GraphQL, each *field* can have zero or more arguments if that’s specified in the *schema*. For example, the `allPersons` field could have a `last` parameter to only return up to a specific number of persons. Here’s what a corresponding query would look like:

---

### **Big Picture (Architecture)**

GraphQL has been released only as a *specification*. This means that GraphQL is in fact not more than a [long document](https://spec.graphql.org/) that describes in detail the behaviour of a *GraphQL server.*

**Use Cases**

In this section, we’ll walk you through 3 different kinds of architectures that include a GraphQL server:

1. GraphQL server *with a connected database*
2. GraphQL server that is a *thin layer in front of a number of third party or legacy systems* and integrates them through a single GraphQL API
3. A *hybrid approach of a connected database and third party or legacy systems* that can all be accessed through the same GraphQL API

All three architectures represent major use cases of GraphQL and demonstrate the flexibility in terms of the context where it can be used.

---

### ****React + Apollo Tutorial - Introduction****

[Getting Started with GraphQL, React and Apollo Tutorial](https://www.howtographql.com/react-apollo/1-getting-started/)