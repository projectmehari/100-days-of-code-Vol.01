# Day 36

Tags: Javascript
Date: August 9, 2023
Status: Done

Task of the day 

- JavaScript Syntax Part 2
- Building interactive websites
- Making a website Accessible
- Git and Github Part 1
- Portfolio project: Personal portfolio website

---

****Debugging Overview****

## **JavaScript Error Types**

Now that you can identify the type of error from an error stack trace, you might be wondering what the different types of errors mean.

Here are three common error types:

- **SyntaxError**: This error will be thrown when a typo creates invalid code — code that cannot be interpreted by the compiler. When this error is thrown, scan your code to make sure you properly opened and closed all brackets, braces, and parentheses and that you didn’t include any invalid semicolons.
- **ReferenceError**: This error will be thrown if you try to use a variable that does not exist. When this error is thrown, make sure all variables are properly declared.
- **TypeError**: This error will be thrown if you attempt to perform an operation on a value of the wrong type. For example, if we tried to use a string method on a number, it would throw a TypeError

## **Debugging Errors**

Here’s a process for efficiently working through your code’s errors one by one:

1. Run your code. Using the first error’s stack trace, identify the error’s type, description, and location.
2. Go to the file name and line number indicated by the error stack trace. Using the error type and description, identify the bug in your code.
3. Fix the bug and re-run your code.
4. Repeat steps 1-3 until your code no longer throws any errors.

## **Debugging with console.log()**

Let’s synthesize our workflow from the previous exercise into a reusable set of debugging steps.

1. Go to the beginning of the malfunctioning code. Print out all starting variables, existing values, and arguments using `console.log()`. If the values are what you expect, move on to the next piece of logic in the code. If not, you have identified a bug and should skip to step 3.
2. After the next piece of logic in your code, add `console.log()` statements to ensure updated variables have the values that you now expect and that the block of code is being executed. If that logic is executing properly, continue repeating this step until you find a line not working as expected, then move to step 3.
3. Fix the identified bug and run your code again. If it now works as expected, you’ve finished debugging! If not, continue stepping through your code using step 2 until it does.

**DEBUGGING JAVASCRIPT CODE**

## **Debugging Review**

You just learned a lot of techniques for helping you get unstuck in all debugging situations. Congratulations! Let’s synthesize everything you learned into one debugging process.

1. **Is your code throwing errors?** If so, read the error stack trace for the type, description, and location of the error. Go to the error’s location and try to fix.
2. **Is your code broken but not throwing errors?** Walk through your code using `console.log()` statements. When unexpected results occur, isolate the bug and try to fix it.
3. **Did you locate the bug using steps 1 and 2, but can’t fix the bug?** Consult documentation to make sure you are using all JavaScript functionality properly. If you are still stuck, Google your issue and consult Stack Overflow for help. Read solutions or post your own Stack Overflow question if none exist on the topic.

---

**THE SCRIPT ELEMENT**

## **Review**

Let’s review.

- HTML creates the skeleton of a webpage, but JavaScript introduces interactivity
- The `<script>` element has an opening and closing tag. You can embed JavaScript code inbetween the opening and closing `<script>`tags.
- You link to external JavaScript files with the **src** attribute in the opening `<script>` tag.
- By default, scripts are loaded and executed as soon as the HTML parser encounters them in the HTML file, the HTML parser waits to load the entire script before from proceeding to parse the rest of the page elements.
- The `defer` attribute ensures that the entire HTML file has been parsed before the script is executed.
- The `async` attribute will allow the *HTML parser* to continue parsing as the script is being downloaded, but will execute immediately after it has been downloaded.

The old convention was to put scripts right before the `</body>` tag to prevent the script from blocking the rest of the HTML content. Now, the convention is to put the script tag in the `<head>`element and to use the `defer` and `async`attributes.

---

**THE DOCUMENT OBJECT MODEL**

## **What is the DOM?**

The *Document Object Model*, abbreviated DOM, is a powerful tree-like structure that allows programmers to conceptualize hierarchy and access the elements on a web page.

