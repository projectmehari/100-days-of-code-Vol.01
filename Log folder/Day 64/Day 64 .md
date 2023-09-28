# Day 64

Tags: Testing React
Date: September 16, 2023
Status: Done

Task of the day

- API Calls
    - GraphQL:Apollo
    - REST: Axios
- Testing
    - Test Automation
    - Playwright
    - Jest
    - React Testing Library

---

### API Calls

APIs, short for Application Programming Interfaces, are software-to-software interfaces. Meaning, they allow different applications to talk to each other and exchange information or functionality. This allows businesses to access another business’s data, piece of code, software, or services in order to extend the functionality of their own products — all while saving time and money. There are several options available to make API calls from your React.js applications

**React**

Built-in React APIs: In addition to hooks and components, the react package exports a few other APIs that are useful for defining components. This page lists all the remaining modern React APIs

- `[createContext](https://react.dev/reference/react/createContext)` lets you define and provide context to the child components. Used with `[useContext`.](https://react.dev/reference/react/useContext)
- `[forwardRef](https://react.dev/reference/react/forwardRef)` lets your component expose a DOM node as a ref to the parent. Used with `[useRef`.](https://react.dev/reference/react/useRef)
- `[lazy](https://react.dev/reference/react/lazy)` lets you defer loading a component’s code until it’s rendered for the first time.
- `[memo](https://react.dev/reference/react/memo)` lets your component skip re-renders with same props. Used with `[useMemo](https://react.dev/reference/react/useMemo)` and `[useCallback`.](https://react.dev/reference/react/useCallback)
- `[startTransition](https://react.dev/reference/react/startTransition)` lets you mark a state update as non-urgent. Similar to `[useTransition`.](https://react.dev/reference/react/useTransition)

---

### [Axios](https://www.freecodecamp.org/news/how-to-use-axios-with-react/)

The most common way for frontend programs to communicate with servers is through the HTTP protocol. You are probably familiar with the Fetch API and the XMLHttpRequest interface, which allows you to fetch resources and make HTTP requests.

Axios is a client HTTP API based on the XMLHttpRequest interface provided by browsers.

**How to use Axios with React: The Definitive guide**

**What is Axios**

Axios is an HTTP client library that allows you to make requests to a given endpoint

![Untitled](Day%2064%205629e46ff834481a892119d75cb00a50/Untitled.png)

This could be an external API or your own backend Node.js server, for example. By making a request, you expect your API to perform an operation according to the request you made.

For example, if you make GET request, you expect to get back data to display in your application.

**Why use Axios in React**

There are a number of different libraries yo ucan use to make these requests, so why choose Axios?

Here are five reasons why you should use Axios as your client to make HTTP requests

1. It has good defaults to work with JSON data. Unlike alternatives such as the Fetch API, you often don't need to set your headers. Or perform tedious tasks like converting your request body to a JSON string.
2. Axios has function names that match any HTTP methods. To perform a GET request, you use the `.get()` method.
3. Axios does more with less code. Unlike the Fetch API, you only need one `.then()` callback to access your requested JSON data.
4. Axios has better error handling. Axios throws 400 and 500 range errors for you. Unlike the Fetch API, where you have to check the status code and throw the error yourself.
5. Axios can be used on the server as well as the client. If you are writing a Node.js application, be aware that Axios can also be used in an environment separate from the browser.

---

### **Getting Started with the Test Automation Pyramid – An Ultimate Guide**

The Testing Pyramid is a framework that can help both developers and QAs create high-quality software. It reduces developers time to identify if a change they introduced breaks the code. It can also help build a more reliable test suite.

- Essentially, the testing pyramid, also referred to as the test automation pyramid, lays out the types of tests that should be included in an automated test suite. It also outlines the sequence and frequency of these tests.
- The whole point is to offer immediate feedback to ensure that code changes do not disrupt existing features.

### The different levels of a Test Automation Pyramid

This test automation pyramid or a testing pyramid operates through three levels:

1. [Unit Tests](https://www.browserstack.com/guide/unit-testing-a-detailed-guide)
2. [Integration Tests](https://www.browserstack.com/guide/integration-tests-on-flutter-apps)
3. [End-to-End Tests](https://www.browserstack.com/guide/end-to-end-testing)

---

### **Jest**

Jest is a delightful JavaScript Testing Framework with a focus on simplicity. It works with projects using: Babel, TypeScript, Node, React, Angular, Vue and more!

[https://www.youtube.com/watch?v=FgnxcUQ5vho](https://www.youtube.com/watch?v=FgnxcUQ5vho)