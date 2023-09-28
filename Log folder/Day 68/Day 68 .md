# Day 68

Tags: React Native
Date: September 21, 2023
Status: Done

Task of the day

- Development Workflow
    - [Running on Device](https://reactnative.dev/docs/running-on-device)
    - Debugging
- [Building a React Native](https://www.youtube.com/watch?v=0-S5a0eXPoc) (2/2)

---

### Debugging

**In-App Developer Menu**

React Native provides an in-app developer menu which offers several debugging options. You can access the Dev Menu by shaking your device or via keyboard shortcuts:

- Android: `Cmd + M` or `Ctrl + M`
- iOS: `Cmd + D` or `Ctrl + D`

**Enabling fast refresh**

Fast Refresh is a React Native feature that allows you to get near-instant feedback while making changes in your code. It achieves this by reloading only the portion of the app that was changed, without losing the current state. This makes the development process a lot smoother as you don’t have to wait for the entire app to rebuild after making a change.

Learn more here

[Fast Refresh · React Native](https://reactnative.dev/docs/fast-refresh)

**LogBox**

LogBox is a new feature added to React Native to improve how logs are displayed and managed in your development environment. It provides better visualization and organization of logs, warnings, and errors, making it easier for developers to address issues in their code.

- **Better Error Formatting:** Errors are displayed in a more understandable format with clear syntax highlighting and relevant information regarding the error and the specific code that caused it.
- **Improved Warnings**: Warnings now come with filtering and sorting options, allowing you to control which warnings you want to prioritize or ignore during development.
- **Component Stacks**: Instead of displaying the raw call stack, LogBox provides a component stack that shows component hierarchy, allowing you to pinpoint the exact component causing the issue.
- **Customizable**: You can disable LogBox, customize its behavior, or even extend it with your own code to tailor your debugging experience.

**Sourcemaps**

Sourcemaps are files that map the original source code of a project to its minified or transpired version. This is especially useful in environments, like React Native, where the code may be transformed before being executed in the device/emulator. Sourcemaps help developers to debug their code more easily by mapping errors in the transformed code back to their original location in the source code.

- `eval`: Uses `eval` function to generate the sourcemaps. This is faster but provides less detailed information than other options.
- `cheap-source-map`: Simple line-to-line mapping without column information. Faster than `source-map` but less accurate.
- `cheap-module-source-map`: Similar to `cheap-source-map` but with support for modules.
- `source-map`: Full source mapping with both line and column information. It is accurate, though slower compared to other options.

After generating sourcemaps, you can use them to debug errors more efficiently, as they will reference the original locations in the source code. The browser’s developer tools, like Google Chrome, have built-in support for sourcemaps, providing the ability to navigate and debug errors with ease.

---

### Part 2 - React Native Tutorial for beginners

[https://www.youtube.com/watch?v=0-S5a0eXPoc](https://www.youtube.com/watch?v=0-S5a0eXPoc)