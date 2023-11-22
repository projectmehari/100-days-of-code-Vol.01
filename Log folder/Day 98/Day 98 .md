# Day 98

Tags: GraphQL
Date: November 20, 2023
Status: Done

**Tasks of the day**

- Mutations
- Subscriptions
- Schema

---

### Mutations

In GraphQL, a mutation is a type of query used to make changes to the data on the server, such as creating, updating, or deleting data. A mutation is structured similarly to a query, but with a “mutation” field at the top level instead of a “query” field.

The mutation includes fields that specify the data to be changed, the operation to be performed (create, update or delete) and also can include arguments to specify the specific data to be affected.

**Inline Fragments**

Like many other type systems, GraphQL schemas include the ability to define interfaces and union types

If you are querying a field that returns an interface or a union type, you will need to use inline fragments to access data on the underlying concrete type. It’s easiest to see with an example:

![Screen Shot 2023-11-19 at 4.46.48 PM.png](Day%2098%207833588e05a5416b97986e42e98baf52/Screen_Shot_2023-11-19_at_4.46.48_PM.png)

In this query, the hero field returns the type character, which might be either a human or a droid depending on the episode argument. In the direct selection, you can only ask for fields that exist on the character interface, such as name.

To ask for a field on the concrete type, you need to use an inline fragment with a type condition. Because the first fragment is labeled as …on Droid, the primaryFunction field will only be executed if the character returned from hero is of the Droid type. Similarly for the height field for the human type.

Named fragments can also be used in the same way, since a named fragment always has a type attached.

### Meta fields

Given that there are some situations where you don't know what type you'll get back from the GraphQL service, you need some way to determine how to handle that data on the client. GraphQL allows you to request `__typename`, a meta field, at any point in a query to get the name of the object type at that point.

![Screen Shot 2023-11-19 at 4.50.05 PM.png](Day%2098%207833588e05a5416b97986e42e98baf52/Screen_Shot_2023-11-19_at_4.50.05_PM.png)

In the above query, search returns a union type that can be on of three options. It would be impossible to tell apart the different types from the client without the __typename field.

GraphQL services provide a few meta fields, the rest of which are used to expose the introspection system.

**Operation Name**

In GraphQL, an operation name is an optional identifier that can be used to uniquely identify a query or a mutation in a document containing multiple operations. It can be used to provide more meaningful names for operations, making it easier to understand the purpose of the operation and to identify it in the event of an error.

In several of the examples above we have been using a shorthand syntax where we omit both the `query` keyword and the query name, but in production apps it's useful to use these to make our code less ambiguous.

Here’s an example that includes the keyword `query` as *operation type* and `HeroNameAndFriends` as *operation name* :

![Screen Shot 2023-11-19 at 4.52.17 PM.png](Day%2098%207833588e05a5416b97986e42e98baf52/Screen_Shot_2023-11-19_at_4.52.17_PM.png)

The *operation type* is either *query*, *mutation*, or *subscription* and describes what type of operation you're intending to do. The operation type is required unless you're using the query shorthand syntax, in which case you can't supply a name or variable definitions for your operation.

The *operation name* is a meaningful and explicit name for your operation. It is only required in multi-operation documents, but its use is encouraged because it is very helpful for debugging and server-side logging. When something goes wrong (you see errors either in your network logs, or in the logs of your GraphQL server) it is easier to identify a query in your codebase by name instead of trying to decipher the contents. Think of this just like a function name in your favorite programming language. For example, in JavaScript we can easily work only with anonymous functions, but when we give a function a name, it's easier to track it down, debug our code, and log when it's called. In the same way, GraphQL query and mutation names, along with fragment names, can be a useful debugging tool on the server side to identify different GraphQL requests.

---

### Subscriptions

In GraphQL, subscriptions are a way to push real-time updates to the client. They allow a client to subscribe to specific events or data changes on the server, and receive updates in real-time as soon as the event occurs or the data changes. Subscriptions are defined on the server and are structured similarly to queries and mutations.

A subscription includes a “subscription” field at the top level, followed by the fields that define the event or data change to be subscribed to. The client can initiate the subscription by sending the subscription query to the server, and the server will keep the connection open, listening for new events or data changes. Once the event occurs, or the data changes, the server will send the updated data to the client through the open connection.

To learn more, visit the following links:

