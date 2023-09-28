# Day 63

Tags: React, Tailwind
Date: September 14, 2023
Status: Done

Task of the day

- Routers
    - React Router
- State Management
    - Redux
- Styling
    - Tailwind

---

### Routing

Routing is an essential concept in single page applications (SPA). When your application is divided into separated logical sections, and all of them are under their own URL, your users can easily share links among each other.

**Resource**

[How to use Routing in React JS: A Comprehensive Guide 2023 - TeachingBee](https://teachingbee.in/how-to-use-routing-in-react-js/)

### Routers

React router is the most famous library when it comes to implementing routing in React applications.

[https://www.youtube.com/watch?v=aZGzwEjZrXc](https://www.youtube.com/watch?v=aZGzwEjZrXc)

---

### State management

Application state management is the process of maintaining knowledge of an application’s inputs across multiple related data flows that form a complete business transaction — or a session — to understand the condition of the app at any given moment. In computer science, an input is information put into the program by the user and state refers to the condition of an application according to its stored inputs — saved as variables or constants. State can also be described as the collection of preserved information that forms a complete session.

Core business applications process sensitive information like orders, payments, invoices and bills of material. This processing depends on the state of the application and results in changes to the balance of inventories, accounts and financial ledgers. State management allows developers to determine the state of the application to ensure the changes made appropriately reflect the real-world context and business processes.

**How state management works**

Overall, state management makes the state of an app visible in the form of a [data structure](https://searchsqlserver.techtarget.com/definition/data-structure), improving developers' ability to work with the app. State management libraries provide developers with the tools needed to create the data structures and change them when new actions occur.

There are two accepted models for state management: Front-end (also called client side), and back-end (sometimes called server side)

In front-end state management, the user's own app or browser maintains the program's state, often by having certain buttons or [UI](https://www.techtarget.com/searchapparchitecture/definition/user-interface-UI) features enabled or disabled and sending the state along with the message. The user interface connection ensures the user and the application are in harmony throughout the session.

In back-end state management, an application component will use an external data structure or database to record the final state when it's done processing activities. Processing the next message will start with retrieving the previous state from the database. The state variable in the data structure can also synchronize the user interface -- and through it the user -- with the state of the session.

```jsx
                        +------------------------+
                        | State Management       |
                        |                        |
                        | - Makes state of app   |
                        |   visible              |
                        +------------------------+
                                   |
                                   |
                     +-------------+-------------+
                     |                           |
                     v                           v
         +-----------------------+   +----------------------+
         | Front-end (Client-side)|   | Back-end (Server-side)|
         |                       |   |                      |
         | - User maintains      |   | - External data      |
         |   program's state     |   |   structure or        |
         | - UI interaction      |   |   database for state  |
         |   for state updates   |   |   management          |
         +-----------------------+   +----------------------+
                     |                           |
                     |                           |
                     v                           v
         +-------------------+       +--------------------+
         | User Interface    |       | Data Structure/DB  |
         |                   |       |                    |
         | - Enables/Disables|       | - Stores final     |
         |   UI features     |       |   state            |
         | - Sends state     |       | - Synchronizes UI  |
         |   with messages   |       |   with state        |
         +-------------------+       +--------------------+
```

**State management libraries**

Any implementation of state management is likely to enjoy the support of development tools collected in a state management library. These libraries ensure the implementations of front-end or back-end state management work together to successfully obtain and provide understanding and control of the application.

State management libraries speed the development of application state and make the state management code easier to maintain by enforcing common practices across multiple [stateful applications](https://www.techtarget.com/whatis/definition/stateful-app). It's critical to pick state management techniques that work for the application, as well as the best tool library to implement these techniques.

State management libraries are explicit to development techniques such as the development language or the front- or back-end nature of state control. It's important for development teams to research their options and make the best choice for both current and likely future needs.

```jsx
                 +------------------------------------------------+
                 |              State Management Overview         |
                 |                                                |
                 | - Implementation supported by development tools|
                 | - State Management Libraries                   |
                 | - Speed up development                         |
                 | - Enforce common practices                     |
                 | - Choose the right techniques and libraries    |
                 +------------------------------------------------+
                              |                         |
                              |                         |
               +--------------+--------------+  +---------------------------+
               |                             |  |                           |
               v                             v  v                           v
+----------------------+   +----------------+  +-------------------+  +-------------------+
| Front-end State Mgmt |   | Back-end State |  | Stateful         |  | Development      |
|                      |   | Mgmt           |  | Applications     |  | Techniques       |
| - Tools for UI       |   | - Tools for    |  | - Common         |  | - Development    |
|   state handling     |   |   server-side  |  |   practices      |  |   language       |
| - Cooperation        |   |   state control|  |   enforcement    |  | - Front-end      |
|   with libraries     |   |   libraries     |  |   across apps    |  |   or back-end    |
+----------------------+   +----------------+  +-------------------+  +-------------------+
```

**State management in application development**

Early applications controlled the user dialog, so the individual steps within a session were dictated by the process itself; write data to the user, accept changes, confirm them and commit them. With the advent of web applications based on the stateless vision of [HTML](https://www.theserverside.com/definition/HTML-Hypertext-Markup-Language), it became necessary to more clearly define state management practices.

When a session message -- such as an HTML page -- is received, it is interpreted based on the state, which is recorded as a variable or constant that every process can access. The record ensures that receiving, for example, a "confirmation" message while in the "waiting for confirmation" state is handled differently than it would be in the "waited too long for user response state."  That, in turn, ensures that application systems that update databases and produce durable business records are always synchronized with the real world.

```jsx
                       +------------------------------------------------+
                       |            Evolution of State Management       |
                       |                                                |
                       | - Early applications                           |
                       |   controlled user dialog                       |
                       | - State management practices                   |
                       |   for web applications                         |
                       | - Interpretation of session messages           |
                       | - Ensuring synchronization with databases      |
                       +------------------------------------------------+
                                  |                        |
                                  |                        |
               +------------------+----------------+  +------------------------+
               |                                     |  |                        |
               v                                     v  v                        v
+------------------------+            +----------------+  +-----------------------+
| Early Applications     |            | Web Applications|  | Session Messages      |
|                        |            |                |  |                       |
| - Controlled dialogs   |            | - Stateless HTML|  | - Interpretation based|
| - Dictated steps       |            | - State management|  |   on recorded state   |
| - Data handling        |            |   challenges   |  | - Handling different  |
|   and confirmation    |            |   in web apps  |  |   states              |
|   processes            |            |                |  | - Ensuring sync with  |
| - Commit to databases |            |                |  |   databases           |
+------------------------+            +----------------+  +-----------------------+
```

**Advantages of state management**

State management is essential in aligning and integrating core business application and the cloud. Without some form of state management, business activities as routine as the purchase of something or request for information would have to be structured as a single request or response exchange. This could put a significant burden on the user and would almost certainly reduce the effectiveness of the application. In some cases, such as the processing of an order, a stateless exchange could hide critical information like current stock levels, resulting in what could be a significant business impart on the seller and a major inconvenience to the buyer.

**Tools**

State management tools are typically offered in the form of state management libraries, designed for developers who want to build state awareness into their applications. Most of these tools are used to implement front-end state management because that mechanism is easiest to execute and offers the tightest integration with the application's user base. Front-end state control is also ideal for state management when the goal of development is to add a cloud front end to a business process.

Most tools work by adding a state object to something like [JavaScript](https://www.theserverside.com/definition/JavaScript). This object and its methods are then used to manage state and prevent loss of state under unusual conditions, including contamination by code or changes in [client-server](https://www.techtarget.com/searchnetworking/definition/client-server) relationships. Libraries like React focus almost entirely on the user interface. Other libraries, like Redux or Cerebral, provide an integrated form of state management used throughout the workflow. Flutter is an SDK that can be used a bit more broadly, in both front-end and back-end state management applications.

---

### [Redux](https://redux.js.org/introduction/getting-started)

Redux is a predictable state container for JavaScript apps. It helps you write applications that behave consistently, run in different environments (client, server, and native), and are easy to test. On top of that, it provides a great developer experience, such as **[live code editing combined with a time traveling debugger](https://github.com/reduxjs/redux-devtools)**.

Redux Toolkit (RTK) is a library for managing state in JavaScript applications. It is an opinionated set of tools and utilities for building Redux applications, and it is designed to make it easier and faster to build Redux applications.

RTK is often used as an alternative to writing Redux applications from scratch, as it provides a set of conventions and utilities that can make it easier and faster to build Redux applications.

---

### Styling

While “CSS in JS” is the most predominant way of styling modern frontend applications, there are several different ways to style your React applications whether it is vanilla CSS, **[CSS Modules](https://github.com/css-modules/css-modules)**, or **[CSS in JS](https://css-tricks.com/a-thorough-analysis-of-css-in-js/)** etc and each has several frameworks available.

**Tailwing**

[https://www.youtube.com/watch?v=hdGsFpZ0J2E](https://www.youtube.com/watch?v=hdGsFpZ0J2E)