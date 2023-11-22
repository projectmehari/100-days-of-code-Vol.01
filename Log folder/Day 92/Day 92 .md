# Day 92

Tags: WebSockets
Date: November 1, 2023
Status: Done

Task of the day

- WebSockets
- Requests with ES6
- Authentication and oAuth

---

### Introduction: what are WebSockets?

Imagine that your favorite basketball team is playing but you can’t watch the game live. You’re trying to follow the score on your phone but you can only get the live score by manually pressing a button to request new data. Needless to say, this isn’t a great user experience. Not only is pressing a button to get the latest score annoying, each request will take some time to process meaning that the score may have already changed by the time you get a response!

This is how an application using an HTTP connection might work and demonstrates the problem that *WebSocket connections* are here to solve. While plain old HTTP connections require the client to make a new request to the server in order to get new data, WebSocket connections require just a single request that establishes continuous, bidirectional communication enabling real-time updates of data shared between a client and a server.

A WebSocket connection is the solution that allows you to track the score of a basketball game in real-time, send and receive instant messages in an online chatroom, and play fast-paced multiplayer video games in your browser.

This lesson covers the core concepts of WebSockets while the next lesson will cover building a WebSockets application. In this lesson, you will learn how WebSockets:

- Benefit specific kinds of applications
- Have various modes of communication
- Are built upon the foundation of an HTTP request
- Create a persistent connection
- Allow for bidirectional communication
- Are superior to earlier attempts to mimic real-time updates
- Are initiated with something called a “handshake”
- Can be made more secure using the `wss://` protocol and HTTPS

### WebSocket Communication Patterns

![Screen Shot 2023-10-31 at 12.03.53 PM.png](Day%2092%20c0fca809b1d9458699a6c862070789d0/Screen_Shot_2023-10-31_at_12.03.53_PM.png)

The main feature of a WebSocket connection is that they allow continuous and bidirectional communication between a server and a client. In addition to the client sending data to the server, the server can also send data directly to the client – and this can happen without interruption!

For example, in the stock tracking application from the previous exercise, the server can continuously send the client the most up-to-date stock prices without the client requesting them.In addition to enabling uninterrupted communication between a client and a server, WebSocket connections also enable a communication pattern called *broadcasting*. Broadcasting is when a server sends the same message to many connected clients at once.

In some cases, the server may send a broadcast message to all connected users but often the server will choose only a subset of clients to broadcast a message to, such as in a chatroom application. For example, when a client’s message is sent to the server, the server can broadcast the message to all other connected clients. If the application supports smaller chat rooms, the server can determine which room the “sender” is in, and broadcast their message only to the other clients in the same room.

To summarize, WebSocket connections enable the three following communication patterns:

- client to server
- server to client
- server to many clients (broadcasting)

### Secure WebSocket Connections

You may notice that some websites (including Codecademy.com) use the `https://` protocol at the beginning of the URI while others use `http://`. So what’s the difference?

