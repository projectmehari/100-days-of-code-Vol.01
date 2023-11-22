# Day 99

Tags: GraphQL
Date: November 21, 2023
Status: Done

**Tasks of the day**

- Validation
- Execution
- Serving over the internet

---

### Validation

Validation in GraphQL refers to the process of checking whether a GraphQL query or mutation conforms to the rules and constraints defined in the GraphQL schema. This can include checking that the query or mutation includes the required fields, that the arguments passed to a field are of the correct type, and that the values passed to fields or arguments fall within the expected range.

By using the type system, it can be predetermined whether a GraphQL query is valid or not. this allows servers and clients to effectively inform developers when an invalid query has been created, without having to rely on runtime checks.

To start, let’s take a complex valid query. This is a nested query, similar to an example from the previous section, but with the duplicated field factored out into a fragment.

![Screen Shot 2023-11-21 at 5.30.54 PM.png](Day%2099%208aacb438919e488da27080e6cb27ff9f/Screen_Shot_2023-11-21_at_5.30.54_PM.png)

And this query is valid. Let’s take a look at some invalid queries…

A fragment cannot refer to itself or create a cycle, as this could result in an unbounded result! Here’s the same query above but without the explicit three levels of nesting:

![Screen Shot 2023-11-21 at 5.34.31 PM.png](Day%2099%208aacb438919e488da27080e6cb27ff9f/Screen_Shot_2023-11-21_at_5.34.31_PM.png)

When we query for fields, we have to query for a field that exists on the given type. So as `hero` returns a `Character`, we have to query for a field on `Character`. That type does not have a `favoriteSpaceship` field, so this query is invalid:

![Screen Shot 2023-11-21 at 5.34.56 PM.png](Day%2099%208aacb438919e488da27080e6cb27ff9f/Screen_Shot_2023-11-21_at_5.34.56_PM.png)

---

### Execution

In GraphQL, execution refers to the process of executing a query or mutation and returning the result to the client. The execution process includes several steps such as parsing, validation, and data retrieval, that are performed by the GraphQL engine to produce the final response to the client.

**Validation: producing the result**

In GraphQL, producing the result refers to the process of generating the final response to a query or mutation. This includes executing the resolvers for the selected fields, gathering the data, and formatting the response according to the requirements of the query or mutation.

When a client sends a query or mutation to a GraphQL server, the server performs several steps to produce the result:

- Parsing: The query or mutation is parsed and converted into an abstract syntax tree (AST)
- Validation: The query or mutation is validated against the schema to ensure that it is well-formed and adheres to the schema definition.
- Execution: The resolvers for the selected fields are executed, and the data is retrieved from the data source.
- Formatting: The data is formatted and organized into the final response, according to the requirements of the query or mutation.

**Root fields**

In GraphQL, the root fields are the top-level fields that are available to clients in a query or mutation. They are defined in the schema and are the entry point for client requests. The root fields represent the operations that can be performed on the data, such as querying for data or modifying data.

There are two types of root fields in GraphQL:

- **Query:** defines the fields that can be queried to retrieve data from the server.
- **Mutation:** defines the fields that can be used to create, update, or delete data on the server.

**Resolvers**

In GraphQL, a resolver is a function that is responsible for fetching the data for a field in a query or mutation. Resolvers are defined in the schema and are executed by the GraphQL server when a query or mutation is received.

Each field in a GraphQL schema has a corresponding resolver function that is responsible for returning the data for that field. The resolver function can retrieve the data from a database, a third-party API, or any other source, and return it to the client.

**Synchronous**

In GraphQL, a resolver is a function that is responsible for fetching the data for a field in a query or mutation. Resolvers are defined in the schema and are executed by the GraphQL server when a query or mutation is received.

A synchronous resolver is a type of resolver that runs and completes its execution before returning any value. It directly returns the result of the computation, without waiting for any external event such as a database query or a third-party API call.

**Asynchronous**

In GraphQL, a resolver is a function that is responsible for fetching the data for a field in a query or mutation. Resolvers are defined in the schema and are executed by the GraphQL server when a query or mutation is received.

