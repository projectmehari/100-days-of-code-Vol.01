# Day 90

Tags: React
Date: October 27, 2023
Status: Done

Tasks of the day

- Component Lifecycle
- Learning p5.js
- Animation with p5.js

---

### The Component lifecycle

The component lifecycle has three-high level parts:

1. *Mounting,* when the component is being initialized and put into the DOM for the first time
2. *Updating*, when the component updates as a result of changed state or changed props
3. *Unmounting*, when the component is being removed from the DOM

![Screen Shot 2023-10-27 at 1.00.19 PM.png](Day%2090%20fd34f109174d4a5f93e627ba31d5a9bd/Screen_Shot_2023-10-27_at_1.00.19_PM.png)

Every React component you’ve ever interacted with does the first step at a minimum. If a component never mounted, you’d never see it!

Most interesting components are *updated* at some point. A purely static component—like, for example, a logo—might not ever update. But if a component’s state changes, it updates. Or if different props are passed to a component, it updates.

Finally, a component is *unmounted* when it’s removed from the DOM. For example, if you have a button that hides a component, chances are that component will be unmounted. If your app has multiple screens, it’s likely that each screen (and all of its child components) will be unmounted. If a component is “alive” for the entire lifetime of your app (say, a top-level `<App />`component or a persistent navigation bar), it won’t be unmounted. But most components can get unmounted one way or another!

---

### Review

1. *Mounting*, when the component is being initialized and put into the DOM for the first time. We saw that the `constructor`, `render()`, and `componentDidMount()` are called during this phase.
2. *Updating*, when the component updates as a result of changed state or changed props. We saw that `render()` and `componentDidUpdate()`are called during this phase.
3. *Unmounting*, when the component is being removed from the DOM. We saw that `componentWillUnmount()`was called here, which was a good time to clean things up.

---

### What is p5.js

[p5.js](https://p5js.org/) is an [open-source](https://en.wikipedia.org/wiki/Open-source_software) JavaScript library for creative coding. A collection of pre-written code, it provides us with tools that simplify the process of creating interactive visuals with code in the web browser.

p5.js was developed by the artist and programmer [Lauren McCarthy](https://lauren-mccarthy.com/) with support from the [Processing Foundation](https://processingfoundation.org/). It was inspired by [Processing](https://processing.org/), a flexible software sketchbook created by  [Casey Reas](http://reas.com/) and [Ben Fry](https://benfry.com/) that allows users to program visualizations using the Java programming language. p5.js was created as a version of Processing for the web. First released in 2014, it has since grown in popularity as a tool that makes programming accessible for artists, designers, educators, beginners, and anyone else!

### Anatomy of a p5.js

Before diving into code, let’s take a look at the web technologies that p5.js uses. If you are relatively new to web programming, remember that web applications typically require three types of files: HTML, CSS, and JavaScript. The same applies to a p5.js program! Here are lists of roles that each of these components plays to render a p5.js sketch.

**HTML**

- HTML is used for the content of a web page.
- The HTML file is where you can view the output of your p5.js program in the browser.
- You’ll also have to link your p5.js sketch file and the p5.js library as `<script>` tags.

**CSS:**

- CSS stylesheets are used to style HTML elements.
- p5.js will create an HTML `<canvas>` element that you can style using CSS. We will talk more about the `<canvas>` element in the next exercise.

**JavaScript:**

- JavaScript is used for adding functionality to a web application.
- A JavaScript file, typically named **sketch.js**, will contain the code for your p5.js application.
- p5.js is a JavaScript library that contains built-in variables and functions to help you develop visual programs.

---

### Review

The p5.js library has many built-in functions to draw 2D shapes to the canvas:

- `point()` and `line()`
- `rect()` and `square()`
- `ellipse()` and `circle()`
- `triangle()` and `quad()`

There are style functions that must be called before drawing shapes:

- `background()`
- `fill()`
- `stroke()`
- `strokeWeight()`

- p5.js allows for many ways to specify color:
    - gray value (0 - 255)
    - RGB values (0 - 255)
    - Named CSS color (like `'purple'` and `'yellow'`)
    - 3 or 6 digit hexadecimal values (like `'#FE0'` and `'#1557FF'`)
- `for` loops make it easy to draw many shapes at once.

---

### **Frames**

In p5.js, multiple frames can easily be shown in a sequence using the `draw()` loop. By default, any code in the `draw()`function will repeat over and over again, many times per second. This function’s endless repetition is ideal for making an animation because we can write code in the `draw()` function that slightly alters our image each time it runs.

### **FPS**

*Frames Per Second* (FPS) specifies the number of frames displayed every second. When the FPS of animation is lower, it looks like it is in slow motion. When the frame rate is higher, the animation looks like it is being fast-forwarded.

p5.js will automatically run your code at 60 frames per second. However, you can manipulate the FPS by using the `frameRate()`function, which will change the number of frames shown per second to the number specified as the function’s argument. For example, the code snippet below will cause the `draw()` function to run `numberOfFrames` times per second.