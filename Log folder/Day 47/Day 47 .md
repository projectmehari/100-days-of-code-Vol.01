# Day 47

Tags: css
Date: August 30, 2023
Status: Done

Task of the day

- CSS Methodologies
- CSS Preprocessors
- **Painting a Website—Ryan Scheuer**

---

### A look into some CSS methodologies

Object-Oriented CSS

Nicole Sullivan’s Object-Oriented CSS, or OOCSS for short, was launched in 2009. It was really the first CSS methodology to become widely adopted. It’s still hugely influential today. OOCSS advocates the separation of structure from skin.

The methodology makes a clear distinction between content and its containers. In OOCSS, style rules are written exclusively using CSS class selectors

**OOCSS Example**

- `.button` — provides the button’s basic structure
- `.grey-btn` — applies colors and other visual properties

**CSS**

```css
.button { box-sizing: border-box; height: 50px; width: 100%; }.grey-
```

One goal of the OOCSS methodology is to reduce duplication of the same properties throughout your various style rules. In other words, OOCSS can help us maintain DRY stylesheets. The methodology attempts to achieve this goal by using lots of small, modular, specialist CSS classes.

Very few style properties are applied via type selectors (e.g. `h1`, `div` and `body`).

**Block, Element, Modifier (BEM)**

Block, Element, Modifier - more commonly called BEM — is a CSS class-naming system devised by the dev team at Yandex (the google of Russia).

The idea behind BEM is to differentiate CSS classes that fulfill different roles. This is done by naming CSS classes in a way that indicates their role. BEM complements OOCSS because OOCSS doesn’t impose any particular class-naming convention.

In BEM terminology, a **block** is an independent, modular UI component. A block may be composed of multiple HTML elements, or even multiple blocks.  An example of a block might be your navigation menu or search form.

An **element** is a component of a block. An element serves a singular purpose. For example, if you have a navigation menu block, then elements of it might be your navigation menu’s links, which in turn might be in the form of list items (`li`elements) and links (`a` elements).

A **modifier** is a CSS class that changes the default presentation of a block or element. This is the BEM class-naming syntax:

- `.block`
- `.block--modifier`
- `.block__element`
- `.block__element--modifier`

# **BEM Example**

Here’s the markup above with BEM classes applied: **HTML**

```html
<formclass="loginform loginform--errors"> <labelclass="loginform__username loginform__username--error"> Username <input type="text" name="username" /> </label> <labelclass="loginform__password"> Password <input type="password" name="password" /> </label> <buttonclass="loginform__btn loginform__btn--inactive"> Sign in </button> </form>
```

The `.loginform` class is the block. The `.loginform` block is composed of three elements:

![Screen Shot 2023-08-30 at 3.56.14 PM.png](Day%2047%20b0b3b7cbbb044bab84578dfad16dec73/Screen_Shot_2023-08-30_at_3.56.14_PM.png)

![Screen Shot 2023-08-30 at 3.56.23 PM.png](Day%2047%20b0b3b7cbbb044bab84578dfad16dec73/Screen_Shot_2023-08-30_at_3.56.23_PM.png)

The BEM naming convention helps CSS authors comply with the OOCSS principle of using a flat selector hierarchy composed of equally-specific class selectors. It also helps OOCSS authors avoid deep descendant selectors.

**Scalable and Modular Architecture for CSS (SMACSS)**

Jonathan Snook published his book on *Scalable and Modular Architecture for CSS*in 2011. Abbreviated as SMACSS. Pronounced as “smacks”. A key idea in this CSS methodology is how we categorize our CSS style rules. Snook came up with five categories (Base,Layout, Modules, State, Themes)

**Suit CSS**

Nicholas Gallagher SUIT CSS introduced in 2014, is interesting because it combines a BEM-like class-naming system with a CSS preprocessor. So SUIT CSS provides us with extended CSS syntax a la Sass, Less or Stylus. SUIT CSS classes come in five formats:

- `u-utilityName`
- `ComponentName`
- `ComponentName--modifierName`
- `ComponentName-elementName`
- `ComponentName.is-stateOfName`