`[https://` is the secure version of the `http://` protocol](https://en.wikipedia.org/wiki/HTTPS) and is encrypting using the Transport Layer Security (TLS) protocol. Using an HTTPS server instead of a basic HTTP server safeguards your users from malicious attacks, such as a [Man In The Middle Attack](https://developer.mozilla.org/en-US/docs/Web/Security/Types_of_attacks#man-in-the-middle_mitm).

In the last exercise, we learned that during the WebSocket handshake a GET request is sent to the server using a `ws://` URI. Just like the `http://` protocol, `ws://` is an unencrypted protocol. So is there a more secure WebSocket protocol?

Yes! WebSocket connections can also use the TLS protocol to establish a more secure connection by using the `wss://` protocol (notice the extra `s`). Connections using the `wss://` protocol function just like `ws://` ones, except that the initial handshake takes place over HTTPS instead of HTTP.

### Apps that benefits from WebSockets

So far we’ve learned about the communication capabilities of WebSocket connections, the benefits of persistent connections, some details about how an HTTP connection can be upgraded to a WebSocket connection during the handshake process, and about secure WebSocket connections using `wss://`. As a final step, let’s discuss the applications for which WebSockets can be most beneficial.

WebSockets are the go-to approach for applications that need real-time data. Before WebSockets, many web developers had to rely on abusing the HTTP protocol by repeatedly making HTTP requests in quick succession to simulate continuous streams of data. This resulted in excessive headers, [latency buildup](https://developer.mozilla.org/en-US/docs/Web/Performance/Understanding_latency), and difficulty tracking each client’s current state.

However, WebSockets aren’t always the superior solution compared to basic HTTP connections so you should consider carefully if WebSockets are needed for your application. To help, you can ask yourself these two questions:

- Does the application involve multiple users communicating with each other?
- Is the application a window into server-side data that’s constantly changing?

Answering “yes” to either of these questions indicates the need for WebSockets technology.

![Screen Shot 2023-10-31 at 12.10.14 PM.png](Day%2092%20c0fca809b1d9458699a6c862070789d0/Screen_Shot_2023-10-31_at_12.10.14_PM.png)

### Review

Congratulations! In this lesson you have built a strong conceptual foundation of what WebSockets are and how they are created. With the growing number of real-time applications, WebSockets introduced an alternative to repetitive HTTP requests in order to build websites with continuous, bidirectional communication. Here’s what else you learned:

- WebSockets allow for bidirectional communication between client and server allowing for a continuous flow of real-time data.
- Common communication patterns involve both client and server bi-directional communication along with broadcasting, which refers to a server being able to communicate with multiple clients.
- WebSocket connections are persistent giving them the advantage of lower overhead and being stateful compared to a stateless connection protocol like HTTP.
- The foundation for a WebSocket connection begins with an HTTP request and response called a *handshake*which aims to replace the HTTP protocol with a WebSocket protocol over a single TCP connection.
- A client can initiate a handshake with a special `Upgrade` header. A server can complete the handshake by sending back a response with the `101 Switching Protocols`header.
- WebSockets are ideal for applications dealing with real-time data such as data trackers, multiplayer games, collaborative document editing, and social feeds and chat rooms.
- `wss://` connections function just like `ws://` ones, except that the initial handshake takes place over HTTPS instead of HTTP.

Now that you have a sense for what a WebSocket connection is and how they are formed we are ready to start building applications with WebSockets!

![Screen Shot 2023-10-31 at 12.11.57 PM.png](Day%2092%20c0fca809b1d9458699a6c862070789d0/Screen_Shot_2023-10-31_at_12.11.57_PM.png)

---

### Introduction to requests with ES6

There are many types of HTTP requests. The four most commonly used types of HTTP requests are GET, POST, PUT, and DELETE, in this lesson, we’ll cover GET and POST requests.

With a GET request, we’re retrieving, or getting, information from some source (usually a website). For a POST request, we’re posting information to a source that will process the information and send it back.

JavaScript uses an [event loop](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop)to handle asynchronous function calls. When a program is run, function calls are made and added to a stack. The functions that make requests that need to wait for servers to respond then get sent to a separate queue. Once the stack has cleared, then the functions in the queue are executed.

Web developers use the event loop to create a smoother browsing experience by deciding when to call functions and how to handle asynchronous events. We will go into event loops in more detail in the [Concurrency Model and Event Loop in JavaScript](https://www.codecademy.com/courses/learn-intermediate-javascript/articles/javascript-concurrency-model-and-event-loop) article.

To make asynchronous event handling easier, [promises](https://www.codecademy.com/resources/docs/javascript/promise)were introduced in ES6 JavaScript.

---

### Intro to POST Requests using Fetch

![Screen Shot 2023-10-31 at 1.28.20 PM.png](Day%2092%20c0fca809b1d9458699a6c862070789d0/Screen_Shot_2023-10-31_at_1.28.20_PM.png)

The object passed to the `fetch()` function as its second argument contains two properties: `method`, with a value of `'POST'`, and `body`, with a value of `JSON.stringify({id: '200'});`. This second argument determines that this request is a POST request and what information will be sent to the API.

A successful POST request will return a response body, which will vary depending on how the API is set up.

The rest of the request is identical to the GET request. A `.then()` method is chained to the `fetch()` function to check and return the `response` as well as throw an exception when a network error is encountered. A second `.then()` method is added on so that we can use the response however we may choose.

### Async GET Requests

![Screen Shot 2023-10-31 at 1.46.41 PM.png](Day%2092%20c0fca809b1d9458699a6c862070789d0/Screen_Shot_2023-10-31_at_1.46.41_PM.png)

In the following exercises, we’re going to take what we’ve learned about chaining Promises and make it simpler using functionality introduced in ES8: `[async](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)` and `[await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)`. You read that right, you did the hard part already. Now it’s time to make it easier.

The structure for this request will be slightly different. We will use the new keywords `async` and `await`, as well as the `try` and `catch`statements.

Take a look at the diagram on the right.

Here are some key points to keep in mind as we walk through the code:

- The `async` keyword is used to declare an `async`function that returns a promise.
- The `await` keyword can only be used within an `async` function. `await`suspends the program while waiting for a promise to resolve.
- In a `[try...catch`statement](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch), code in the `try` block will be run and in the event of an exception, the code in the `catch` statement will run.

Study the `async` `getData()`function to the right to see how the request can be written using `async` and `await`.

### Async POST Requests

![Screen Shot 2023-10-31 at 1.55.52 PM.png](Day%2092%20c0fca809b1d9458699a6c862070789d0/Screen_Shot_2023-10-31_at_1.55.52_PM.png)

Now that you’ve made an `async` GET request, let’s start getting familiar with the `async` POST request.

As we’ve seen before, a POST request requires more information. Take a look at the diagram to the right.

We still have the same structure of using `try` and `catch` as the `async` GET request we just learned about. But, in the `fetch()` call, we now have to include an additional argument that contains more information like `method` and `body`.

The `method` property value is set to `'POST'` to specify the type of request we are making. Then we have to include a `body` property with the value of `JSON.stringify({id: 200})`.

### Review

- GET and POST requests can be created in a variety of ways.
- We can use `fetch()` and `async`/`await` to asynchronous request data from APIs.
- Promises are a type of JavaScript object that represents data that will eventually be returned from a request.
- The `fetch()` function can be used to create requests and will return promises.
- We can chain `.then()`methods to handle promises returned by the `fetch()` function.
- The `async` keyword is used to create asynchronous functions that will return promises.
- The `await` keyword can only be used with functions declared with the `async` keyword.
- The `await` keyword suspends the program while waiting for a promise to resolve.

---

## Authentication and OAuth

**Password authentication**

The most common implementation of authentication requires a user to input their username or email and a password. The application’s server then checks the supplied credentials to determine if the user exists and if the supplied password is correct. If the credentials are correct, the user is logged in and able to use the application as that user.

Typically, upon a successful login, the application will respond with an *authentication token* (or auth token) for the client to use for additional HTTP requests. This token is then stored on the user’s computer, preventing the need for users to continuously log in.

This token generally expires after a certain amount of time, ensuring the correct user is using the application over time as well.

### API Keys

While it is common to think of authentication as the interaction between a human user and an application, sometimes the user is another application.

Many apps expose interfaces to their information in the form of an API (application program interface). For example, the [Spotify API](https://developer.spotify.com/web-api/) provides endpoints for almost all of its functionality. This allows applications to fetch data from the Spotify music catalog and manage user’s playlists and saved music.

Since these external requests could overwhelm a service and also access user information, they need to be secured using authentication.

The most basic pattern for API access from another application is using an *API key*.

Public APIs usually provide a developer portal where you can register your application and generate a corresponding API key. This key is then unique to your application. When your application makes a request, this key is sent along with it. The API can then verify that your application is allowed access and provide the correct response based on the permission level of your application.

The API can track what type and frequency of requests each application is making. This data can be used to [throttle requests](https://en.wikipedia.org/wiki/Throttling_process_(computing)) from a specific application to a pre-defined level of service. This prevents applications from spamming an endpoint or abusing user data, since the API can easily block that application’s API key and prevent further malicious use of the API by that application.

### OAuth

For many applications, a generic developer-level API key is not sufficient. As mentioned earlier, APIs sometimes have the ability to provide access to user-level data. However, most services only provide this private data if the user enables it.

For example, Facebook doesn’t want Tinder to access all of their users’ data, just the users who have opted in to allowing the sharing of data to better help them find a match in their area.

A basic approach to this problem might be to have the user provide their login credentials to the intermediary application, but this is not very secure and would give full access to the requesting application, when the requesting application might only need a very limited set of privileges to function.

**OAuth** defines a more elegant approach to this problem. It was developed in November 2006 by lead Twitter developer Blaine Cook and version 1.0 was published in April 2010.

OAuth is an **open standard** and is commonly used to grant permission for applications to access user information without forcing users to give away their passwords.

An open standard is a publicly available definition of how some functionality should work. However, the standard does not actually build out that functionality.

As a result, each API is required to implement their own version of OAuth and therefore may have a slightly different implementation or flow. However, they’re all based around the same OAuth specification.

This can make using a new OAuth API a little more frustrating. However, with time you will begin noticing the similarities between API authentication flows and be able to use them in your applications with increasing ease. Below is a summary of the standard OAuth flow.

### Generic OAuth Flow

Many applications implementing OAuth will first ask the user to select which service they would like to use for credentials:

![https://content.codecademy.com/programs/react/authentication/authentication_login.png](https://content.codecademy.com/programs/react/authentication/authentication_login.png)

After selecting the service, the user will be redirected to the service to login. This login confirms the user’s identity and typically provides the user with a list of permissions the originating application is attempting to gain on the user’s account.

If the user confirms they want to allow this access, they will be redirected back to the original site, along with an *access token*. This access token is then saved by the originating application.

Like a developer API key, this access token will be included on requests by the application to prove that the user has granted access and enable access to the appropriate content for that user. When a user returns to the application, the token will be retrieved and they will not have to re-authenticate.

### OAuth 2

Since OAuth evolved out of Twitter, there were important use cases not originally considered as part of the specification. Eventually, this led to the creation of a new version of the specification, called *OAuth 2*.

Among other improvements, OAuth 2 allows for different authentication flows depending on the specific application requesting access and the level of access being requested.

OAuth 2 is still an open standard, so each API will have its own flow based on its particular implementation. Below, we’ll discuss a few of the common OAuth 2 flows and how they are used.

### Client Credentials Grant

Sometimes an application will not need access to user information but may implement the added security and consistency of the OAuth 2 specification. This type of grant is used to access application-level data (similar to the developer API key above) and the end user does not participate in this flow.

Instead of an API key, a *client ID* and a *client secret* (strings provided to the application when it was authorized to use the API) are exchanged for an access token (and sometimes a *refresh token*). We will discuss refresh tokens in more depth later.

This flow is similar to our first example, where an email and password were exchanged for an authentication token.

**It is essential to ensure the client secret does not become public information, just like a password. As a result, developers should be careful not to accidentally commit this information to a public git repository. Additionally, to ensure integrity of the secret key, it should not be exposed on the client-side and all requests containing it should be sent server-side.**

Similar to the previously-mentioned keys, the returned access token is included on requests to identify the client making the requests and is subject to API restrictions.

This access token is often short-lived, expiring frequently. Upon expiration, a new access token can be obtained by re-sending the client credentials or, preferably, a refresh token.

Refresh tokens are an important feature of the OAuth 2 updates, encouraging access tokens to expire often and, as a result, be continuously changed (in the original OAuth specification, access tokens could last for time periods in the range of years). When a refresh token is used to generate a new access token, it typically expires any previous access tokens.

## **Authorization Code Grant**

This flow is one of the most common implementations of OAuth and will look familiar if you’ve ever signed into a web application with Google or Facebook. It is similar to the OAuth flow described earlier with an added step linking the requesting application to the authentication.

A user is redirected to the authenticating site, verifies the application requesting access and permissions, and is redirected back to the referring site with an *authorization code*.

The requesting application then takes this code and submits it to the authenticating API, along with the application’s client ID and client secret to receive an access token and a refresh token. This access token and refresh token are then used in the same manner as the previous flow.

To avoid exposing the client ID and secret, this step of the flow should be done on the server side of the requesting application.

Since tokens are tied both to users and requesting applications, the API has a great deal of control over limiting access based on user behavior, application behavior, or both.

## **Implicit Grant**

The previous two methods cause the client secret key to be exposed, so they need to be handled server-side. Some applications may need to access an OAuth API but don’t have the necessary server-side capabilities to keep this information secure.

The *Implicit Grant OAuth flow* was designed for this very use case. This flow prompts the user through similar authorization steps as the Authorization Code flow, but does not involve the exchange of the client secret.

The result of this interaction is an access token, and typically no refresh token. The access token is then used by application to make additional requests to the service, but is not sent to the server side of the requesting application.

This flow allows applications to use OAuth APIs without fear of potentially exposing long-term access to a user or application’s information.

## **Conclusion**

OAuth provides powerful access to a diverse set of sites and information. By using it correctly, you can reduce sign-up friction and enrich user experience in your applications.