An asynchronous resolver is a type of resolver that runs, but instead of returning the final value, it returns a promise that will be resolved with the final value. This allows the resolver to wait for an external event such as a database query or a third-party API call to complete before returning the result.

**Scalar Coercion**

In GraphQL, scalar coercion is the process of converting a value from one type to another, as it flows through the resolvers. This is needed when the input value for a field does not match the expected type, but can still be successfully converted to the correct type.

Scalar coercion can be implemented in the resolvers by using the **GraphQLScalarType** constructor to define a custom scalar type and providing a **coerce** function that can convert the input value to the correct type.

---

### Serving over internet

### **GraphQL over Websockets**

The WebSocket API is an advanced technology that makes it possible to open a two-way interactive communication session between the user’s browser and a server. With this API, you can send messages to a server and receive event-driven responses without having to poll the server for a reply.

**Real time**

Real-time in GraphQL refers to the ability to receive real-time updates from a GraphQL server. This allows clients to receive updates from the server as soon as they occur, rather than having to periodically poll the server for new data.

**Authorization**

Authorization in GraphQL refers to the process of controlling access to specific fields, types, or operations in a GraphQL schema based on user roles or permissions. It allows you to restrict access to certain data or functionality in your application based on the user’s role or permissions.

There are several ways to implement authorization in GraphQL:

- Using middleware
- Using schema directives
- Using a data source layer

### **GraphQL over HTTP**

GraphQL over HTTP refers to the ability to send GraphQL queries and mutations over the HTTP protocol. This allows clients to interact with a GraphQL server using the same standard HTTP methods and headers that are used for other types of web requests.

The most common way to send GraphQL queries and mutations over HTTP is by using the **POST** method, where the query or mutation is sent in the request body as a JSON payload. The server will then execute the query or mutation and return the result in the response body.

**Caching**

Caching is a technique that is used to improve the performance of a GraphQL server by reducing the number of requests that need to be made to the data source. It works by storing a copy of the data that has been requested by a client in a cache, and then returning that data from the cache instead of the data source when the same data is requested again.

There are several types of caching that can be used in GraphQL:

- Client-side caching
- Server-side caching
- CDN caching

**Batching**

Batching in GraphQL refers to the process of sending multiple queries or mutations in a single request. This allows the client to reduce the number of round trips to the server, and can improve the performance of the application.

There are several ways to implement batching in GraphQL:

- Using a batching library: This approach involves using a library such as apollo-link-batch-http, which provides a way to batch multiple queries or mutations into a single request.
- Using a middleware: This approach involves using a middleware such as graphql-batch, which allows you to batch multiple queries or mutations into a single request.
- Using a serverless function: This approach involves using a serverless function such as AWS Lambda, which allows you to batch multiple queries or mutations into a single request.

**Authorization**

Authorization in GraphQL refers to the process of controlling access to specific fields, types, or operations in a GraphQL schema based on user roles or permissions. It allows you to restrict access to certain data or functionality in your application based on the user’s role or permissions.

There are several ways to implement authorization in GraphQL:

- Using middleware
- Using schema directives
- Using a data source layer

### GraphQL over SSE

GraphQL over SSE (Server-Sent Events) is a way to use the Server-Sent Events (SSE) protocol to send real-time updates from the server to the client over a single HTTP connection.
SSE is a simple and efficient protocol for sending real-time updates from the server to the client over a single HTTP connection. It’s supported by most modern web browsers and it’s easy to implement on the server side.
To implement GraphQL over SSE, you can use a library such as graphql-sse which provides a way to send GraphQL updates over SSE. This library allows you to handle SSE connections and events, and to send and receive GraphQL updates over the SSE connection.

**Authorization**

Authorization in GraphQL refers to the process of controlling access to specific fields, types, or operations in a GraphQL schema based on user roles or permissions. It allows you to restrict access to certain data or functionality in your application based on the user’s role or permissions.

There are several ways to implement authorization in GraphQL:

- Using middleware
- Using schema directives
- Using a data source layer