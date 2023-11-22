# Day 97

Tags: GraphQL
Date: November 19, 2023
Status: Done

The next 4 days will be spent reviewing GraphQL and its relation to web service API’s

**Tasks of the day**

- Introduction to GraphQL
- GraphQL Queries

---

### GraphQL introduction

GraphQL is a query language and runtime for APIs. It is used to build and consume web service APIs.

GraphQL allows clients to make a single API call to request exactly the data they need, in a predictable format. This allows for more efficient and flexible data retrieval, compared to traditional REST APIs where the client has to make multiple API calls to different endpoints, and may receive more data than it needs.

With GraphQL, the client defines the structure of the data it needs, by sending a query to the server. The server then returns the requested data in the same structure, as defined by the query. The client can also make mutations to update or create data on the server.

**What is GraphQL**

GraphQL is a query language for your API, and a server-side runtime for executing queries using a type system you define for your data. GraphQL isn’t tied to any specific database or storage engine and is instead backed by your existing code and data.
A GraphQL service is created by defining types and fields on those types, then providing functions for each field on each type.

To learn more, visit the following links:

- **[Introduction to graphQL](https://graphql.org/learn/)**
- **[Tutorial - What is graphQL?](https://www.howtographql.com/basics/0-introduction/)**

**Problems GraphQL solves**

GraphQL solves several problems commonly faced when building APIs, including:

- **Over-fetching:** With REST APIs, the client often receives more data than it needs, resulting in wasted bandwidth and slow performance. GraphQL allows the client to specify exactly the data it needs, reducing over-fetching.
- **Under-fetching:** With REST, the client often has to make multiple requests to different endpoints to gather all the data it needs, resulting in additional latency and complexity. GraphQL allows the client to request all the necessary data in a single request.
- **Inefficient versioning:** With REST, creating a new endpoint for each version of an API can quickly become cumbersome and hard to maintain. GraphQL allows for seamless versioning by adding new fields and types, rather than creating new endpoints.
- **Lack of flexibility:** REST APIs are typically fixed, meaning that the client has to work with the data structure provided by the API. GraphQL allows the client to request exactly the data it needs and receive it in a predictable format, increasing flexibility.

**Thinking in Graphs**

“Thinking in Graphs” is a mindset or approach when working with GraphQL. It refers to the way that data is organized and queried in GraphQL, which is based on the concept of a graph.
In GraphQL, data is represented as a graph, where nodes represent objects and edges represent relationships between them. This allows for a more flexible and intuitive way of querying data, as the client can specify exactly the data it needs by following the relationships between nodes in the graph.

**GraphQL on the Frontend**

In GraphQL, the frontend refers to the client-side of the application, typically the web or mobile app that the end-user interacts with.

When using GraphQL on the frontend, developers can use a GraphQL client library, such as **Apollo Client or Relay**, to interact with the GraphQL server. These libraries provide a way to easily send GraphQL queries and mutations to the server and handle the response.

By using GraphQL on the frontend, developers can benefit from the flexibility and efficiency of GraphQL when querying data. Instead of having to make multiple REST API calls or hardcode data into the frontend, the client can specify exactly the data it needs in a single request, and the server will return it in a predictable format.

![Untitled.png](Day%2097%20fa0a58c9037d42b690cda6701f1f5b95/Untitled.png)

**GraphQL on the backend**

In GraphQL, the backend refers to the server-side of the application, where the data is stored and processed.

When using GraphQL on the backend, developers can create a GraphQL server that handles the incoming GraphQL queries and mutations from the frontend. This can be implemented using a GraphQL library or framework, such as Apollo Server, Express-GraphQL, or GraphQL-Java.

The GraphQL server is responsible for handling the incoming queries and mutations, validating them against a schema, and executing them by fetching data from the database or other data sources. The server then returns the requested data to the client in a predictable format, as defined by the schema.

---

### GraphQL Queries

GraphQL is a query language for APIs. It provides a simple and flexible syntax for making requests to a server to retrieve specific data. In GraphQL, a query is a request made to the server to fetch data. The query specifies the fields of the data that should be returned, and the server responds with the requested data.

A GraphQL query is structured as a single object, with a “query” or “mutation” field at the top level. The “query” field is used to retrieve data, while the “mutation” field is used to make changes to the data. The query is written in a specific format and is executed by the server to retrieve the requested data.

### **What are Queries**

In GraphQL, a query is a request made by the client to the server to retrieve data. Queries are used to fetch data from the server and are structured as a hierarchical tree of fields, which correspond to the properties of the data being requested.

**Field**
 In GraphQL, fields are the individual pieces of data that can be queried or modified. They represent the properties of the data being requested or modified, and are the building blocks of queries and mutations. Fields are defined in the GraphQL schema, which is a blueprint of the data that can be queried and modified. The schema defines the types of data that can be queried, and the fields that are available for each type.

![Screen Shot 2023-11-19 at 4.25.20 PM.png](Day%2097%20fa0a58c9037d42b690cda6701f1f5b95/Screen_Shot_2023-11-19_at_4.25.20_PM.png)

**Aliases**
Aliases in GraphQL are a way to rename fields when they are requested in a query. They are useful in situations where a field is requested multiple times, but with different arguments, or when the field has a name that is not suitable for the client’s usage. They make it easy to distinguish and work with fields in the response and make the query more readable.

![Screen Shot 2023-11-19 at 4.29.52 PM.png](Day%2097%20fa0a58c9037d42b690cda6701f1f5b95/Screen_Shot_2023-11-19_at_4.29.52_PM.png)

**Arguments**
 Arguments in GraphQL are pieces of information that are passed to a field or a directive to specify additional details about how the field should be executed. They can be used to filter, sort, or paginate data, or to specify additional options when creating, updating, or deleting data. They can be passed as key-value pairs, defined as variables, and can be optional or required.

![Screen Shot 2023-11-19 at 4.31.46 PM.png](Day%2097%20fa0a58c9037d42b690cda6701f1f5b95/Screen_Shot_2023-11-19_at_4.31.46_PM.png)

**Directives**

Directives in GraphQL are a way to modify the execution of a query or a field. They are used to add additional behavior or validation to a query or a field, and can be applied to fields, operations (queries and mutations) and fragments. Directives can take one or more arguments to configure their behavior, and can be defined by the developer or used one of the built-in directives provided by GraphQL.

![Screen Shot 2023-11-19 at 4.32.49 PM.png](Day%2097%20fa0a58c9037d42b690cda6701f1f5b95/Screen_Shot_2023-11-19_at_4.32.49_PM.png)

**Variables**

Variables in GraphQL are a way to pass dynamic values to a query or a mutation. They allow the client to make a query more dynamic and flexible by passing in different values for the same argument. They are defined in the query or mutation using the **$** symbol followed by the variable name and a type, and their values must be passed in a separate JSON object. They also are type-safe, this means that variables must be passed values that are of the same type as defined in the query.

**Fragments**

In GraphQL, a fragment is a reusable piece of a GraphQL query that can be used to retrieve specific fields from one or more types of data. A fragment is defined using the “fragment” keyword, followed by the name of the fragment and the type of data it is querying. The fields to be retrieved are then specified within curly braces.

To learn more, visit the following links:

- **[Intro to Fragments in GraphQL](https://graphql.org/learn/queries/#fragments)**