The DOM is one of the better-named acronyms in the field of Web Development. In fact, a useful way to understand what DOM does is by breaking down the acronym but out of order:

- The *DOM* is a logical tree-like **M**odel that organizes a web page’s HTML **D**ocument as an **O**bject.

The DOM is implemented by browsers to allow JavaScript to access, modify, and update the structure of an HTML web page in an organized way.

For this reason, we like to think of the DOM as the link between an HTML web page and scripting languages.

![Screen Shot 2023-08-10 at 12.03.41 PM.png](Day%2036%201d981d1e54cc4bffa09f47e012619226/Screen_Shot_2023-08-10_at_12.03.41_PM.png)

**THE DOCUMENT OBJECT MODEL**

## **Parent Child Relationships in the DOM**

Following the metaphor of a family tree, let’s define some key terminology in the DOM hierarchy:

A *parent node* is any node that is a direct ancestor of another node.

A *child node* is a direct descendant of another node, called the parent node.

Knowing these terms will allow you to understand and discuss the DOM as a tree-like structure. In fact, you will also see this terminology used when referring to the nesting structure of HTML code. Programmers refer to elements nested inside other elements as the children elements and parent elements respectively.

---

**THE DOCUMENT OBJECT MODEL**

## **Review**

Congratulations on completing our introduction to the Document Object Model, or DOM, as a structure!

Let’s review what you’ve learned so far:

- The DOM is a structural model of a web page that allows for scripting languages to access that page.
- The system of organization in the DOM mimics the nesting structure of an HTML document.
- Elements nested within another are referred to as the children of that element. The element they are nested within is called the parent element of those elements.
- The DOM also allows access to the attributes of an HTML element such as `style`, `id`, etc.

With this understanding, you can begin to leverage the power of scripting languages to create, update, and maintain web pages!

---

**JAVASCRIPT AND THE DOM**

## **Review**

In this lesson, you manipulated a webpage structure by leveraging the Document Object Model (DOM) interface in JavaScript.

Let’s review what we learned:

- The `document` keyword grants access to the root of the DOM in JavaScript.
- The DOM Interface allows you to select a specific element with CSS selectors by using the `.querySelector()` method.
- You can access an element directly by its ID with the `.getElementById()` method which returns a single element.
- You can access an array of elements with the `.getElementsByClassName()` and `.getElementsByTagName()` methods, then call a single element by referencing its placement in the array.
- The `.innerHTML` and `.style` properties allow you to modify an element by changing its contents or style respectively.
- You can create, append, and remove elements by using the `.createElement()`,`.appendChild()` and `.removeChild()` methods respectively.
- The `.onclick` property can add interactivity to a DOM element based on a click event.
- The `.children` property returns a list of an element’s children and the `.parentNode` property returns the element’s closest connected node in the direction towards the root.

---

**DOM EVENTS WITH JAVASCRIPT**

## **What is an Event?**

When you refresh your email inbox, double tap on a post, or scroll through a newsfeed — something cool happens in your browser. These actions are known as *events*!

Events on the web are user interactions and browser manipulations that you can program to trigger functionality. Some other examples of events are:

- A mouse clicking on a button
- Webpage files loading in the browser
- A user swiping right on an image

When a user does any of the above actions, they’re causing the event to be *fired* or be *triggered*. As in, “a click event fired when the button was clicked”. Being able to respond to these events makes your website interactive and therefore *dynamic*.

---

**DOM EVENTS WITH JAVASCRIPT**

## **Review**

Congrats, you completed the lesson! Now you’ve learned about JavaScript events and you can leverage these events on the DOM to create interactivity with event handlers.

Let’s review what you’ve learned:

- You can register events to DOM elements using the `addEventListener()` method.
- The `addEventListener()` method takes two arguments: an event type and an event handler function.
- When an event is triggered on the event target, the registered event handler function executes.
- Event handler functions can also be registered as values of `onevent` properties of their event target.
- Event object properties like `.target`, `.type`, and `.timeStamp` are used to provide information about the event.
- The `addEventListener()` method can be used to add multiple event handler functions to a single event.
- The `removeEventListener()` method stops specific event handlers from “listening” for specific events firing.