This class-naming convention highlights the division between:

- General utility classes
- Standalone/modular UI components
- Individual elements
- Modifiers

### Systematic CSS

Systematic CSS is a new CSS methodology which I developed and launched recently. Systematic CSS is based on a CSS-authoring system that I have fine-tuned over several years while working for various tech startups. Systematic CSS is how I personally compose web designs.

Systematic CSS shares many of the principles and ideas you can find in OOCSS, BEM, SMACSS, SUIT CSS, and other CSS methodologies. Systematic CSS is meant to be simpler alternative to existing CSS methodologies: There are fewer naming-conventions to remember, and the class-naming convention is intended to be more intuitive. In the Systematic CSS methodology, the process of developing a new web design is broken up into four phases:

1. Layout
2. Elements
3. Widgets
4. Modifiers

### Conclusion

All CSS methodologies tackle the scalability and maintainability problem in CSS by providing a class-based system for breaking up big web designs into lots of small, modular, discrete units. Each UI module can be reused over and over throughout a design, and even ported from one project to another if two projects share the same CSS methodology.

In the process, CSS methodologies do much more than fix the CSS scalability problem. They make it easier to develop and iterate a design. They make front-end code easier to read and understand, provide ready-made documentation, and make it easier for multiple people to collaborate on a design.

Adopting a CSS methodology can reduce the learning curve for new designers joining a project, and make for a smoother transition when a project is handed over to a new team. And because CSS methodologies encourage reuse of existing code, they enforce consistency in visual designs and reduce page size and increase page rendering speed. CSS methodologies have different class-naming conventions and they carve up web designs along slightly different lines.

But the specifics of any particular methodology are less important than the general solutions they provide for modularizing front-end code and making CSS easier to scale. You can take away the ideas and develop your own categories of classes and devise your own class-naming conventions that work best for you. That’s what I do.

Systematic CSS is my starting point, but every project is different, and I always tweak and extend my CSS methodology to better fit the skill set and creative temperament of the team I’m working with.

---

### ****CSS Preprocessors Explained****

CSS Preprocessors compile the code which is written using a special compiler. They then use that to create a CSS file, which can then be referenced by the main HTML document.

When using any CSS Preprocessor, you will able to program in normal CSS just as you would if the preprocessor were not in place.  

### Variables

One of the most commonly used item in any programming language is the variable, something which CSS notably lacks. By having variables at your disposal, you may define a value once, and reuse if throughout the entire program. An example of this in SASS would be:

```html
$yourcolor: #000056
.yourDiv {
  color: $yourcolor;
 }
```

### **Loops**

Another common item in languages are loops, something else CSS lacks. Loops can be used to repeat the same instructions multiple times without having to be reentered multiple times. An example with SASS would be:

```sass
@for $vfoo 35px to 85px {
  .margin-#{vfoo} {
    margin: $vfoo 10px;
   }
 }
```

This loop saves us from having the to write the same code multiple times to change the margin size.

### **If/Else Statements**

Yet another feature which CSS lacks are If/Else statements. These will run a set of instructions only if a given condition is true. An example of this in SASS would be:

```sass
@if width(body) > 500px {
  background color: blue;
 } else {
  background color: white;
 }
```

---

### **5 Reasons to use a CSS Preprocessor**

1. **It will make your code easier to maintain** You will be able to create variables, mixins and functions that are declared at the beginning of the document which will make simple changes, like a color, easier to maintain.
2. **It will make your CSS DRY** DRY as in *Don’t repeat yourself* (as opposed to WET, *Write everything twice*). Don’t repeat yourself is a main principle of computer programming.
3. **It will make your CSS more organized** Both Sass and LESS support nested definitions. This is an excellent feature and keeps things organized. After you start writing your css definitions this way, you will realize how repetitive the old way was.
4. **It will save you time**
5. **It’s fun**

---

### ****Painting a Website—Ryan Scheuer****

[https://www.youtube.com/watch?v=YC6xRnQ8L6c&t=1461s](https://www.youtube.com/watch?v=YC6xRnQ8L6c&t=1461s)

bugs

- couldn’t compile Sass to css style