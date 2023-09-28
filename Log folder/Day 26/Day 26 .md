# Day 26

Tags: A-Frame, Javascript
Date: December 19, 2022
Status: Done

Tasks of the day

- ****[Creative Summit | The sound of on-chain music - Web3 and NFT music Metadata](https://www.youtube.com/watch?v=qq6E65_Dwe4&list=PLXzKMXK2aHh4ReviSGoUdlMYSsc1iRfAm&index=34)****

---

### **Creative coding - Chapter 1**

Adding two.js to a project

- [Two.js.org](http://Two.js.org)
- Two.js is a two-dimensional drawing api geared towards modern web browsers. It is renderer agnostic enabling the same api to draw in multiple contexts: svg, canvas, and webgl

**[Basic Usage](https://two.js.org/#basic-usage)**

In order to start any of these demos you'll want to **[download](https://two.js.org/#download)**
 two.js and add it to your HTML document. Once downloaded add this tag to the `<head>`
 of your document: `<script src="./path-to-two/two.js"></script>`
. When you visit the page, you should be able to open up the console and type `Two`
. If this returns a function (and not an error) then you're ready to begin!

### **[Drawing Your First Shapes](https://two.js.org/#drawing-your-first-shapes)**

Before we get into all the fancy animating it's good to get a feel for how to make shapes in two.js. In order to do this we need to have an instance of two. This sets up a dom element that contains either an svg or canvas element to add to the webpage. The two object has a scene which holds all shapes as well as methods for creating shapes.

```jsx
`// Make an instance of two and place it on the page.
var params = { fullscreen: true };
var elem = document.body;
var two = new Two(params).appendTo(elem);`

`// Two.js has convenient methods to make shapes and insert them into the scene.
var radius = 50;
var x = two.width * 0.5;
var y = two.height * 0.5 - radius * 1.25;
var circle = two.makeCircle(x, y, radius);`

`y = two.height * 0.5 + radius * 1.25;
var width = 100;
var height = 100;
var rect = two.makeRectangle(x, y, width, height);`

`// The object returned has many stylable properties:
circle.fill = '#FF8000';
// And accepts all valid CSS color:
circle.stroke = 'orangered';
circle.linewidth = 5;`

`rect.fill = 'rgb(0, 200, 255)';
rect.opacity = 0.75;
rect.noStroke();`

`// Don’t forget to tell two to draw everything to the screen
two.update();`
```

### **[Shapes and Groups](https://two.js.org/#shapes-and-groups)**

Adding shapes to groups makes managing multiple shapes easier and more sane. Group's provide an easy way to move your content through `position`, `rotation`, and `scale`. These operations emit from the coordinate space `(0, 0)`. In the example below we can see that the initial orientation of the circle and rectangle changed from the first example. These shapes are oriented around `(0, 0)`, which allows us to transform the group around the centeroid of the shapes. In addition Group's styling operations trickle down and apply to each shape.

```jsx
var params = { fullscreen: true }
var elem = document.body;
var two = new Two(params).appendTo(elem);
 
var circle = two.makeCircle(-70, 0, 50);
var rect = two.makeRectangle(70, 0, 100, 100);
circle.fill = '#FF8000';
circle.stroke = 'orangered';
rect.fill = 'rgba(0, 200, 255, 0.75)';
rect.stroke = '#1C75BC';
 
// Groups can take an array of shapes and/or groups.
var group = two.makeGroup(circle, rect);
 
// And have position, rotation, scale like all shapes.
group.position.set(two.width / 2, two.height / 2);
group.rotation = Math.PI;
group.scale = 0.75;
 
// You can also set the same properties a shape have.
group.linewidth = 7;
 
two.update();
```

### **[Adding Motion](https://two.js.org/#adding-motion)**

Finally, let's add some motion to our shapes. So far the examples use `two.update();` to draw content to the screen. The instance of two.js has two particular methods for animation. The first is `two.play();` which calls `two.update();` at 60 frames-per-second. This rate, however, will slowdown if there's too much content to render per frame.

The second method is `two.bind();` This method takes a string as its first parameter indicating what event to listen to and a function as its second argument delineating what to do when the event described in the first parameter happens. To sync a function with the animation loop simply invoke `two.bind('update', referenceToFunction);` as outlined below:

```jsx
var params = { fullscreen: true };
var elem = document.body;
var two = new Two(params).appendTo(elem);
 
var circle = two.makeCircle(-70, 0, 50);
var rect = two.makeRectangle(70, 0, 100, 100);
circle.fill = '#FF8000';
rect.fill = 'rgba(0, 200, 255, 0.75)';
 
var cx = two.width * 0.5;
var cy = two.height * 0.5;
var group = two.makeGroup(circle, rect);
group.position.set(cx, cy);
group.scale = 0;
group.noStroke();
 
// Bind a function to scale and rotate the group to the animation loop.
two.bind('update', update);
// Finally, start the animation loop
two.play();
 
function update(frameCount) {
// This code is called every time two.update() is called.
if (group.scale > 0.9999) {
group.scale = group.rotation = 0;
}
var t = (1 - group.scale) * 0.125;
group.scale += t;
group.rotation += t * 4 * Math.PI;
}
```

### **Next Steps**

Now that you got a quick glimpse into some of the functionality two.js offers, check out the **[official](https://two.js.org/examples/#official-examples)** and **[community](https://two.js.org/examples/#community-examples)** examples to see what else you can do. These examples range from showing off specific features of the library to using the library in other environments, like **[React](https://two.js.org/examples/#react)** and **[Angular](https://two.js.org/examples/#angular)**.

Looking for more information on a specific property? Then head over to the **[documentation](https://two.js.org/docs/two/)** which outlines all of the library's public features.

Haven't found what you're looking for? Then ask a question on our **[GitHub page.](https://github.com/jonobr1/two.js/issues/new?assignees=&labels=question&template=question.md&title=%5BQuestion%5D)**

---

Notes

**The sound of on-chain music - Web3 and NFT music metadata**

![Screen Shot 2022-12-16 at 5.36.28 PM.png](Day%2026%20ef715963d2814ca6af4b9c3848351372/Screen_Shot_2022-12-16_at_5.36.28_PM.png)

**Host**

Brooke Jackson - (Water & Music)

**Panelists**

- AJ Washington (Phlote)
- Ahmed Mutahadir (UVR Citizen developer group)
- Kyle Dhillon (Arpeggi Labs)
- Kyle Smith (LexDAO) - Lawyers & Developers

The question of metadata in the music industry

What are the current problems?

- Education about metadata and it usage within different platforms ( web2 vs web3? - Ahmed
    - Major publication platforms aren’t adopting the metadata standard
    - You should be given the option to be able to populated that data
- How do alleviated the technical barriers from artists? and how do this in a decentralized way? - AJ
- Neue ? (music metadata aggregators) - Kyle D
- A UX where the signature is easy to identify by the user - Kyle S
    - Kernel community?
- API standards - Kyle S
- CCO ( SongaDay POV on this?)

How can we solve them?

- Leading with example by building projects that showcase transparency with the data - Ahmed

How can we can connect stakeholders