---

**INTRODUCTION TO FORM VALIDATION**

## **Introduction**

Modern websites require a lot of information to function as intended. Information like our usernames, passwords, “friends”, “likes”, credit card information, and shopping orders all have to be provided by users on the front-end and sent to the web applications’ servers so they can be processed. This information is used to create a personalized experience for the user.

User information is traditionally collected using HTML *forms*. If you’ve ever entered text in a website, selected from options on a list, or checked boxes and then hit enter or pressed a button, you likely filled out and submitted an HTML form!

In order for the data submitted through forms to be useful, it’s essential that the information is valid—if you were allowed to accidentally submit your last name where your address was expected, your package would never show up!

The process of checking that the information submitted through a form adheres to expectations is called *form validation*. In this lesson, we’ll explore the different techniques for validating form inputs.

**INTRODUCTION TO FORM VALIDATION**

## **Client-side Validation: JavaScript**

Client-side validation has two main advantages. First, it’s a better experience for the user to be alerted to problematic data immediately rather than having to wait for that information to come back from the server and have to fill out the form again. Second, catching mistakes earlier in the process saves the application time and resources as well. But not all issues can be handled with the built-in HTML validations.

In order to truly customize validation or to perform more complex validations, we can incorporate JavaScript form validations. We can do this by either writing the JavaScript ourselves or by incorporating a JavaScript library. If we have unique requirements for usernames on our site, for example, we’ll have to provide these systems of validation ourselves.

