# Day 51

Tags: Next.js, React
Date: September 5, 2023
Status: Done

Task of the day

- Server-side rendering
- [Learn React Testing](https://www.codecademy.com/learn/learn-react-testing)
- **[How to Deploy a Website](https://www.codecademy.com/learn/deploy-a-website)**
    - Tried to instal jeykell static website but ran into an issue with installing ruby on Mac, will attempt this another day.
- [Next.js](https://www.youtube.com/watch?v=1WmNXEVia8I)

---

### ****What is server-side rendering?****

**Server-side rendering (SSR)**, is the ability of an application to contribute by displaying the web-page on the server instead of rendering it in the browser. Server-side sends a fully rendered page to the client; the client’s JavaScript bundle takes over and allows the SPA framework to operate. There is also **client-side rendering** which slows down the procedure of viewing and interacting with the web page.

### **Advantages of using server-side rendering**

- It enables pages to load faster which provides a better user experience.
- It plays an important role in SEO (search engine optimization) and correctly indexes webpages. This happens because Google favors web pages with faster load time.
- It provides body to the HTML pages for all server ships.
- It assists with loading the page when the user has a slow internet connection.
- It assists in loading the page when the user has an outdated device.

---

**UNIT TESTING WITH JEST**

### **Review**

Great work! We have covered a lot in this lesson. Let’s take a moment to review:

- We have learned that Jest is an easy-to-use framework for testing in a JavaScript environment because it combines a test-runner with assertion methods like the `expect()` API.
- We also learned some of the basic syntax involved with creating a simple unit test, such as the `it()` function.
- After tackling basic unit tests, we adventured into the realm of testing asynchronous code with Jest by using the `done`parameter to wait for asynchronous callbacks and the `async`/`await` keywords to wait for Promises to resolve.
- Lastly, we learned how to mock functions using `jest.fn()`and make use of mocked modules with `jest.mock()` by mocking the Axios module.

---

**REACT TESTING LIBRARY**

### **What is React Testing Library?**

In this lesson, you will learn how to test your React components with the **[R**eact **T**esting **L**ibrary (RTL)](https://testing-library.com/docs/react-testing-library/intro/). React Testing Library is a UI-layer testing framework that helps us ensure that our React components are rendering and behaving properly.

The main advantages of RTL over other UI-layer testing frameworks are:

- It is built explicitly for testing React components.
- It allows us to test our components in a way that mimics real user interactions.

The logic behind this is that a user will not care about the implementation details of a React component, such as the component’s state, the props passed to it, etc. The user will only care about whether or not they are able to use the app. We should test our application with these same motivations.

Before we jump into the lesson, let’s take a quick look at an example that shows off the power and elegance of the React Testing Library.

> Note: this lesson assumes that you have a basic understanding of the Jest testing framework.
> 

Take a moment to observe the code sample below. It shows a `GroceryList` component with a few items. You can click on the checkboxes to mark that you’ve added one of these items to your cart. You can see the code for this component in the file `GroceryList.js`.

```jsx
const GroceryList = () => {
  return (
  <div>
    <h1>Grocery List</h1>
      <ul>
        <li>
          <label htmlFor="item1">Apples</label>
          <input type="checkbox" id="item1"/>
        </li>
        <li>
          <label htmlFor="item2">Milk</label>
          <input type="checkbox" id="item2"/>
        </li>
        <li>
          <label htmlFor="item3">Cereal</label>
          <input type="checkbox" id="item3"/>
        </li>
      </ul>
    </div>
  )
};

export default GroceryList;

```

Next, let’s look at a unit test using RTL. Observe how it mimics a user clicking the first checkbox:

```jsx
import { render, screen, cleanup } from '@testing-library/react';
import GroceryList from './components/GroceryList';
import userEvent from '@testing-library/user-event';

it('should mark the first checkbox as checked', () => {
  // render the grocery list
  render(<GroceryList />);
  // grab the apple item
  const appleItem = screen.getByLabelText('Apples');
  // simulate a "click" on the apple checkbox
  userEvent.click(appleItem);
  // assert that the apple checkbox was checked
  expect(appleItem).toBeChecked();
});

```

Can you see how we are able to test the `GroceryList`component without knowing any of its implementation details? This is what makes RTL so powerful. We can test our React components as if we are a real user and not worry about the specific logic that went behind coding them.

Don’t worry if you cannot understand every single line of the code snippet above. In the upcoming exercises, you’ll gain a strong understanding of React Testing Library and be able to do the following:

- Virtually render React components in the testing environment
- Use the `screen` object to query elements in the DOM to make assertions
- Utilize the `user-event` library extension to simulate user interactions in the DOM
- Understand the difference between query methods in React Testing Library
- Work with asynchronously rendered elements and understand the best practices to test them
- Verify the behavior of components that make API calls

---

### **Review**

Good job! We can now use React Testing Library (RTL) to test our React components. Let’s quickly review what we’ve learned so far:

- React Testing Library allows us to test React components by mimicking real user interactions.
- In order to make your component available in the unit test, we have to use the `render()` function. We can check to see the available components in our rendered DOM by using the `screen.debug()` method. `screen` is a special object that can be thought of as a representation of the browser window.
- RTL has built-in query methods (`.getByX`,`.findByX`,`.queryByX`) that allow us to extract the DOM nodes from your components. We can use these query methods by using the `screen` object, e.g., `screen.getByText()`.
- We can test the behavior of these extracted nodes by using the jest matchers provided by the `@testing-library/jest-dom` library. E.g. `expect().toBeChecked()`.
- We can mimic user interactions by using methods provided by the `testing-library/user-event` library. An example method is `userEvent.click()`.
- Besides `.findByX`, RTL has the `waitFor()` asynchronous function that can be used to test asynchronous events such as an element being removed asynchronously or a component making an API call.
- We can test with accessibility in mind by using `ByRole`query variants to help us discover accessibility holes in our applications

---

**CREATE A STATIC WEBSITE USING JEKYLL**

### **Deploying: Overview**

In this course, you’ll learn how to deploy a [static site](https://en.wikipedia.org/wiki/Static_web_page) to the Internet.

What exactly do we mean by *deploy*, or *deploying*?

Deploying means making content or software accessible and available for use.

The website that you’ll deploy in this course will be public, or “live”, on the Internet. It will be accessible to anyone (with open Internet access), at anytime, anywhere in the world.

By the end of this course, you will have:

1. Generated a static site
2. Deployed it to the Internet
3. Given the website a custom domain name

Let’s begin!

![Screen Shot 2023-09-04 at 2.34.09 PM.png](Day%2051%20a4ef8af74f144404af85e23b683acd40/Screen_Shot_2023-09-04_at_2.34.09_PM.png)

---

### Introduction to Next.Js

⭐️ Course Contents ⭐️

- Introduction

**A react framework**

**file-system routing

- What is Next.js
- Tools: Node.js, VS Code, and the command line
- Setting up Next.js
- Setting the Sanity Studio CMS
- Connecting Next.js with your content lake
- Making a simple navigation bar in _app.js
- Making your first page template in index.js
- Setting up dynamic routes with [slug].js
- Diving into data fetching and pre-rendering with getStaticPaths & getStaticProps
- Create a like button with API routes and serverless functions
- Adding live real-time preview with [Sanity.io](http://sanity.io/)'s content lake
- Set up automatic deployment with GitHub and Vercel
- Summary: What you have learned and next steps

---