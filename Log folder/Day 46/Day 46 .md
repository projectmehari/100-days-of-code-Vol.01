# Day 46

Tags: Tailwind, css
Date: August 29, 2023
Status: Done

Task of the day 

- Tailwind CSS crash course

---

[https://www.youtube.com/watch?v=UBOj6rqRUME](https://www.youtube.com/watch?v=UBOj6rqRUME)

**A utility-first CSS framework for rapidly building custom designs.**

- Tailwind CSS is a highly customizable, low-level CSS framework that gives you all of the building blocks you need to build bespoke designs without any annoying opinionated styles you have to fight to override.

**Installation** 

1) Install **`tailwindcss`** via npm, and create your **`tailwind.config.js`** file.

```jsx
npm install -D tailwindcss
npx tailwindcss init
```

**Configure your template paths**

2) Add the paths to all of your template files in your **`tailwind.config.js`** file.

```css
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ["./src/**/*.{html,js}"],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

**Add the tailwind directives to your CSS**

3) Add the **`@tailwind`** directives for each of Tailwind’s layers to your main CSS file.

```css
@tailwind base;
@tailwind components;
@tailwind utilities;
```

****Start the Tailwind CLI build process****

4) Run the CLI tool to scan your template files for classes and build your CSS.

```css
<!doctype html>
<html>
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link href="/dist/output.css" rel="stylesheet">
</head>
<body>
  <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
</body>
</html>
```

---

[https://www.youtube.com/watch?v=8eQwgc9nc64](https://www.youtube.com/watch?v=8eQwgc9nc64)