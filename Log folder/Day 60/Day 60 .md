# Day 60

Tags: React
Date: September 12, 2023
Status: Done

Task of the day

- Composition
    - • **[Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)**
    - • **[How to perform component composition in React](https://www.robinwieruch.de/react-component-composition/)**
    - • **[Achieving Reusability With React Composition](https://formidable.com/blog/2021/react-composition/)**
- Basic Hooks
    - useState hook
        - • **[Using the State Hook](https://react.dev/reference/react/useState)**
        - • **[React useState Hook by Example](https://www.robinwieruch.de/react-usestate-hook/)**
    - useEffect
        - • **[Using the Effect Hook](https://react.dev/reference/react/useEffect)**
        - • **[React useEffect Hook by Example](https://www.robinwieruch.de/react-useeffect-hook/)**

---

# ****Composition vs Inheritance****

### Containment

Some components don’t know their children ahead of time. This is especially common for components like `Sidebar` or `Dialog` that represent generic “boxes”.

We recommend that such components use the special `children` prop to pass children elements directly into their output:

```jsx
function FancyBorder(props) {
  return (
    <div className={'FancyBorder FancyBorder-' + props.color}>
      {props.children}
    </div>
  );
}
```

### Specialization

Sometimes we think about components as being “special cases” of other components. For example, we might say that a `WelcomeDialog` is a special case of `Dialog`.

```jsx
function Dialog(props) {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        {props.title}
      </h1>
      <p className="Dialog-message">
        {props.message}
      </p>
    </FancyBorder>
  );
}

function WelcomeDialog() {
  return (
    <Dialog
      title="Welcome"
      message="Thank you for visiting our spacecraft!" />
  );
}
```

### So what about Inheritance?

At Facebook, we use React in thousands of components, and we haven’t found any use cases where we would recommend creating component inheritance hierarchies.

Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that component may accept arbitrary props, including primitive values, React elements, or functions.

If you want to reuse non-ui functionality between components, we suggest extracting it into JavaScript module. The components may import it and use that function, object, or class, without extending it.

---

### ****React JS Tutorial p.10 - Composition****

[https://www.youtube.com/watch?v=C63qybsY9Kc](https://www.youtube.com/watch?v=C63qybsY9Kc)

**React Component Composition**

There is one property (React Prop) that helps us out with this dilema for our React component: the React children prop. It’s one special prop provided by React to render something within a component whereas the component isn’t aware of it ahead of time. 

A basic example may be the following:

```jsx
const Button = ({ onClick, type = 'button', children }) => (
  <button type={type} onClick={onClick}>
    {children}
  </button>
);
```

The button element becomes a reusable button component whereas the Button component doesn’t know what it renders except for the button. Let’s use the children prop to our previous example to substitute our HTML form element with a Form component that renders all its inner content with React’s children prop:

```jsx
...

const UsernameForm = ({ onSubmit }) => {
  const [username, setUsername] = useState('');

  return (
    <Form
      onSubmit={event => {
        onSubmit(username);
        event.preventDefault();
      }}
    >
      <label>
        Your name:
        <input
          type="text"
          value={username}
          onChange={event => setUsername(event.target.value)}
        />
      </label>

      <button type="submit">Send</button>
    </Form>
  );
};

const Form = ({ onSubmit, children }) => (
  <form onSubmit={onSubmit}>{children}</form>
);

...
```

Let’s continue with this substitution for the other React elements before we can reap the fruits of having a composable React Form component. The Button component that has been shown before can be used to render our button element:

```jsx
...

const UsernameForm = ({ onSubmit }) => {
  const [username, setUsername] = useState('');

  return (
    <Form
      onSubmit={event => {
        onSubmit(username);
        event.preventDefault();
      }}
    >
      <label>
        Your name:
        <input
          type="text"
          value={username}
          onChange={event => setUsername(event.target.value)}
        />
      </label>

      <Button type="submit">Send</Button>
    </Form>
  );
};

const Form = ({ onSubmit, children }) => (
  <form onSubmit={onSubmit}>{children}</form>
);

const Button = ({ onClick, type = 'button', children }) => (
  <button type={type} onClick={onClick}>
    {children}
  </button>
);

...
```

Last but not least, the input field HTML element and its label. Let’s extract it to another reusable React component.

```jsx
const UsernameForm = ({ onSubmit }) => {
  const [username, setUsername] = useState('');

  return (
    <Form
      onSubmit={event => {
        onSubmit(username);
        event.preventDefault();
      }}
    >
      <InputField value={username} onChange={setUsername}>
        Your name:
      </InputField>

      <Button type="submit">Send</Button>
    </Form>
  );
};

const Form = ({ onSubmit, children }) => (
  <form onSubmit={onSubmit}>{children}</form>
);

const Button = ({ onClick, type = 'button', children }) => (
  <button type={type} onClick={onClick}>
    {children}
  </button>
);

const InputField = ({ value, onChange, children }) => (
  <label>
    {children}
    <input
      type="text"
      value={value}
      onChange={event => onChange(event.target.value)}
    />
  </label>
);
```

As you can see, the InputField component becomes generic/abstract while all props are passed to the component to specialize it. In addition, the component takes it one step further than the Form and Button components, because it offers a new kind of ‘HTML element” composition that encapsulates a label with an input field into a one component. It can be reused as such in our Form component but anywhere else too.

All three steps from before made our Form a composable React component. The Form renders the HTML form element, but everything within is rendered with React’s children. The same applies to the components in themselves, by just rendering anything that’s passed to them with the children property.

---

### Achieving reusability with React Composition

**What is React Composition?**

React Composition is a development pattern based on React’s original component model where we build component model where we build components from other components using explicit defined props or the implicit children prop.

In terms of refactoring, React composition is a pattern that can be used to break a complex component down to smaller components, and then composing those smaller components to structure and complete your application.

**Why use React composition?**

This technique prevents us from building too many similar components containing duplicate code and allows us to build fewer components that can be reused anywhere within our application, making them easier to understand and maintain for your team.

Accordion Component

```jsx
import React, { useState } from "react";

const Accordion = () => {
  const [expanded, setExpanded] = useState(false);

  const toggleExpanded = () => {
    setExpanded((prevExpanded) => !prevExpanded);
  };

  return (
    <div>
      <button onClick={toggleExpanded}>
        Header <span>{expanded ? "-" : "+"}</span>
      </button>
      {expanded && <div>Content</div>}
    </div>
  );
};

export default Accordion;
```

```jsx
import React from "react";
import Accordion from "./components/Accordion";

const App = () => {
  return <Accordion />;
};

export default App;
```

Editable Component

```jsx
import React, { useState } from "react";

const Editable = () => {
  const [editable, setEditable] = useState(false);
  const [inputValue, setInputValue] = useState("Title");

  const toggleEditable = () => {
    setEditable((prevEditable) => !prevEditable);
  };

  const handleInputChange = (e) => {
    setInputValue(e.target.value);
  };

  return (
    <div>
      {editable ? (
        <label htmlFor="title">
          Title:
          <input
            type="text"
            id="title"
            value={inputValue}
            onChange={handleInputChange}
          />
        </label>
      ) : (
        <>Title: {inputValue}</>
      )}
      <button onClick={toggleEditable}>{editable ? "Cancel" : "Edit"}</button>
    </div>
  );
};

export default Editable
```

```jsx
import React from "react";
import Editable from "./components/Editable";

const App = () => {
  return <Editable />;
};

export default App;
```

Let’s explore one similarity between these two components

**Problem:** Notice how both the Accordion component and the Editable component share the same functionality, where both are dependent on a boolean and a function to update that boolean — in other words, a toggle functionality. 

**Solution:** We can use a custom hook that will allow us to reuse this toggle logic in both components, and in any new component added in the future.

**Introducing Custom Hooks:** 

The purpose of creating a custom hook is to extract logic from a component and convert it into a reusable hook.

A reusable custom hook is used to avoid creating too many similar components that share the same logic. It also improves the code of your application by removing duplicate code, making your application easier to maintain. When introducing a new feature in your application, creating a custom hook prevents us from implementing that same new feature to each similarly built component. Instead, we can now reuse a custom hook.

Let’s create a custom hook named useToggle that returns a Status sate and a toggleStatus handler function:

```jsx
import { useState, useCallback, useMemo } from "react";

const useToggle = () => {
  const [status, setStatus] = useState(false);

  const toggleStatus = useCallback(() => {
    setStatus((prevStatus) => !prevStatus);
  }, []);

  const values = useMemo(
    () => ({
      status,
      toggleStatus
    }),
    [status, toggleStatus]
  );

  return values;
};

export default useToggle
```

The toggle logic implemented in useToggle is useful in the following scenarios:

- Hiding/displaying a component
- Collapsing/Expanding a component

We can now reuse our new custom hook as many times as needed in any component that will take advantage of using this shared logic.

**Refactoring Accordion component to use custom hook**

```jsx
import React from "react";
import useToggle from "./useToggle";

const Accordion = () => {
  const { status: expanded, toggleStatus: toggleExpanded } = useToggle();

  return (
    <div>
      <button onClick={toggleExpanded}>
        Header <span>{expanded ? "-" : "+"}</span>
      </button>
      {expanded && <div>Content</div>}
    </div>
  );
};

export default Accordion;
```

**Refactoring Editable component to use custom hook**

We can also refactor the editable component using the same useToggle custom hook:

```jsx
import React, { useState } from "react";
import useToggle from "./useToggle";

const Editable = () => {
  const { status: editable, toggleStatus: toggleEditable } = useToggle();
  const [inputValue, setInputValue] = useState("Title");

  const handleInputChange = (e) => {
    setInputValue(e.target.value);
  };

  return (
    <div>
      {editable ? (
        <label htmlFor="title">
          Title:
          <input
            type="text"
            id="title"
            value={inputValue}
            onChange={handleInputChange}
          />
        </label>
      ) : (
        <>Title: {inputValue}</>
      )}
      <button onClick={toggleEditable}>{editable ? "Cancel" : "Edit"}</button>
    </div>
  );
};

export default Editable;
```

Refactoring Accordion Component to use specialized and container components

Let’s examine how the header and content are displayed in our new Accordion to investigate another problem.

**Problem:** If we wanted to create different variations of the `Accordion`, e.g. `CarDetailsAccordion`, `CommentsAccordion`, `PaymentOptionsAccordion`, then we would have to write the same `button` element and `expanded && content` conditional in each component.

**Solution:** To avoid having duplicate boiler plate code when displaying the header and content of a variation of an `Accordion`, let's create specialized and container components.

**Specialized Components**

A specialized component is a component that is built from its accepted props to handle one specific case.

Let's create two new specialized components to handle displaying the header and the content of the `Accordion` component:

```jsx
import React from "react";

const AccordionHeader = ({ children, expanded, toggleExpanded }) => {
  return (
    <button onClick={toggleExpanded}>
      {children} <span>{expanded ? "-" : "+"}</span>
    </button>
  );
};

export default AccordionHeader;
```

```jsx
import React from "react";

const AccordionContent = ({ children, expanded }) => {
  return <>{expanded && children}</>;
};

export default AccordionContent;
```

**Container Components**

A container component, also known as a parent component, is a component that provides the state and behavior to its children components.

We can now refactor the `Accordion` component into a container component, and also include our two new specialized components `AccordionHeader` and `AccordionContent`:

```jsx
import React from "react";
import useToggle from "./useToggle";
import AccordionHeader from "./AccordionHeader";
import AccordionContent from "./AccordionContent";

const Accordion = ({ children, header }) => {
  const { status: expanded, toggleStatus: toggleExpanded } = useToggle();

  return (
    <div>
      <AccordionHeader expanded={expanded} toggleExpanded={toggleExpanded}>
        {header}
      </AccordionHeader>
      <AccordionContent expanded={expanded}>{children}</AccordionContent>
    </div>
  );
};

export default Accordion;
```

Notice how we are reusing the `AccordionHeader` and `AccordionContent` components, and this can also be applied to any new component that needs them.

This is how we will use our refactored `Accordion` component in our application:

```jsx
import React from "react";
import Accordion from "./components/Accordion";

const App = () => {
  return (
    <>
      <Accordion header="Accordion 1">
        <div>Content for Accordion 1</div>
      </Accordion>
      <Accordion header="Accordion 2">
        <div>Content for Accordion 2</div>
      </Accordion>
      <Accordion header="Accordion 3">
        <div>Content for Accordion 3</div>
      </Accordion>
    </>
  );
};

export default App;
```

Let's examine our `Accordion` component once again.

**Problem**: Notice how we are passing the `expanded={expanded}` prop to `AccordionHeader` and to `AccordionContent`. If we were to introduce a new specialized component that also needed the `expanded={expanded}` prop to be passed, we would also create additional duplicate code.

**Solution**: We can avoid repeating ourselves by using React's Context API, where we don't have to write and pass the same prop to all of the `Accordion`'s children components, deeply nested components, or newly added specialized components.

[Refactoring The Accordion Component To Use React's Context API](https://formidable.com/blog/2021/react-composition/#Refactoring-The-Accordion-Component-To-Use-React's-Context-API)

We'll use React's Context API to provide the `expanded` state and the `toggleExpanded` handler function to the entire `Accordion` component tree, making them available to all its children components and newly added children components. This also prevents us from having to *manually* pass down props when a new prop is introduced:

```jsx
import React, { createContext } from "react";
import useToggle from "./useToggle";
import AccordionHeader from "./AccordionHeader";
import AccordionContent from "./AccordionContent";

export const AccordionContext = createContext();
const { Provider } = AccordionContext;

const Accordion = ({ children, header }) => {
  const { status: expanded, toggleStatus: toggleExpanded } = useToggle();

  const value = {
    expanded,
    toggleExpanded
  };

  return (
    <Provider value={value}>
      <div>
        <AccordionHeader>{header}</AccordionHeader>
        <AccordionContent>{children}</AccordionContent>
      </div>
    </Provider>
  );
};

export default Accordion;
```

```jsx
import React, { useContext } from "react";
import { AccordionContext } from "./Accordion";

const AccordionHeader = ({ children }) => {
  const { expanded, toggleExpanded } = useContext(AccordionContext);

  return (
    <button onClick={toggleExpanded}>
      {children} <span>{expanded ? "-" : "+"}</span>
    </button>
  );
};

export default AccordionHeader;
```

```jsx
import React, { useContext } from "react";
import { AccordionContext } from "./Accordion";

const AccordionContent = ({ children }) => {
  const { expanded } = useContext(AccordionContext);

  return <>{expanded && children}</>;
};

export default AccordionContent;
```

Our newly refactored `Accordion` component does not affect how we reuse it within our application:

```jsx
import React from "react";
import Accordion from "./components/Accordion";

const App = () => {
  return (
    <>
      <Accordion header="Accordion 1">
        <div>Content for Accordion 1</div>
      </Accordion>
      <Accordion header="Accordion 2">
        <div>Content for Accordion 2</div>
      </Accordion>
      <Accordion header="Accordion 3">
        <div>Content for Accordion 3</div>
      </Accordion>
    </>
  );
};

export default App;
```

[Extending The Accordion Component](https://formidable.com/blog/2021/react-composition/#Extending-The-Accordion-Component)

Let's say our client would like us to update the `-` and `+` text that is toggled in our `AccordionHeader`. The client would like us to use icons instead. This can now be easily accomplished by introducing a new specialized `AccordionIcon` component:

```jsx
import React, { useContext } from "react";
import { AccordionContext } from "./Accordion";

const AccordionIcon = ({ opened = "-", closed = "+" }) => {
  const { expanded } = useContext(AccordionContext);

  return <span>{expanded ? opened : closed}</span>;
};

export default AccordionIcon;
```

And implement it in our `AccordionHeader` component:

```jsx
import React, { useContext } from "react";
import { AccordionContext } from "./Accordion";
import AccordionIcon from "./AccordionIcon";
import { FontAwesomeIcon } from "@fortawesome/react-fontawesome";
import { faAngleDown, faAngleUp } from "@fortawesome/free-solid-svg-icons";

const AccordionHeader = ({ children }) => {
  const { toggleExpanded } = useContext(AccordionContext);

  return (
    <button onClick={toggleExpanded}>
      {children} <AccordionIcon
        opened={<FontAwesomeIcon icon={faAngleUp} />}
        closed={<FontAwesomeIcon icon={faAngleDown} />}
      />
    </button>
  );
};

export default AccordionHeader;
```

## [Conclusion](https://formidable.com/blog/2021/react-composition/#Conclusion)

By prioritizing reusability from the beginning of our application, we can now easily extend the `Accordion` component with new features that our client would like us to implement, and increase our team's speed to deliver those new features. Thus, with the help of React composition, we can provide our teams with more reusable, readable, and extendable components.

Achieving reusability is no easy task, but as we continue to grow and learn with each and every application we build for our clients, we build the experience that is needed to succeed in our careers as software engineers.

---

### **How to useState in React**

[https://www.youtube.com/watch?v=4pO-HcG2igk](https://www.youtube.com/watch?v=4pO-HcG2igk)

Since [React Hooks](https://www.robinwieruch.de/react-hooks/) have been released, [function components](https://www.robinwieruch.de/react-function-component/) can use state and side effects. There are two hooks that are used for modern state management in React: useState and useReducer. This tutorial goes step by step through a useState example in React to get you started with this React Hook for state management.****

**Simple state in React**

In the past, state couldn't be used in function components. Hence they called them functional stateless components. However, with the release of React Hooks, state can be used in this kind of component too, and so they were rebranded by the React community to function components. A straightforward example on how to use state in a function component with the useState hook is demonstrated in the following example:``

```jsx
const App = () => {
  const [count, setCount] = React.useState(0);

  const handleIncrease = () => {
    setCount(count + 1);
  };

  const handleDecrease = () => {
    setCount(count - 1);
  };

  return (
    <div>
      Count: {count}
      <hr />
      <div>
        <button type="button" onClick={handleIncrease}>
          Increase
        </button>
        <button type="button" onClick={handleDecrease}>
          Decrease
        </button>
      </div>
    </div>
  );
};
```

The useState function takes as argument a value for the initial state. In this case, the count starts at 0. In addition, the hook returns an array of two values: `count` and `setCount`. It's up to you to name the two values, because they are [destructured from the returned array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) where renaming is allowed.

The first value, in this case `count`, represents the current state. The second value, in this case `setCount`, is a function to update the state with anything that's passed to this function when calling it. This function is also called the state update function. Every time this function is called, React re-renders the component to render the new state.

**Complex state in React**

So far, the example has only shown useState with a JavaScript primitive. That's where useState shines. It can be used for integers, booleans, strings, and also arrays. However, once you plan to manage more complex state with objects or more complex arrays, you should check out [React's useReducer hook](https://www.robinwieruch.de/react-usereducer-hook/). There are various scenarios where useReducer outperforms useState:

- complex state containers
- complex state transitions
- conditional state updates

It also helps to avoid multiple successive state updates by using only useState. You should definitely check it out if you want to manage more complex state in React.

**Asynchronous state in React**

What happens if you are dependent on actual state to update the state? Let's illustrate this case with an example where we are delaying the state update with a [JavaScript built-in setTimeout](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) function:``

```jsx
const App = () => {
  const [count, setCount] = React.useState(0);

  const handleIncrease = () => {
    setTimeout(() => setCount(count + 1), 1000);
  };

  const handleDecrease = () => {
    setTimeout(() => setCount(count - 1), 1000);
  };

  return (
    <div>
      Count: {count}
      <hr />
      <div>
        <button type="button" onClick={handleIncrease}>
          Increase
        </button>
        <button type="button" onClick={handleDecrease}>
          Decrease
        </button>
      </div>
    </div>
  );
};
```

React's useState is the go-to hook to manage state. It can be used [with useReducer and useContext](https://www.robinwieruch.de/react-state-usereducer-usestate-usecontext/) for modern state management in React. [Compared to useReducer, it is the more lightweight approach to manage state.](https://www.robinwieruch.de/react-usereducer-vs-usestate/)

---

**useEffect as a React hook**

[https://www.youtube.com/watch?v=0ZJgIjIuY7U](https://www.youtube.com/watch?v=0ZJgIjIuY7U)

---

### How to useEffect in React

In this tutorial you will learn everything about React's useEffect Hook. Let's say we have these two components whereas the parent component manages state with [React's useState Hook](https://www.robinwieruch.de/react-usestate-hook/) and its child component consumes the state and modifies the state with a [callback event handler](https://www.robinwieruch.de/react-event-handler/):``

```jsx
import * as React from 'react';

const App = () => {
  const [toggle, setToggle] = React.useState(true);

  const handleToggle = () => {
    setToggle(!toggle);
  };

  return <Toggler toggle={toggle} onToggle={handleToggle} />;
};

const Toggler = ({ toggle, onToggle }) => {
  return (
    <div>
      <button type="button" onClick={onToggle}>
        Toggle
      </button>

      {toggle && <div>Hello React</div>}
    </div>
  );
};

export default App;
```

Based on the stateful boolean flag coming from the parent component, the child component [renders "Hello React" conditionally](https://www.robinwieruch.de/conditional-rendering-react/). Now let's dive into React's useEffect Hook. Essentially useEffect runs a side-effect function whenever you want to run it. It can run only when the component mounts, when the component renders, or only when the component re-renders, and so on. We will go through various useEffect examples to demonstrate its usage.****

**React useEffect hook: update**

Previously you have learned about React's useEffect Hook's dependency array. This array can be used to run the side-effect function of useEffect only if a certain variable changes:
``

```jsx
const Toggler = ({ toggle, onToggle }) => {
  React.useEffect(() => {
    console.log('I run only if toggle changes (and on mount).');
  }, [toggle]);

  return (
    <div>
      <button type="button" onClick={onToggle}>
        Toggle
      </button>

      {toggle && <div>Hello React</div>}
    </div>
  );
};
```

Now the side-effect function for this React component **runs only when the variable in the dependency array changes**. However, note that the function runs also on the component's first render (mount). Anyhow, the dependency array can grow in size, because it's an array after all, so you can pass in more than one variable. Let's check this out with the following addition to our component:
``

```jsx
const Toggler = ({ toggle, onToggle }) => {
  const [title, setTitle] = React.useState('Hello React');
  React.useEffect(() => {
    console.log('I still run only if toggle changes (and on mount).');
  }, [toggle]);
  const handleChange = (event) => {
    setTitle(event.target.value);
  };
  return (
    <div>
      <inputtype="text"value={title}onChange={handleChange} />
      <buttontype="button"onClick={onToggle}>
        Toggle
      </button>
      {toggle && <div>{title}</div>}
    </div>
  );
};

```

However, in this case you could leave out the second argument -- the dependency array -- of useEffect entirely, because only these two variables trigger an update of this component, so by not having a second argument the side-effect would run on every re-render anyway.

There are various use cases for having React's useEffect run on an updated variable. For example, after updating the state, one might want to have a [callback function based on this state change](https://www.robinwieruch.de/react-usestate-callback/).