- **[How GraphQL Subscriptions Work?](https://the-guild.dev/blog/subscriptions-and-live-queries-real-time-with-graphql)**

**Event based Subscriptions**

Event-based subscriptions in GraphQL are a way to push real-time updates to the client based on specific events that occur on the server. These events can be triggered by external sources such as user actions, sensor data, or other systems, or by internal actions such as database updates.

With event-based subscriptions, the client can subscribe to a specific event or set of events and receive updates in real-time as soon as the event occurs. This allows the client to receive notifications about important changes in the system without the need to constantly poll the server for updates.

**Live Queries**

In GraphQL, live queries, also known as “real-time queries” or “subscriptions to queries”, is a way to push real-time updates to the client, when the data that is being queried changes on the server. It allows the client to subscribe to a specific query and receive updates in real-time as soon as the data changes.

With live queries, the client can subscribe to a specific query and receive updates when the data that is being queried changes on the server. The client can also specify the fields and arguments of the query, and the server will only send updates for the fields that the client has requested.

**Defer Stream Directives**

In GraphQL, the “defer” and “stream” directives are used to control the handling of fields and their associated data. These directives allow developers to control how data is fetched and sent over the network, and can be used to optimize the performance of a GraphQL API.

The “defer” directive is used to delay the fetching of a field’s data until the data is actually needed by the client. This can be useful for improving the performance of an API by reducing the amount of data that needs to be fetched upfront.

---

### Schema

In GraphQL, a schema is a blueprint that defines the types, fields, and operations (queries and mutations) that are available to clients. The schema is the contract between the client and the server, specifying what data can be requested and how it can be modified.

A GraphQL schema is defined using the GraphQL Schema Definition Language (SDL), which is a human-readable syntax for defining the structure of a GraphQL API. The SDL includes keywords such as **type**, **query**, **mutation**, **field**, and **argument** to define the different components of a schema.

**Type System**

GraphQL is a strongly typed language. Type System defines various data types that can be used in a GraphQL application. The type system helps to define the schema, which is a contract between client and server. The commonly used GraphQL data types are as follows:

**Scalar**

Scalars are “leaf” values in GraphQL. There are several built-in scalars, and you can define custom scalars, too. (Enums are also leaf values.) The built-in scalars are:

- **String**, like a JSON or Ruby string
- **Int**, like a JSON or Ruby integer
- **Float**, like a JSON or Ruby floating point decimal
- **Boolean**, like a JSON or Ruby boolean (true or false)
- **ID**, which a specialized String for representing unique object identifiers
- **ISO8601DateTime**, an ISO 8601-encoded datetime
- **ISO8601Date**, an ISO 8601-encoded date
- **JSON**, This returns arbitrary JSON (Ruby hashes, arrays, strings, integers, floats, booleans and nils). Take care: by using this type, you completely lose all GraphQL type safety. Consider building object types for your data instead.
- **BigInt**, a numeric value which may exceed the size of a 32-bit integer

**Enums**

Enums also called as enumeration types are a special kind of scalar that is restricted to a particular set of allowed values. This allows you to:

- Validate that any arguments of this type are one of the allowed values
- Communicate through the type system that a field will always be one of a finite set of values

**Objects**

In GraphQL, an object is a type that represents a group of fields. Objects can be used to define the structure of a query or a mutation. Each field of an object can return a scalar value (such as a string or an integer) or another object, allowing for the creation of complex, nested data structures. In a GraphQL schema, objects are defined using the **type**keyword, followed by the object’s name and a set of fields in curly braces.

To learn more, visit the following:

- **[Object Types and Fields](https://graphql.org/learn/schema/#object-types-and-fields)**
- **[Object Types](https://graphql.org/graphql-js/object-types/)**

**Lists**

In GraphQL, a list is a type that represents an ordered collection of items. Lists are defined using square brackets, with the type of the items inside.

Lists are used to represent an array of items in a GraphQL schema, and can be used as the return type for a field in an object type. Lists can contain any type of items, including scalars and other objects, and can also be nested within other lists.

**Interfaces**

In GraphQL, an interface is a type that defines a set of fields that a type must implement. Interfaces are defined using the interface keyword, and can be used to define common fields for multiple types.

In GraphQL, lists can also be used within interfaces to define the return type for fields.

**Unions**

Unions are useful in cases where a field can return multiple types and you want to handle those types differently in your client. They also allow for more flexibility in how you structure your schema, as you can group types together that share common fields.

Unions don’t allow to specify a common set of fields to be queried across multiple types, but it allows to handle multiple types differently in your client.