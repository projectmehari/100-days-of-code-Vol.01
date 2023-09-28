# Day 30

Tags: Front-end, HTML
Date: August 1, 2023
Status: Done

Tasks of the day

- Introduction of the fundamentals of CSS

---

### **Review of some fundamentals of CSS

Notes

The goal of this unit is to introduce you to CSS, one of the languages essential to developing websites. You will learn how to apply styles to HTML documents using CSS.

After this unit, you will be able to:

- Understand how CSS is used for web development
- Use CSS to add initial styling to your website
- Understand the Box Model in CSS
- Add positioning using CSS
- Read CSS documentation

![Screen Shot 2023-08-01 at 4.07.10 PM.png](Day%2030%20dcb67446985d4a9bbc04a1279b525a24/Screen_Shot_2023-08-01_at_4.07.10_PM.png)

---

## **Inline Styles**

Although CSS is a different language than HTML, it’s possible to write CSS code directly within HTML code using *inline styles*.

To style an HTML element, you can add the `style` attribute directly to the opening tag. After you add the attribute, you can set it equal to the CSS style(s) you’d like applied to that element.

```
<p style='color: red;'>I'm learning to code!</p>

```

The code in the example above demonstrates how to use inline styling. The paragraph element has a `style` attribute within its opening tag. Next, the `style` attribute is set equal to `color: red;`, which will set the color of the paragraph text to red within the browser.

If you’d like to add *more* than one style with inline styles, simply keep adding to the `style` attribute. Make sure to end the styles with a semicolon (`;`).

```
<p style='color: red; font-size: 20px;'>I'm learning to code!</p>

```

It’s important to know that inline styles are a quick way of directly styling an HTML element, but are rarely used when creating websites. But you may encounter circumstances where inline styling is necessary, so understanding how it works, and recognizing it in HTML code is good knowledge to have. Soon you’ll learn the proper way to add CSS code!

---

## **Review**

Great work so far! By understanding how to incorporate CSS code into your HTML file, as well as learning some of the key terms, you’re on your way to creating spectacular websites with HTML and CSS.

Let’s review what you learned so far:

- The basic anatomy of CSS syntax written for both inline styles and stylesheets.
- Some commonly used CSS terms, such as *ruleset*, *selector*, and *declaration*.
- CSS inline styles can be written inside the opening HTML tag using the `style` attribute.
- Inline styles can be used to style HTML, but it is not the best practice.
- An internal stylesheet is written using the `<style>` element inside the `<head>` element of an HTML file.
- Internal stylesheets can be used to style HTML but are also not best practice.
- An external stylesheet separates CSS code from HTML, by using the `.css` file extension.
- External stylesheets are the best approach when it comes to using HTML and CSS.
- External stylesheets are linked to HTML using the `<link>`element.

Take this knowledge to the next lesson, where you start learning how to select HTML elements to style!

Here are a few more resources to add to your toolkit:

- [Codecademy Docs: CSS](https://www.codecademy.com/resources/docs/css)
- [Codecademy Workspaces: CSS](https://www.codecademy.com/workspaces/new)

Make sure to bookmark these links so you have them at your disposal.

---

**SELECTORS**

## **Review**

Throughout this lesson, you learned how to select HTML elements with CSS and apply styles to them. Let’s review what you learned:

- CSS can select HTML elements by type, class, ID, and attribute.
- All elements can be selected using the universal selector.
- An element can have different states using the pseudo-class selector.
- Multiple CSS classes can be applied to one HTML element.
- Classes can be reusable, while IDs can only be used once.
- IDs are more specific than classes, and classes are more specific than type. That means IDs will override any styles from a class, and classes will override any styles from a type selector.
- Multiple selectors can be chained together to select an element. This raises the specificity but can be necessary.
- Nested elements can be selected by separating selectors with a space.
- Multiple unrelated selectors can receive the same styles by separating the selector names with commas.

---