If we’re creating a relatively simple website, it makes sense to code the form validation ourselves or use a simple vanilla JavaScript library—[just-validate, for example](https://www.npmjs.com/package/just-validate). But most basic validation libraries will involve directly accessing or manipulating the DOM. This can get tricky when working with a framework that relies on a virtual DOM—like React or Vue. In those situations, it might be best to incorporate a library that works well with your specific framework. For example, the [formik library](https://www.npmjs.com/package/formik) is a lightweight library that simplifies validating forms in a React app.

---

**INTRODUCTION TO FORM VALIDATION**

## **Review**

In this lesson, we’ve explored form validation from many angles. Let’s review what we covered:

- Modern websites require a lot of information from their users and they collect a lot of this information through HTML forms.
- It’s essential to validate the data submitted through forms to keep websites secure and to make sure they function correctly.
- Regular expressions are sequences of characters that define patterns to look for in text. They are an important tool used in validating input.
- Modern HTML comes with useful built-in methods for form validation.
- Custom and complicated client-side validation can be accomplished with JavaScript.
- Asynchronous requests to the server can perform back-end validations before a form has been submitted.
- A final back-end validation of all data is required to ensure an application’s security and sanitize all data.

---

**HTML FORMS**

## **Review**

Nice work interacting with the extremely common and useful `<form>` element!

In this lesson we went over:

- The purpose of a `<form>` is to allow users to input information and send it.
- The `<form>`‘s `action` attribute determines where the form’s information goes.
- The `<form>`‘s `method` attribute determines how the information is sent and processed.
- To add fields for users to input information we use the `<input>` element and set the `type` attribute to a field of our choosing:
    - Setting `type` to `"text"` creates a single row field for text input.
    - Setting `type` to `"password"` creates a single row field that censors text input.
    - Setting `type` to `"number"` creates a single row field for number input.
    - Setting `type` to `"range"` creates a slider to select from a range of numbers.
    - Setting `type` to `"checkbox"` creates a single checkbox that can be paired with other checkboxes.
    - Setting `type` to `"radio"` creates a radio button that can be paired with other radio buttons.
    - Setting `type` to `"text"` and adding the `list`attribute will pair the `<input>` with a `<datalist>`element if the `list` of `<input>` and the `id` of `<datalist>` are the same.
    - Setting `type` to `"submit"` creates a submit button.
- A `<select>` element is populated with `<option>`elements and renders a dropdown list selection.
- A `<datalist>` element is populated with `<option>`elements and works with an `<input>` to search through choices.
- A `<textarea>` element is a text input field that has a customizable area.
- When a `<form>` is submitted, the `name` of the fields that accept input and the `value` of those fields are sent as `name=value` pairs.

Using the `<form>` element in conjunction with the other elements listed above allows us to create sites that take into consideration the wants and needs of our users. Take the opportunity to take what you’ve learned, and apply it!

---

**FORM VALIDATION**

## **Introduction to HTML Form Validation**

Ever wonder how a login page actually works? Or why the combination of a username and password grants you access to a website? The answers lie in *validation*. Validation is the concept of checking user provided data against the required data.

There are different types of validation. One type is *server-side validation*, this happens when data is sent to another machine (typically a server) for validation. An example of this type of validation is the usage of a login page. The form on the login page accepts username and password input, then sends the data to a server that checks that the pair matches up correctly.

On the other hand, we use *client-side validation* if we want to check the data on the browser (the client). This validation occurs before data is sent to the server. Different browsers implement client-side validation differently, but it leads to the same outcome.

Shared among the different browsers are the benefits of using HTML5’s built-in client-side validation. It saves us time from having to send information to the server and wait for the server to send back confirmation or rejection of the data. This can also help us protect our server from malicious code or data from a malicious user. It also allows us to quickly give feedback to users for specific fields rather than having them fill in a form again if the data they input into the form was rejected.

In this lesson, we’ll learn how to add some validation checks to our `<form>`s!

**FORM VALIDATION**

## **Review**

Awesome job adding client-side validation to `<form>`s!

Let’s quickly recap:

- Client-side validations happen in the browser before information is sent to a server.
- Adding the `required` attribute to an input related element will validate that the input field has information in it.
- Assigning a value to the `min` attribute of a number input element will validate an acceptable minimum value.
- Assigning a value to the `max` attribute of a number input element will validate an acceptable maximum value.
- Assigning a value to the `minlength` attribute of a text input element will validate an acceptable minimum number of characters.
- Assigning a value to the `maxlength` attribute of a text input element will validate an acceptable maximum number of characters.
- Assigning a regex to `pattern` matches the input to the provided regex.
- If validations on a `<form>` do not pass, the user gets a message explaining why and the `<form>` cannot be submitted.

---

**ACCESSIBILITY**

## **Introduction to Accessibility**

When designing a website, it is important to keep in mind that some users access the Internet in many different ways. For example, many users with a visual impairment use screen readers to access content on the Internet.

A screen reader is a piece of software that provides an audio description of a web page’s content. A screen reader not only reads the visual content out loud, it also reads out element names and other attributes that make it easier for visually impaired users to navigate a web page.

In the early days of the Internet, many pages were saturated with graphics and flash animations. Screen readers, unfortunately, could not interpret these types of elements. As such, a person with a visual impairment might not have been able to perceive important information on a website. For this reason, the [Web Accessibility Initiative](https://en.wikipedia.org/wiki/Web_Accessibility_Initiative) (led by W3C) developed standards for making information on the Internet accessible to all.

These standards fall under a group of guidelines called [ARIA](https://en.wikipedia.org/wiki/WAI-ARIA), or Accessible Rich Internet Applications. These guidelines are easily implemented and make web pages accessible to a broader audience. We’ll learn how to use ARIA roles and properties in this lesson to improve access for people who are visually impaired.

In this lesson, we will cover these practices:

1. Semantic Elements
2. ARIA Roles
3. ARIA Properties
4. `alt` Attributes

---

**ACCESSIBILITY**

## **ARIA Properties**

ARIA properties are attributes that you can add to HTML elements. These attributes provide additional information about elements that might not be obvious to users of screen readers. Let’s explore a property called `aria-label`.

```html
<img src="#" alt="A painting of the Shenandoah Valley"/>
<p>Armand Cabrera, 2010</p>

```

In the example above, a person looking at the web page would likely see “Armand Cabrera” below the image and use visual clues to infer that he is the artist. However, for someone using a screen reader it might not be clear what the paragraph below the image means. The property `aria-label` gives the screen reader additional information to read out loud to the user.

```html
<img src="#" alt="A painting of the Shenandoah Valley"/>
<p aria-label="Artist">Armand Cabrera, 2010</p>

```

In the improved HTML above, a user of a screen reader will know how this paragraph relates to the image above it.

Other ARIA properties are useful in more complex websites using HTML forms, JavaScript, and other advanced tools.

For a complete list of ARIA properties, visit the following resource:

- [ARIA Techniques](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques)

---

**ACCESSIBILITY**

## **Review: Accessibility**

Using ARIA roles and properties, `alt` attributes, and semantic elements in your HTML is a simple way to make your website accessible to visually-impaired Internet users.

1. Using semantic HTML elements whenever possible (such as `<header>` instead of `<div id="header">`) will allow screen reader users to navigate your website more efficiently.
2. The `role` attribute is used to communicate information about the role of specific elements.
3. `role="presentation"` allows a screen reader to skip markup elements that don’t directly contain useful information.
4. `aria-label` and other ARIA properties can be used to help users perceive information that is communicated visually but not through text.
5. The `alt` attribute should be added to every image element (and all other elements that support it) instead of `aria-label`. When used, its value should be a useful description of the image.

---

# **Review: Making a Website Accessible**

**In this unit, you learned about web accessibility (a11y) practices.**

Congratulations! The goal of this unit was to introduce you to website accessibility (a11y), why it is necessary and how to include it in your website design.

Having completed this unit, you are now able to:

- Understand what accessibility (a11y) means
- Understand the necessity for a11y on the web
- Add features for improved screen reader usage

If you are interested in learning more about these topics, here are some additional resources:

- Article: [What is a11y?](https://www.boia.org/blog/what-is-a11y)
- Resource: [The a11y Project Checklist](https://www.a11yproject.com/checklist/)
- Article: [CSS and JavaScript accessibility best practices](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript)

Learning is social. Whatever you’re working on, be sure to connect with the Codecademy community in the [forums](https://discuss.codecademy.com/). Remember to check in with the community regularly, including for things like asking for code reviews on your project work and providing code reviews to others in the [projects category](https://discuss.codecademy.com/c/project/1833), which can help to reinforce what you’ve learned.

---

# **Review: Git and GitHub, Part I**

**Review what you just learned in the Git and Github, Part I Unit.**

Congratulations! The goal of this unit was to introduce you to the Git versioning technology. Understanding Git is a crucial tool in your developer toolkit—but don’t worry if it didn’t stick! Practice is crucial with Git, which is why we introduced it early in the Path. You also now know how to take the repositories on your computer and put them online with GitHub. Having your work on Github will be important when you apply for jobs, and now you also know how to write a solid README.md with markdown.

Having completed this unit, you are now able to:

- Version control projects using Git
- Backtrack in Git
- Host a codebase online using GitHub repositories
- Use markdown to author a good README.md file

If you are interested in learning more about these topics, here are some additional resources:

- Documentation: [GitHub Docs](https://docs.github.com/en)
- Resource: [GitHub Cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf)
- Resource: [GitHub Learning Lab](https://github.com/apps/github-learning-lab)
- Resource: [Markdown and Visual Studio Code](https://code.visualstudio.com/docs/languages/markdown)
- Resource: [GitHub Guide to Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

Remember, you will put all of this knowledge into practice with an upcoming Portfolio Project. If you ever get stuck while working on the project, you can come back to this Unit and review what you have learned.

Learning is social. Whatever you’re working on, be sure to connect with the Codecademy community in the [forums](https://discuss.codecademy.com/). Remember to check in with the community regularly, including for things like asking for code reviews on your project work and providing code reviews to others in the [projects category](https://discuss.codecademy.com/c/project/1833), which can help to reinforce what you’ve learned.