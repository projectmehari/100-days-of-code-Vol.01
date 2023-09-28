# Day 31

Tags: Front-end, css
Date: August 2, 2023
Status: Done

Tasks of the day

- Introduction of the fundamentals of CSS (Cont)

---

**review of front-end* 

## **Review Visual Rules**

Incredible work! You used CSS to alter text and images on a website. Throughout this lesson, you learned concepts including:

- The `font-family` property defines the typeface of an element.
- `font-size` controls the size of text displayed.
- `font-weight` defines how thin or thick text is displayed.
- The `text-align` property places text in the left, right, or center of its parent container.
- Text can have two different color attributes: `color` and `background-color`. `color` defines the color of the text, while `background-color` defines the color behind the text.
- CSS can make an element transparent with the `opacity`property.
- CSS can also set the background of an element to an image with the `background-image` property.
- The `!important` flag will override any style, however it should almost never be used, as it is extremely difficult to override.

---

**THE BOX MODEL**

## **Review**

In this lesson, we covered the four properties of the box model: height and width, padding, borders, and margins. Understanding the box model is an important step towards learning more advanced HTML and CSS topics. Let’s take a minute to review what you learned:

- The box model comprises a set of properties used to create space around and between HTML elements.
- The height and width of a content area can be set in pixels or percentages.
- Borders surround the content area and padding of an element. The color, style, and thickness of a border can be set with CSS properties.
- Padding is the space between the content area and the border. It can be set in pixels or percent.
- Margin is the amount of spacing outside of an element’s border.
- Horizontal margins add, so the total space between the borders of adjacent elements is equal to the sum of the right margin of one element and the left margin of the adjacent element.
- Vertical margins collapse, so the space between vertically adjacent elements is equal to the larger margin.
- `margin: 0 auto` horizontally centers an element inside of its parent content area, if it has a width.
- The `overflow` property can be set to `display`, `hidden`, or `scroll`, and dictates how HTML will render content that overflows its parent’s content area.
- The `visibility` property can hide or show elements.

---

**CHANGING THE BOX MODEL**

## **Review: Changing the Box Model**

In this lesson, you learned about an important limitation of the default box model: box dimensions are affected by border thickness and padding.

Let’s review what you learned:

1. In the default box model, box dimensions are affected by border thickness and padding.
2. The `box-sizing` property controls the box model used by the browser.
3. The default value of the `box-sizing` property is `content-box`.
4. The value for the new box model is `border-box`.
5. The `border-box` model is not affected by border thickness or padding.

---

**DISPLAY AND POSITIONING**

## **Flow of HTML**

A browser will render the elements of an HTML document that has no CSS from left to right, top to bottom, in the same order as they exist in the document. This is called the *flow* of elements in HTML.

In addition to the properties that it provides to style HTML elements, CSS includes properties that change how a browser *positions*elements. These properties specify where an element is located on a page, if the element can share lines with other elements, and other related attributes.

In this lesson, you will learn five properties for adjusting the position of HTML elements in the browser:

- `position`
- `display`
- `z-index`
- `float`
- `clear`

Each of these properties will allow us to position and view elements on a web page. They can be used in conjunction with any other styling properties you may know.

---

**DISPLAY AND POSITIONING**

## **Review: Layout**

Great job! In this lesson, you learned how to control the positioning of elements on a web page.

Let’s review what you’ve learned so far:

- The `position` property allows you to specify the position of an element.
- When set to `relative`, an element’s position is relative to its default position on the page.
- When set to `absolute`, an element’s position is relative to its closest positioned parent element. It can be pinned to any part of the web page, but the element will still move with the rest of the document when the page is scrolled.
- When set to `fixed`, an element’s position can be pinned to any part of the web page. The element will remain in view no matter what.
- When set to `sticky`, an element can stick to a defined offset position when the user scrolls its parent container.
- The `z-index` of an element specifies how far back or how far forward an element appears on the page when it overlaps other elements.
- The `display` property allows you to control how an element flows vertically and horizontally in a document.
- `inline` elements take up as little space as possible, and they cannot have manually adjusted `width` or `height`.
- `block` elements take up the width of their container and can have manually adjusted `height`s.
- `inline-block` elements can have set `width` and `height`, but they can also appear next to each other and do not take up their entire container width.
- The `float` property can move elements as far left or as far right as possible on a web page.
- You can clear an element’s left or right side (or both) using the `clear` property.

When combined with an understanding of the box model, positioning can create visually appealing web pages. So far, we’ve focused on adding content in the form of text to a web page. In the next unit, you’ll learn how to add and manipulate images to a web page.