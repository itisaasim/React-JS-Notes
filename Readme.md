# React JS Notes

Content

### 🟢 **Beginner Level**

> Focus: Syntax, components, JSX, props, state, basic hooks
> 
1. **What is React?**
2. **JSX**
3. **Components (Function & Class)**
4. **Props**
5. **State (`useState`)**
6. **Event Handling**
7. **Conditional Rendering**
8. **Lists & Keys**
9. **Controlled vs Uncontrolled Components**
10. **Forms & Inputs**
11. **Basic Styling (inline, CSS modules)**
12. **Basic `useEffect` for side effects**

---

### 🟡 **Intermediate Level**

> Focus: Component logic, performance, reusability, real-world data handling
> 
1. **useEffect Deep Dive (cleanup, dependencies)**
2. **Custom Hooks**
3. **useRef**
4. **useContext (Context API)**
5. **Prop Drilling vs Lifting State Up**
6. **Component Composition vs Inheritance**
7. **React Router (v6+)**
8. **Fetching Data (with fetch/axios)**
9. **Error Boundaries**
10. **useReducer (vs useState)**
11. **React Memoization: `React.memo`, `useMemo`, `useCallback`**
12. **Forms with Libraries (Formik / React Hook Form)**
13. **Performance Optimization Basics**

---

### 🔴 **Advanced Level**

> Focus: Architecture, performance, testing, advanced patterns
> 
1. **Code Splitting & Lazy Loading (`React.lazy`, `Suspense`)**
2. **Error Handling with Suspense (future)**
3. **Concurrent Features (StartTransition, useDeferredValue)**
4. **Testing React (Jest, React Testing Library)**
5. **Higher-Order Components (HOCs)**
6. **Render Props Pattern**
7. **Compound Components**
8. **Controlled vs Uncontrolled Components (Deep Dive)**
9. **Accessibility in React**
10. **React Portals**
11. **useImperativeHandle with `forwardRef`**
12. **Server-Side Rendering (Next.js)**
13. **Static Site Generation (Next.js)**
14. **React DevTools & Debugging**
15. **State Management Libraries (Redux, Zustand, Recoil)**
16. **React Query / TanStack Query (data caching)**
17. **React with TypeScript (basic to advanced)**
18. **Design Patterns in React (Container/Presentational, Hooks-based)**
19. **Monorepo & Component Libraries (Storybook, Bit.dev)**
20. **React Native (intro)**
21. **React Architecture (folders, services, domain separation)**

# 🧠 What is React?

React is a **JavaScript library** for building user interfaces. It allows you to build **reusable components** and manage **state and rendering** efficiently using a **declarative** and **component-based** approach.

---

## 🔤 Syntax

```jsx
jsx
CopyEdit
import React from 'react';
import ReactDOM from 'react-dom/client';

function App() {
  return <h1>Hello, world!</h1>;
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
import React from 'react';
import ReactDOM from 'react-dom/client';

function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Alice" />
      <Welcome name="Bob" />
    </div>
  );
}

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);

```

---

## ✅ What to do with it

- Break the UI into **reusable components**.
- Use **JSX** to express UI declaratively.
- **Manage state** using hooks like `useState`.
- Think of your UI as a function of state.

---

## ❌ What not to do with it

- ❗ Avoid directly manipulating the DOM (use state-driven rendering).
- ❗ Don’t use class components unless absolutely necessary (prefer functional components + hooks).
- ❗ Don’t mix logic and UI messily — keep components focused and clean.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Quick Start
- Fullstackopen.com – Part 1: Introduction to React
- EpicReact.dev by Kent C. Dodds – React Fundamentals

# 🔤 JSX

JSX stands for **JavaScript XML**. It is a **syntax extension** for JavaScript that looks similar to HTML and is used with React to describe what the UI should look like. JSX makes your code more readable and expressive by letting you write HTML-like structures directly in JavaScript.

---

## 🔧 Syntax

```jsx
jsx
CopyEdit
const element = <h1>Hello, world!</h1>;

```

JSX expressions can contain JavaScript using `{}`:

```jsx
jsx
CopyEdit
const name = 'Alice';
const greeting = <h1>Hello, {name}!</h1>;

```

JSX must return a **single parent element**:

```jsx
jsx
CopyEdit
return (
  <div>
    <h1>Hello</h1>
    <p>Welcome!</p>
  </div>
);

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
import React from 'react';

function Greeting({ name }) {
  const isLoggedIn = true;

  return (
    <div>
      <h1>Hello, {name}!</h1>
      <p>{isLoggedIn ? 'Welcome back!' : 'Please log in.'}</p>
    </div>
  );
}

```

---

## ✅ What to do with it

- Wrap multiple elements in a single parent (like `<div>` or `<>...</>`).
- Use `{}` to insert variables or expressions.
- Use `className` instead of `class` for CSS classes.
- Use `htmlFor` instead of `for` for `<label>` elements.

---

## ❌ What not to do with it

- ❗ Don’t forget to close all tags (even self-closing ones like `<img />`).
- ❗ Don’t try to return multiple elements without wrapping them.
- ❗ Don’t use `if` statements directly inside JSX — use ternary expressions or logical `&&`.

---

## 📚 If you want to learn more

- React Docs (react.dev) – JSX
- Fullstackopen.com – Part 1: JavaScript XML (JSX)
- EpicReact.dev by Kent C. Dodds – JSX Module

# 🧩 Components (Function & Class)

In React, **components** are the building blocks of the UI. They are **JavaScript functions** or **classes** that return JSX. Components allow you to break down complex UIs into reusable, isolated pieces.

There are **two types** of components:

- **Function Components** – the modern standard, often used with hooks.
- **Class Components** – older style, used before hooks were introduced.

---

## 🔧 Syntax

### ✅ Function Component

```jsx
jsx
CopyEdit
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

```

### ✅ Arrow Function Variant

```jsx
jsx
CopyEdit
const Welcome = ({ name }) => <h1>Hello, {name}</h1>;

```

### 🧱 Class Component

```jsx
jsx
CopyEdit
import React, { Component } from 'react';

class Welcome extends Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
function ProfileCard({ name, title }) {
  return (
    <div className="card">
      <h2>{name}</h2>
      <p>{title}</p>
    </div>
  );
}

function App() {
  return (
    <div>
      <ProfileCard name="Alice" title="Frontend Developer" />
      <ProfileCard name="Bob" title="Backend Engineer" />
    </div>
  );
}

```

---

## ✅ What to do with it

- ✅ Prefer **function components** with **hooks**.
- ✅ Use **props** to pass data into components.
- ✅ Keep components **pure** — avoid side effects directly inside them.
- ✅ Split large UIs into **smaller, focused components**.

---

## ❌ What not to do with it

- ❌ Don’t mutate props inside the component.
- ❌ Don’t use class components unless maintaining legacy code.
- ❌ Don’t mix too many responsibilities in a single component.
- ❌ Don’t name components with lowercase (e.g., `function app()` won’t work — it should be `App`).

---

## 📚 If you want to learn more

- React Docs (react.dev) – Describing the UI with Components
- Fullstackopen.com – Part 1: Component Basics
- EpicReact.dev by Kent C. Dodds – Function Components Module

# 📦 Props (Properties)

**Props** are **read-only inputs** to React components. They allow **data to flow from parent to child** components, making components dynamic and reusable.

Props are passed like **HTML attributes**, and accessed inside components via the `props` object or destructuring.

---

## 🔧 Syntax

### Passing props:

```jsx
jsx
CopyEdit
<Greeting name="Alice" age={25} />

```

### Receiving props in a function component:

```jsx
jsx
CopyEdit
function Greeting(props) {
  return <h1>Hello, {props.name}</h1>;
}

```

### Destructuring props:

```jsx
jsx
CopyEdit
function Greeting({ name, age }) {
  return <h1>{name} is {age} years old</h1>;
}

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
function Button({ label, onClick }) {
  return <button onClick={onClick}>{label}</button>;
}

function App() {
  const handleClick = () => alert('Button clicked!');

  return (
    <div>
      <Button label="Click Me" onClick={handleClick} />
    </div>
  );
}

```

---

## ✅ What to do with it

- ✅ Use props to make components **reusable and configurable**.
- ✅ Destructure props for **cleaner code**.
- ✅ Treat props as **immutable** (read-only).
- ✅ Combine multiple props logically (e.g., `firstName` + `lastName` = `fullName`).

---

## ❌ What not to do with it

- ❌ Don’t mutate or change props inside a component.
- ❌ Don’t forget to provide a **default value** or fallback (especially for optional props).
- ❌ Don’t rely solely on props for deep logic — separate concerns where necessary.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Passing Props to a Component
- Fullstackopen.com – Part 1: Component with props
- EpicReact.dev by Kent C. Dodds – Props Module

# 🧠 State (`useState` Hook)

**State** in React refers to **data that can change over time** within a component. The `useState` Hook lets you add state to **function components**, enabling your UI to respond to user input, network responses, and more.

---

## 🔧 Syntax

```jsx
jsx
CopyEdit
const [state, setState] = useState(initialValue);

```

- `state` – the current value.
- `setState` – a function that updates the value.
- `initialValue` – the starting state (number, string, object, array, etc.).

---

## 🧪 Example

```jsx
jsx
CopyEdit
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

---

## ✅ What to do with it

- ✅ Use `useState` for **local component state** (e.g., form inputs, toggles).
- ✅ Use **primitive values** (number, string) when possible to avoid unnecessary re-renders.
- ✅ If updating based on previous state, use a **callback**:

```jsx
jsx
CopyEdit
setCount(prev => prev + 1);

```

- ✅ Place `useState` **at the top level** of the component, not inside loops or conditions.

---

## ❌ What not to do with it

- ❌ Don’t mutate state directly (e.g., avoid `state.push()` for arrays).
- ❌ Don’t forget that state updates are **asynchronous** — they won't reflect immediately after calling `setState`.
- ❌ Don’t call `useState` conditionally — it breaks the Rules of Hooks.
- ❌ Don’t use state for **derived values** — calculate them inside the render.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Adding State to a Component
- Fullstackopen.com – Part 1: State Hooks
- EpicReact.dev by Kent C. Dodds – useState Module

# 🎮 Event Handling

Event handling in React allows you to **respond to user interactions** like clicks, key presses, or form submissions. React wraps standard DOM events in a special `SyntheticEvent` to provide a consistent interface across browsers.

---

## 🔧 Syntax

### ✅ Basic Event Handling

```jsx
jsx
CopyEdit
function Button() {
  const handleClick = () => {
    alert('Button clicked!');
  };

  return <button onClick={handleClick}>Click me</button>;
}

```

### ✅ Passing Arguments to Event Handlers

```jsx
jsx
CopyEdit
function Button({ label }) {
  const handleClick = (message) => {
    alert(message);
  };

  return <button onClick={() => handleClick(label)}>{label}</button>;
}

```

### ✅ Using Event Object

```jsx
jsx
CopyEdit
function Input() {
  const handleChange = (event) => {
    console.log(event.target.value);
  };

  return <input onChange={handleChange} />;
}

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
function LoginForm() {
  const [username, setUsername] = useState('');

  const handleChange = (e) => setUsername(e.target.value);
  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Submitted: ${username}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <inputtype="text"
        value={username}
        onChange={handleChange}
        placeholder="Enter username"
      />
      <button type="submit">Submit</button>
    </form>
  );
}

```

---

## ✅ What to do with it

- ✅ Use the `on<Event>` props (e.g., `onClick`, `onChange`, `onSubmit`) to handle user actions.
- ✅ Use **arrow functions** or **function expressions** for inline handlers to pass arguments.
- ✅ Always **call `e.preventDefault()`** for form submissions to prevent page reloads.
- ✅ Pass the **event object** if you need to access more details about the event (e.g., `event.target`).

---

## ❌ What not to do with it

- ❌ Don’t forget to bind methods when using **class components** (e.g., `this.handleClick = this.handleClick.bind(this)`).
- ❌ Don’t call the handler without the parentheses (e.g., `onClick={handleClick()}` will execute immediately).
- ❌ Avoid heavy logic in event handlers — keep them **clean and minimal**.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Handling Events
- Fullstackopen.com – Part 1: Event Handling
- EpicReact.dev by Kent C. Dodds – Event Handling

# 🔄 Rendering & Conditional Rendering

**Rendering** refers to how React components display UI elements based on their **state** and **props**. **Conditional rendering** is a technique used to render different content depending on certain conditions, such as a value or state change.

---

## 🔧 Syntax

### ✅ Basic Rendering

```jsx
jsx
CopyEdit
function Greeting({ isLoggedIn }) {
  if (isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please log in.</h1>;
  }
}

```

### ✅ Inline Conditional Rendering (Ternary Operator)

```jsx
jsx
CopyEdit
function Greeting({ isLoggedIn }) {
  return (
    <h1>{isLoggedIn ? 'Welcome back!' : 'Please log in.'}</h1>
  );
}

```

### ✅ Short-circuit Evaluation (`&&`)

```jsx
jsx
CopyEdit
function Message({ message }) {
  return <p>{message && 'You have a new message!'}</p>;
}

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
function UserProfile({ user }) {
  return (
    <div>
      {user ? (
        <h2>Welcome, {user.name}!</h2>
      ) : (
        <h2>Loading...</h2>
      )}
    </div>
  );
}

```

In this example, if the `user` object is available, a welcome message is shown; otherwise, a loading message appears.

---

## ✅ What to do with it

- ✅ Use **ternary operators** for simple conditional rendering.
- ✅ Use **short-circuit evaluation** (`&&`) for conditions where you want to render something **only when** a condition is true.
- ✅ Make sure you always return **valid JSX** from your conditional blocks.

---

## ❌ What not to do with it

- ❌ Don’t use `if` statements directly inside JSX.
- ❌ Don’t forget to return **fallback UI** when data is loading or unavailable.
- ❌ Don’t overcomplicate conditions — try to keep them simple and readable.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Conditional Rendering
- Fullstackopen.com – Part 1: Rendering Content Conditionally
- EpicReact.dev by Kent C. Dodds – Conditional Rendering

# 📝 Forms

Handling **forms** in React is crucial for user input, such as in login forms, registration forms, or any other interaction where data is collected. React offers a more **controlled** approach to handling forms, giving developers full control over input fields.

---

## 🔧 Syntax

### ✅ Controlled Components

In React, a controlled component is one whose value is controlled by the React state.

```jsx
jsx
CopyEdit
function Form() {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (e) => {
    setInputValue(e.target.value);
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Form submitted with input: ${inputValue}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <inputtype="text"
        value={inputValue}
        onChange={handleChange}
        placeholder="Type something"
      />
      <button type="submit">Submit</button>
    </form>
  );
}

```

### ✅ Uncontrolled Components

An uncontrolled component is one where the form element manages its own state, and React only interacts with the element through a **ref**.

```jsx
jsx
CopyEdit
function UncontrolledForm() {
  const inputRef = useRef();

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Form submitted with input: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} placeholder="Type something" />
      <button type="submit">Submit</button>
    </form>
  );
}

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
function SignUpForm() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Email: ${email}, Password: ${password}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Email:
        <inputtype="email"
          value={email}
          onChange={(e) => setEmail(e.target.value)}
        />
      </label>
      <br />
      <label>
        Password:
        <inputtype="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
        />
      </label>
      <br />
      <button type="submit">Sign Up</button>
    </form>
  );
}

```

---

## ✅ What to do with it

- ✅ Use **controlled components** for better control over form data.
- ✅ For **simple forms**, you can opt for **uncontrolled components** using refs, but controlled components are the preferred way in React.
- ✅ Always **validate user input** and provide proper feedback.
- ✅ Use **`onSubmit`** to handle form submissions and prevent the default behavior (`e.preventDefault()`).

---

## ❌ What not to do with it

- ❌ Don’t rely solely on the browser’s built-in form validation — handle custom validations in React.
- ❌ Don’t mutate state directly in form handlers (e.g., `inputValue.push()`). Always use the setter function.
- ❌ Don’t forget to **clear the form** after submission if necessary (e.g., resetting state).

---

## 📚 If you want to learn more

- React Docs (react.dev) – Forms
- Fullstackopen.com – Part 1: Forms in React
- EpicReact.dev by Kent C. Dodds – Forms Module

# 📜 Lists & Keys

In React, **lists** are used to display multiple items, and **keys** help React identify which items have changed, been added, or removed. Using **keys** is important for performance and to ensure the correct rendering of list items.

---

## 🔧 Syntax

### ✅ Rendering Lists with `.map()`

```jsx
jsx
CopyEdit
function ItemList({ items }) {
  return (
    <ul>
      {items.map((item) => (
        <li key={item.id}>{item.name}</li>
      ))}
    </ul>
  );
}

```

### ✅ Keys in List Items

```jsx
jsx
CopyEdit
function TodoList({ todos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo.id}>{todo.text}</li>
      ))}
    </ul>
  );
}

```

---

## 🧪 Example

```jsx
jsx
CopyEdit
function ProductList({ products }) {
  return (
    <div>
      <h2>Product List</h2>
      <ul>
        {products.map((product) => (
          <li key={product.id}>
            {product.name} - ${product.price}
          </li>
        ))}
      </ul>
    </div>
  );
}

```

In this example, the `key` is used to identify each `li` in the list. React will use the `id` from the `product` to efficiently re-render only the changed item.

---

## ✅ What to do with it

- ✅ Always use **unique keys** for list items to help React track items between renders.
- ✅ If possible, use **stable and unique values** (like database IDs) for keys.
- ✅ **Do not use array indices** as keys, as they may cause issues during dynamic updates (e.g., reordering, adding/removing items).

---

## ❌ What not to do with it

- ❌ Don’t use **non-unique values** (e.g., item names or indexes) as keys. This can lead to rendering problems.
- ❌ Don’t forget to use **keys** for all elements in an array, as React needs them for optimal performance.
- ❌ Avoid **index as a key** when the list items are reordered or dynamically changed.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Lists and Keys
- Fullstackopen.com – Part 1: Lists and Keys
- EpicReact.dev by Kent C. Dodds – Lists and Keys

# ⚖️ Controlled vs Uncontrolled Components

In React, **controlled** and **uncontrolled components** represent two approaches to managing form inputs. **Controlled components** are driven by React state, while **uncontrolled components** manage their own state internally.

---

## 🔧 Syntax

### ✅ Controlled Components

A **controlled component** is one where the form element's value is controlled by React state. React updates the state on user input, making it the **single source of truth**.

```jsx
jsx
CopyEdit
function ControlledForm() {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (e) => {
    setInputValue(e.target.value);
  };

  return (
    <form>
      <inputtype="text"
        value={inputValue}
        onChange={handleChange}
        placeholder="Type something"
      />
    </form>
  );
}

```

### ✅ Uncontrolled Components

An **uncontrolled component** is one where the form element's value is handled by the DOM itself, and React interacts with it via a **ref**.

```jsx
jsx
CopyEdit
function UncontrolledForm() {
  const inputRef = useRef();

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Form submitted with input: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} placeholder="Type something" />
      <button type="submit">Submit</button>
    </form>
  );
}

```

---

## 🧪 Example

### Controlled Component Example:

```jsx
jsx
CopyEdit
function EmailForm() {
  const [email, setEmail] = useState('');

  const handleEmailChange = (e) => setEmail(e.target.value);

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Email submitted: ${email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <inputtype="email"
        value={email}
        onChange={handleEmailChange}
        placeholder="Enter your email"
      />
      <button type="submit">Submit</button>
    </form>
  );
}

```

### Uncontrolled Component Example:

```jsx
jsx
CopyEdit
function PasswordForm() {
  const passwordRef = useRef();

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Password submitted: ${passwordRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="password" ref={passwordRef} placeholder="Enter your password" />
      <button type="submit">Submit</button>
    </form>
  );
}

```

---

## ✅ What to do with it

- ✅ **Use controlled components** when you need to have full control over the form data and need to validate or modify it in real-time.
- ✅ **Use uncontrolled components** when you don’t need to interact with the input data in real-time and prefer a simpler approach.

---

## ❌ What not to do with it

- ❌ Don’t mix controlled and uncontrolled components in the same form, as it can lead to unexpected behavior and state inconsistencies.
- ❌ Avoid using **uncontrolled components** for complex forms that require real-time validation or conditional rendering.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Forms
- Fullstackopen.com – Part 1: Controlled vs Uncontrolled Components
- EpicReact.dev by Kent C. Dodds – Forms (Controlled vs Uncontrolled)

# 🔄 State & Lifecycle

In React, **state** is used to store data that can change over time and cause the UI to re-render when the data changes. **Lifecycle methods** are special methods in a class component or hooks in functional components that allow you to run code at specific stages of a component's life.

---

## 🔧 Syntax

### ✅ Using State in Functional Components

You can use the `useState` hook to add state to a functional component.

```jsx
jsx
CopyEdit
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

### ✅ Using Lifecycle Methods in Class Components

In **class components**, React provides lifecycle methods to handle various stages of a component's lifecycle.

```jsx
jsx
CopyEdit
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }

  componentDidMount() {
    console.log('Component mounted!');
  }

  componentDidUpdate(prevProps, prevState) {
    if (prevState.count !== this.state.count) {
      console.log('Component updated!');
    }
  }

  componentWillUnmount() {
    console.log('Component will unmount!');
  }

  render() {
    return (
      <div>
        <p>Count: {this.state.count}</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Increment
        </button>
      </div>
    );
  }
}

```

---

## 🧪 Example

### Functional Component with State and Lifecycle (using Hooks)

```jsx
jsx
CopyEdit
import { useState, useEffect } from 'react';

function Timer() {
  const [seconds, setSeconds] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setSeconds((prevSeconds) => prevSeconds + 1);
    }, 1000);

    return () => clearInterval(interval); // Cleanup on unmount
  }, []);

  return <div>Elapsed Time: {seconds}s</div>;
}

```

In this example:

- The **state** is used to store the seconds.
- The **`useEffect`** hook manages the lifecycle of the timer (sets up and cleans up the interval).

---

## ✅ What to do with it

- ✅ **Use state** for values that change and need to be reflected in the UI.
- ✅ **Use the `useEffect` hook** to perform side effects in functional components.
- ✅ Use lifecycle methods like **`componentDidMount`**, **`componentDidUpdate`**, and **`componentWillUnmount`** in class components to handle side effects and cleanup.

---

## ❌ What not to do with it

- ❌ Don’t **directly mutate** state. Always use `setState` in class components or the setter from `useState` in functional components.
- ❌ Avoid using **`componentWillMount`** and **`componentWillUpdate`** as they are deprecated and should be replaced by `useEffect` or other hooks.
- ❌ Don’t forget to **clean up side effects** like timers, event listeners, or subscriptions using cleanup functions in `useEffect` or the corresponding class component methods.

---

## 📚 If you want to learn more

- React Docs (react.dev) – State and Lifecycle
- Fullstackopen.com – Part 1: State and Lifecycle
- EpicReact.dev by Kent C. Dodds – State and Lifecycle

# 🎨 Basic Styling (Inline, CSS Modules)

In React, styling components can be done in different ways. Two common approaches are **inline styles** and **CSS modules**. Each has its advantages, depending on the requirements of your project.

---

## 🔧 Syntax

### ✅ Inline Styling

Inline styling in React uses the `style` attribute, which accepts a **JavaScript object**. The properties are written in camelCase (e.g., `backgroundColor` instead of `background-color`).

```jsx
jsx
CopyEdit
function Button() {
  const buttonStyle = {
    backgroundColor: 'blue',
    color: 'white',
    padding: '10px 20px',
    borderRadius: '5px',
  };

  return <button style={buttonStyle}>Click Me</button>;
}

```

### ✅ CSS Modules

CSS Modules allow you to scope your styles locally to the component by creating a separate CSS file. It avoids global scope pollution, making it easier to manage large applications.

1. Create a `.module.css` file.

```css
css
CopyEdit
/* Button.module.css */
.button {
  background-color: blue;
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
}

```

1. Import the CSS module in your component.

```jsx
jsx
CopyEdit
import styles from './Button.module.css';

function Button() {
  return <button className={styles.button}>Click Me</button>;
}

```

---

## 🧪 Example

### Inline Styling Example:

```jsx
jsx
CopyEdit
function Card() {
  const cardStyle = {
    backgroundColor: '#f4f4f4',
    padding: '20px',
    borderRadius: '10px',
    boxShadow: '0px 4px 6px rgba(0, 0, 0, 0.1)',
  };

  return <div style={cardStyle}>This is a card component</div>;
}

```

### CSS Module Example:

```css
css
CopyEdit
/* Card.module.css */
.card {
  background-color: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}

```

```jsx
jsx
CopyEdit
import styles from './Card.module.css';

function Card() {
  return <div className={styles.card}>This is a card component</div>;
}

```

---

## ✅ What to do with it

- ✅ **Use inline styles** for simple, one-off styles that are dynamically set or calculated in the component.
- ✅ **Use CSS Modules** for larger projects where you want to scope your styles to a specific component without affecting global styles.
- ✅ **Combine** inline styles and CSS Modules when needed, for example, when adding dynamic properties to CSS Module-based components.

---

## ❌ What not to do with it

- ❌ Don’t use **inline styles** for complex styles that involve pseudo-classes (like `:hover`) or media queries.
- ❌ Avoid using **global CSS** styles that can lead to style conflicts across components, especially in large projects.
- ❌ Don’t forget to **import** the `.module.css` file correctly when using CSS Modules.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Styling and CSS
- Fullstackopen.com – Part 1: Styling
- EpicReact.dev by Kent C. Dodds – Styling

# 🔄 Basic useEffect for Side Effects

The `useEffect` hook in React is used to handle side effects in functional components. Side effects include data fetching, setting up subscriptions, manually changing the DOM, or performing cleanup operations. `useEffect` runs after every render, but you can control its behavior with dependencies.

---

## 🔧 Syntax

```jsx
jsx
CopyEdit
useEffect(() => {
  // Code to run after every render or when dependencies change
  return () => {
    // Cleanup function (optional)
  };
}, [dependencies]);

```

- **First argument**: A function to run the effect.
- **Second argument**: An optional array of dependencies that tells React when to run the effect. If the array is empty, it runs only once after the initial render (like `componentDidMount` in class components).

---

## 🧪 Example

### Basic useEffect Example (Data Fetching)

```jsx
jsx
CopyEdit
import { useEffect, useState } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('/api/data')
      .then((res) => res.json())
      .then(setData);
  }, []); // Empty array ensures effect runs only once after the initial render

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}

```

In this example:

- `useEffect` fetches data from an API after the component mounts (i.e., after the initial render).
- The empty dependency array `[]` ensures the effect runs only once.

---

## ✅ What to do with it

- ✅ **Use `useEffect`** to perform side effects such as data fetching, DOM manipulation, or setting up subscriptions.
- ✅ **Use the cleanup function** to clean up resources (like canceling network requests or removing event listeners) when the component unmounts or before the effect re-runs.
- ✅ **Control when the effect runs** by providing a dependency array. If the array is empty, the effect will only run once on mount.

---

## ❌ What not to do with it

- ❌ Don’t **forget to include all necessary dependencies** in the dependency array. If you depend on a value inside `useEffect`, add it to the array.
- ❌ Avoid **mutating state** directly inside the effect function. Always use the setter function from `useState` to update the state.
- ❌ Don’t perform **non-deterministic tasks** (like fetching the current time) inside `useEffect` without proper dependency handling.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Hooks → useEffect
- Fullstackopen.com – Part 1: useEffect
- EpicReact.dev by Kent C. Dodds – useEffect

# 🔄 useEffect Deep Dive (Cleanup, Dependencies)

The `useEffect` hook in React is essential for performing side effects in functional components. A deeper understanding of how to handle **cleanup** and **dependencies** can significantly enhance the performance and reliability of your components.

---

## 🔧 Syntax

```jsx
jsx
CopyEdit
useEffect(() => {
  // Code to run on effect
  return () => {
    // Cleanup function (optional)
  };
}, [dependencies]);

```

- **First argument**: A function that runs after every render or when any of the dependencies change.
- **Second argument**: An optional array of dependencies that tells React when to re-run the effect. If the array is empty, it runs once after the initial render (like `componentDidMount`).

---

## 🧪 Example: Cleanup and Dependencies

### Example 1: Cleanup Function (Event Listener)

```jsx
jsx
CopyEdit
import { useEffect } from 'react';

function MouseTracker() {
  useEffect(() => {
    const handleMouseMove = (event) => {
      console.log('Mouse moved:', event.clientX, event.clientY);
    };

    window.addEventListener('mousemove', handleMouseMove);

    return () => {
      window.removeEventListener('mousemove', handleMouseMove); // Cleanup
    };
  }, []); // Empty array ensures effect runs only once

  return <div>Move the mouse around to see the effect!</div>;
}

```

In this example:

- We set up a **mousemove** event listener when the component mounts.
- The **cleanup function** removes the event listener when the component unmounts to avoid memory leaks.

---

### Example 2: Dependencies (Re-running Effect When State Changes)

```jsx
jsx
CopyEdit
import { useState, useEffect } from 'react';

function DataFetcher() {
  const [query, setQuery] = useState('react');
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(`/api/search?q=${query}`)
      .then((res) => res.json())
      .then(setData);
  }, [query]); // The effect will re-run when 'query' changes

  return (
    <div>
      <inputtype="text"
        value={query}
        onChange={(e) => setQuery(e.target.value)}
        placeholder="Search"
      />
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

```

In this example:

- **`useEffect`** runs every time the `query` state changes.
- The **dependency array** `[query]` ensures that the effect only re-runs when the `query` value changes.

---

## ✅ What to do with it

- ✅ **Use cleanup functions** to clean up side effects like event listeners, network requests, or subscriptions to avoid memory leaks or unwanted behavior.
- ✅ **Use the dependency array** to optimize performance by limiting the number of times the effect runs. Only include values that should trigger the effect.
- ✅ **Make sure to handle dependencies properly**, including functions or objects that may change between renders, to avoid unnecessary re-renders or stale state.

---

## ❌ What not to do with it

- ❌ Don’t forget to include all dependencies in the dependency array. If a value used inside `useEffect` changes but is not included in the array, the effect may not run as expected.
- ❌ Avoid using **non-deterministic values** in the effect body unless properly managed (e.g., using a stable reference).
- ❌ Don’t mutate **state directly** in the effect. Always use the setter function from `useState`.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Hooks → useEffect
- Fullstackopen.com – Part 1: useEffect
- EpicReact.dev by Kent C. Dodds – useEffect

# 🧩 Custom Hooks

Custom hooks are a powerful feature in React that allows you to extract and reuse logic across multiple components. By creating a custom hook, you can encapsulate stateful logic and side effects in a reusable way, making your components cleaner and more maintainable.

---

## 🔧 Syntax

A custom hook is a JavaScript function that starts with the prefix `use`, and it can call other hooks like `useState`, `useEffect`, etc.

```jsx
jsx
CopyEdit
function useCustomHook() {
  const [state, setState] = useState(initialValue);

  useEffect(() => {
    // side effect logic here
  }, [dependencies]);

  return [state, setState]; // Or any other logic you need to return
}

```

To use a custom hook, you simply call it like any other hook inside a component.

```jsx
jsx
CopyEdit
function MyComponent() {
  const [value, setValue] = useCustomHook();

  return <div>{value}</div>;
}

```

---

## 🧪 Example

### Example 1: Custom Hook for Fetching Data

```jsx
jsx
CopyEdit
import { useState, useEffect } from 'react';

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch(url);
        const result = await response.json();
        setData(result);
      } catch (err) {
        setError(err);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, [url]);

  return { data, loading, error };
}

```

### Example 2: Using the `useFetch` Custom Hook

```jsx
jsx
CopyEdit
function DataFetcher() {
  const { data, loading, error } = useFetch('/api/data');

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error: {error.message}</p>;

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}

```

In this example:

- `useFetch` is a custom hook that encapsulates the logic for fetching data from a URL.
- The hook returns an object containing the `data`, `loading`, and `error` states, which can be easily reused in any component.

---

## ✅ What to do with it

- ✅ **Use custom hooks** to extract and reuse logic across multiple components.
- ✅ **Encapsulate side effects, state management, and logic** that is common across components into custom hooks.
- ✅ **Follow the rules of hooks**, such as calling hooks at the top level of a component or custom hook.

---

## ❌ What not to do with it

- ❌ Don’t **overuse custom hooks** for simple logic that doesn't need to be reused or abstracted. It's important to balance abstraction with clarity.
- ❌ Avoid calling **hooks conditionally**. Always ensure hooks are called in the same order across renders.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Hooks → Custom Hooks
- Fullstackopen.com – Part 1: Custom Hooks
- EpicReact.dev by Kent C. Dodds – Custom Hooks

# 🧳 useRef

The `useRef` hook is a versatile tool in React. It is used to persist values across renders without causing re-renders. It can be used to reference DOM elements directly or to store mutable values that do not need to trigger a re-render when changed.

---

## 🔧 Syntax

```jsx
jsx
CopyEdit
const ref = useRef(initialValue);

```

- **initialValue**: The value you want to initialize the ref with. This value can be anything (e.g., an object, a DOM element, or a primitive value).
- **ref**: An object with a `current` property that stores the current value.

---

## 🧪 Example

### Example 1: Accessing DOM Elements

```jsx
jsx
CopyEdit
import { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus(); // Access the DOM element directly
  };

  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Focus me!" />
      <button onClick={focusInput}>Focus the input</button>
    </div>
  );
}

```

In this example:

- `inputRef` is used to reference the `<input>` element, allowing us to focus it programmatically when the button is clicked.

### Example 2: Storing a Mutable Value

```jsx
jsx
CopyEdit
import { useRef, useState } from 'react';

function Timer() {
  const countRef = useRef(0);
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
    countRef.current += 1; // Update the mutable ref value
  };

  return (
    <div>
      <p>State count: {count}</p>
      <p>Ref count: {countRef.current}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

```

In this example:

- `countRef` stores a value that persists across renders, but does not trigger re-renders when updated.
- The state (`count`) triggers re-renders, while `countRef` allows us to store a value without causing a re-render.

---

## ✅ What to do with it

- ✅ **Use `useRef`** to access DOM elements directly, like focusing inputs, measuring element sizes, or managing animations.
- ✅ **Store mutable values** that you don't want to cause re-renders when they change (e.g., timers, previous state, or external event listeners).
- ✅ **Combine `useRef` with event listeners** for scenarios where you need to track something across renders without re-triggering re-renders.

---

## ❌ What not to do with it

- ❌ Don’t **rely on `useRef` for state** if the value change needs to trigger re-renders. For that, use `useState` instead.
- ❌ Don’t mutate refs directly without understanding the flow, as it can lead to unexpected behavior if used incorrectly.
- ❌ Avoid using `useRef` as a substitute for `useState` in cases where you need to trigger UI updates.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Hooks → useRef
- Fullstackopen.com – Part 1: useRef
- EpicReact.dev by Kent C. Dodds – useRef

# 🧳 useContext (Context API)

The `useContext` hook is a part of React's Context API, allowing you to share values across the component tree without passing props down manually at every level. This is particularly useful for global state, themes, authentication, or settings that need to be accessed by many components.

---

## 🔧 Syntax

```jsx
jsx
CopyEdit
const value = useContext(MyContext);

```

- **MyContext**: The context object that was created using `React.createContext()`.
- **value**: The current value of the context, which can be any JavaScript value (objects, arrays, functions, etc.).

---

## 🧪 Example

### Example 1: Creating and Using a Context

```jsx
jsx
CopyEdit
import { createContext, useState, useContext } from 'react';

// Step 1: Create the context
const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState('light');

  return (
    <ThemeContext.Provider value={theme}>
      <div>
        <h1>Current Theme: {theme}</h1>
        <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
          Toggle Theme
        </button>
        <ThemeComponent />
      </div>
    </ThemeContext.Provider>
  );
}

function ThemeComponent() {
  // Step 2: Use context in a child component
  const theme = useContext(ThemeContext);

  return <p>The current theme is {theme}</p>;
}

```

In this example:

- `ThemeContext` is created using `createContext()`.
- The `useContext` hook is used to consume the current theme value inside `ThemeComponent`.
- The context value (`theme`) is provided by the `ThemeContext.Provider` in the parent component (`App`).

### Example 2: Using Context for User Authentication

```jsx
jsx
CopyEdit
import { createContext, useContext, useState } from 'react';

// Step 1: Create the context
const UserContext = createContext();

function App() {
  const [user, setUser] = useState(null);

  return (
    <UserContext.Provider value={user}>
      <div>
        <h1>Authentication</h1>
        {!user ? (
          <button onClick={() => setUser({ name: 'John Doe' })}>Log In</button>
        ) : (
          <div>
            <p>Welcome, {user.name}!</p>
            <button onClick={() => setUser(null)}>Log Out</button>
          </div>
        )}
        <Profile />
      </div>
    </UserContext.Provider>
  );
}

function Profile() {
  // Step 2: Use context in a child component
  const user = useContext(UserContext);

  if (!user) {
    return <p>Please log in to see your profile.</p>;
  }

  return <p>Your name is {user.name}</p>;
}

```

In this example:

- The `UserContext` is used to manage the user authentication state, making the user object accessible to all components under `UserContext.Provider`.
- `useContext(UserContext)` is used to consume the current user value inside the `Profile` component.

---

## ✅ What to do with it

- ✅ **Use `useContext`** when you need to pass data through the component tree without manually passing props at every level.
- ✅ **Combine `useContext` with `useReducer`** to manage complex state like global application state or authentication.
- ✅ **Provide default values** in your context so that consumers will have access to meaningful data even if no `Provider` is used.

---

## ❌ What not to do with it

- ❌ Don’t **overuse context** for every piece of state. Use it primarily for global state that must be accessible from many components (e.g., theme, authentication state).
- ❌ Avoid placing **frequently changing state** (e.g., user inputs, animations) in context as it could lead to unnecessary re-renders of components that consume the context.
- ❌ Don’t **nest multiple Providers** unnecessarily, as it can create overly complex component trees.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Context API
- Fullstackopen.com – Part 1: Context API
- EpicReact.dev by Kent C. Dodds – Context API

# 🧳 Prop Drilling vs Lifting State Up

In React, managing state and passing data between components can lead to two common patterns: **Prop Drilling** and **Lifting State Up**. Both approaches solve different problems, and knowing when to use each can significantly improve the structure of your components and your app's maintainability.

---

## 🔧 Prop Drilling

**Prop drilling** refers to the process of passing data from a parent component to a deeply nested child component through multiple intermediary components (i.e., "drilling" props down through layers of components).

### When to Use Prop Drilling:

- When data is only needed in a few components.
- When the component tree structure is relatively shallow.
- When you want clear component isolation without introducing unnecessary state management solutions.

### Example: Prop Drilling

```jsx
jsx
CopyEdit
function Parent() {
  const [theme, setTheme] = useState('light');

  return (
    <div>
      <h1>Parent Component</h1>
      <Child theme={theme} setTheme={setTheme} />
    </div>
  );
}

function Child({ theme, setTheme }) {
  return (
    <div>
      <h2>Child Component</h2>
      <Grandchild theme={theme} setTheme={setTheme} />
    </div>
  );
}

function Grandchild({ theme, setTheme }) {
  return (
    <div>
      <h3>Grandchild Component</h3>
      <p>Current Theme: {theme}</p>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Toggle Theme
      </button>
    </div>
  );
}

```

In this example:

- `theme` and `setTheme` are passed down from the `Parent` component to the `Grandchild` component through `Child`, even though `Child` itself doesn't need these props.

---

## 🔧 Lifting State Up

**Lifting state up** involves moving the state from a child component to the closest common ancestor component. This allows the ancestor component to manage the state and pass it down to the necessary child components.

### When to Use Lifting State Up:

- When multiple sibling components need to share the same state.
- When the state needs to be updated or read by multiple components at different levels.
- When you need to ensure consistent state between components.

### Example: Lifting State Up

```jsx
jsx
CopyEdit
function Parent() {
  const [theme, setTheme] = useState('light');

  return (
    <div>
      <h1>Parent Component</h1>
      <Child theme={theme} setTheme={setTheme} />
      <AnotherChild theme={theme} setTheme={setTheme} />
    </div>
  );
}

function Child({ theme, setTheme }) {
  return (
    <div>
      <h2>Child Component</h2>
      <p>Current Theme: {theme}</p>
      <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Toggle Theme
      </button>
    </div>
  );
}

function AnotherChild({ theme, setTheme }) {
  return (
    <div>
      <h2>Another Child Component</h2>
      <p>Current Theme: {theme}</p>
    </div>
  );
}

```

In this example:

- The state (`theme`) and its setter (`setTheme`) are lifted up to the `Parent` component, so both `Child` and `AnotherChild` can access and update the same state.

---

## ✅ What to do with it

### Prop Drilling:

- ✅ **Use prop drilling** for passing data down a shallow component tree.
- ✅ **Use prop drilling** when the data flow is simple and doesn't require state updates from multiple components.

### Lifting State Up:

- ✅ **Lift state up** when multiple components at different levels need to share or modify the same state.
- ✅ **Lift state up** to avoid redundant state management in deeply nested child components.
- ✅ **Lift state up** to ensure that the parent manages the state in a centralized manner.

---

## ❌ What not to do with it

### Prop Drilling:

- ❌ Don’t excessively drill props through many layers of components when other solutions (like Context API or state management) can simplify the data flow.
- ❌ Avoid prop drilling when a state is shared by deeply nested components or when the same data is passed through multiple layers.

### Lifting State Up:

- ❌ Don’t lift state up unnecessarily for components that don’t need access to the shared state.
- ❌ Avoid lifting state up too far in the component tree, making the ancestor components overly complex and harder to manage.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Lifting State Up
- Fullstackopen.com – Part 1: Lifting State Up
- EpicReact.dev by Kent C. Dodds – Prop Drilling vs Lifting State Up

# 🧳 Component Composition vs Inheritance

In React, component design can be approached in two primary ways: **Component Composition** and **Inheritance**. While both are ways of structuring components and reusing code, React’s philosophy strongly favors composition due to its flexibility and simplicity.

---

## 🔧 Component Composition

**Component Composition** is the process of building complex UIs by combining simpler, smaller components. Instead of relying on inheritance, components are composed together, where each component is independent and reusable.

### Benefits:

- Promotes reusability and modularity.
- Encourages separation of concerns.
- Easy to manage and update as components are self-contained.
- Easier to understand and debug as there is no hierarchical relationship like in inheritance.

### Example: Component Composition

```jsx
jsx
CopyEdit
function Card({ title, children }) {
  return (
    <div className="card">
      <h2>{title}</h2>
      <div>{children}</div>
    </div>
  );
}

function App() {
  return (
    <Card title="Welcome to React">
      <p>This is a simple card component that can be reused with different content.</p>
    </Card>
  );
}

```

In this example:

- `Card` is a reusable component that takes a `title` prop and accepts children (other components or elements) to be displayed within the card.
- The `children` prop is used to compose the card with different content based on its usage in the `App` component.

---

## 🔧 Inheritance

**Inheritance** refers to a class-based approach where a component can inherit properties and behavior from another class component. React’s class-based components could use inheritance, but it is less favored in modern React development in favor of functional components and composition.

### When to Use Inheritance:

- Inheritance is generally used when you need a specialized class or behavior that extends a base class. However, this is rarely needed in React due to the power of composition.
- When the component hierarchy becomes complex and needs shared functionality across components (though React’s context, hooks, and higher-order components (HOCs) often solve this better).

### Example: Inheritance (Class Components)

```jsx
jsx
CopyEdit
class BaseCard extends React.Component {
  render() {
    return (
      <div className="card">
        <h2>{this.props.title}</h2>
        <div>{this.props.children}</div>
      </div>
    );
  }
}

class App extends BaseCard {
  render() {
    return (
      <BaseCard title="Welcome to React">
        <p>This is an example of inheritance in React.</p>
      </BaseCard>
    );
  }
}

```

In this example:

- `App` is inheriting from `BaseCard`, meaning it gets all the behavior of `BaseCard` and can be extended with additional methods or functionality.
- This pattern is less common and not recommended in modern React, as component composition is much more flexible.

---

## ✅ What to do with it

### Component Composition:

- ✅ **Use component composition** for building flexible and reusable components.
- ✅ **Pass props to children** to make components customizable while maintaining their independence.
- ✅ **Use higher-order components (HOCs)** or **render props** for sharing behavior among components in a composition-driven way.

### Inheritance:

- ✅ **Consider inheritance** when extending a component with a specific functionality or behavior (but in React, this is rare and can often be replaced by composition).
- ✅ **Use inheritance cautiously** if you need a class to share stateful logic between many components (though Hooks often provide a more effective solution).

---

## ❌ What not to do with it

### Component Composition:

- ❌ Don’t over-complicate your components by composing too many deeply nested children. Keep it simple and intuitive.
- ❌ Avoid creating large monolithic components that do too much. Break down logic into smaller components for better reusability.

### Inheritance:

- ❌ Don’t use inheritance as the primary means of reusing component logic. It can lead to tightly coupled components and a complex, hard-to-manage component hierarchy.
- ❌ Avoid using inheritance if you don’t need to extend or share state and behavior across components. Composition usually handles these cases more cleanly.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Composition vs Inheritance
- Fullstackopen.com – Part 1: Component Composition
- EpicReact.dev by Kent C. Dodds – Composition vs Inheritance

# 🧳 React Router (v6+)

**React Router** is a popular routing library for React that enables navigation between different components and views in a single-page application (SPA). It allows developers to manage URL routing, render specific components based on the URL, and handle navigation seamlessly.

**React Router v6** introduces several breaking changes and improvements over v5, making routing more declarative, intuitive, and easier to use.

---

## 🔧 What is React Router?

**React Router** is used to create routes in a React application and control the rendering of components based on the URL path. React Router allows us to declaratively map different parts of an application to URLs, enabling dynamic and efficient navigation.

---

## 🔧 Key Features of React Router (v6+)

- **Declarative routing**: Routes are defined in JSX, making routing more predictable and easier to manage.
- **Nested routes**: Organize your routes in a hierarchical manner to create better app structure.
- **Relative routing**: Routes are defined relative to their parent routes, which allows more flexibility.
- **Automatic route matching**: React Router now uses a more sophisticated matching algorithm for better route matching and rendering.
- **Redirects**: Instead of `<Redirect />`, React Router v6 uses the `useNavigate` hook or `<Navigate />` component to handle redirection.

---

## 🔧 Basic Usage

### Installation:

```bash
bash
CopyEdit
npm install react-router-dom@6

```

### Define Routes in your App

In React Router v6, routing is done using the `Routes` component instead of `Switch`, and route matching is now more strict.

```jsx
jsx
CopyEdit
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
}

```

In this example:

- The `Router` component wraps the routes.
- The `Routes` component is used to wrap multiple `Route` elements.
- The `Route` component defines the path and the component to render when the URL matches that path.

---

## 🔧 Nested Routes

React Router v6 makes it easy to handle nested routes, allowing components to render nested content based on the URL path.

### Example: Nested Routes

```jsx
jsx
CopyEdit
function Dashboard() {
  return (
    <div>
      <h2>Dashboard</h2>
      <Routes>
        <Route path="overview" element={<Overview />} />
        <Route path="settings" element={<Settings />} />
      </Routes>
    </div>
  );
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/dashboard/*" element={<Dashboard />} />
      </Routes>
    </Router>
  );
}

```

Here, `/dashboard/overview` and `/dashboard/settings` will render the respective components based on the path. The `*` in `path="/dashboard/*"` tells React Router to match any child routes inside the `Dashboard` component.

---

## 🔧 Navigation

To programmatically navigate to different routes, React Router v6 uses the `useNavigate` hook instead of the older `useHistory`.

### Example: Programmatic Navigation

```jsx
jsx
CopyEdit
import { useNavigate } from 'react-router-dom';

function HomePage() {
  const navigate = useNavigate();

  const goToContact = () => {
    navigate('/contact');
  };

  return <button onClick={goToContact}>Go to Contact</button>;
}

```

In this example:

- The `useNavigate` hook returns a function (`navigate`) that allows you to navigate to different routes programmatically.

---

## 🔧 Link vs NavLink

- **Link**: Used to navigate between routes by rendering anchor tags (`<a>`).
- **NavLink**: Similar to `Link`, but allows for applying styles to the active route.

### Example: Using Link and NavLink

```jsx
jsx
CopyEdit
import { Link, NavLink } from 'react-router-dom';

function Navigation() {
  return (
    <nav>
      <Link to="/">Home</Link>
      <NavLink to="/about" activeClassName="active">About</NavLink>
    </nav>
  );
}

```

In this example:

- The `Link` component renders an anchor tag to navigate to a specific route.
- The `NavLink` component is used to apply styles (like `activeClassName`) when the current route matches.

---

## 🔧 Route Parameters

React Router v6 supports dynamic routes with parameters. These parameters can be accessed using the `useParams` hook.

### Example: Dynamic Route with Parameters

```jsx
jsx
CopyEdit
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { id } = useParams();
  return <h1>User Profile for ID: {id}</h1>;
}

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/user/:id" element={<UserProfile />} />
      </Routes>
    </Router>
  );
}

```

In this example:

- The `UserProfile` component will display a different message based on the `id` parameter passed in the URL (`/user/123` would render `User Profile for ID: 123`).
- The `useParams` hook is used to extract the route parameters.

---

## ✅ What to do with it

- ✅ **Use React Router** to manage navigation in a React app, especially for SPAs.
- ✅ **Use the `Routes` component** instead of `Switch` for route matching in React Router v6.
- ✅ **Use `useNavigate`** for programmatic navigation in your app.
- ✅ **Use nested routes** to create a clean and logical route structure.
- ✅ **Use `NavLink`** to highlight active links and improve UX.

---

## ❌ What not to do with it

- ❌ Don’t use `Switch` in React Router v6, as it has been replaced by `Routes`.
- ❌ Avoid using `<Redirect />` for redirects in v6. Instead, use `useNavigate` or `<Navigate />`.
- ❌ Don’t overcomplicate route structures. Keep routes simple and understandable to improve maintainability.

---

## 📚 If you want to learn more

- React Docs (react.dev) – React Router
- Fullstackopen.com – Part 1: React Router
- EpicReact.dev by Kent C. Dodds – React Router

# 🌐 Fetching Data (with fetch/axios)

In React, fetching data is a common task when you need to display dynamic content from external APIs or servers. There are several ways to fetch data, but the two most popular methods are using the `fetch` API and third-party libraries like `axios`.

---

## 🔧 What is Fetching Data?

Fetching data refers to the process of sending an HTTP request to an API or server to retrieve information and then using that information in your app.

- **fetch**: A built-in JavaScript API that allows you to make HTTP requests to external resources (like REST APIs).
- **axios**: A popular third-party library that simplifies making HTTP requests, with additional features like automatic JSON parsing, request cancellation, and more.

---

## 🔧 Fetch API

The `fetch` API is built into JavaScript and provides a simple way to fetch resources over the network. It returns a `Promise` that resolves to the `Response` object representing the response to the request.

---

### Example: Fetch Data with fetch

```jsx
jsx
CopyEdit
import { useState, useEffect } from 'react';

function DataFetcher() {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then((response) => {
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        return response.json();
      })
      .then((data) => setData(data))
      .catch((error) => setError(error.message));
  }, []);

  if (error) {
    return <div>Error: {error}</div>;
  }

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}

```

In this example:

- The `useEffect` hook is used to fetch data when the component is mounted.
- The `fetch` function is called to make the request to the API.
- If the response is successful, the data is stored in the `data` state. If there’s an error, it’s caught and displayed.

---

## 🔧 Axios

`Axios` is a promise-based HTTP client for the browser and Node.js. It simplifies making HTTP requests and provides additional features, such as automatic JSON parsing and handling of request/response interceptors.

To use Axios, you need to install it first:

```bash
bash
CopyEdit
npm install axios

```

---

### Example: Fetch Data with Axios

```jsx
jsx
CopyEdit
import { useState, useEffect } from 'react';
import axios from 'axios';

function DataFetcher() {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios
      .get('https://api.example.com/data')
      .then((response) => setData(response.data))
      .catch((error) => setError(error.message));
  }, []);

  if (error) {
    return <div>Error: {error}</div>;
  }

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}

```

In this example:

- The `axios.get` method is used to fetch the data.
- `response.data` contains the response body, which is automatically parsed from JSON.
- The error handling is done via the `.catch()` method.

---

## 🔧 What to do with it

- ✅ **Use fetch** for basic data fetching needs, as it’s built into JavaScript and easy to use.
- ✅ **Use Axios** for more advanced features, such as handling request/response interceptors, request cancellation, or when working with more complex APIs.
- ✅ **Handle loading and error states** in your component to provide a better user experience.
- ✅ **Use `useEffect`** to perform side effects like data fetching when the component mounts.

---

## ❌ What not to do with it

- ❌ Don’t forget to handle errors. Always include `.catch()` for `fetch` or `.catch()` for Axios to handle any network or data parsing issues.
- ❌ Avoid making data requests directly inside the render method. Always use `useEffect` or other lifecycle methods to fetch data asynchronously.
- ❌ Don’t forget to cancel pending requests if the component unmounts, especially in the case of Axios or complex requests.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Data Fetching
- [EpicReact.dev by Kent C. Dodds – Fetching Data](https://epicreact.dev/)
- Fullstackopen.com – Fetching Data

# 🚨 Error Boundaries

In React, an **Error Boundary** is a higher-order component that catches JavaScript errors anywhere in the component tree, logs those errors, and displays a fallback UI instead of crashing the entire component tree. It helps to create more robust and user-friendly React applications.

---

## 🔧 What are Error Boundaries?

Error Boundaries allow you to catch errors in the lifecycle methods, render methods, and constructors of your React components. They prevent the entire component tree from crashing due to errors in one part of the app, improving the user experience and app stability.

---

### How Error Boundaries Work:

- When an error occurs in a component, React will check if any of its parent components are Error Boundaries.
- If it finds one, it will "catch" the error and display a fallback UI.
- If no Error Boundary is found, the app will crash, and an error message will be shown in the console.

---

## 🔧 How to Create an Error Boundary?

An Error Boundary is created by defining a class component that implements **`componentDidCatch`** and/or **`static getDerivedStateFromError`** methods.

- **`getDerivedStateFromError`** is used to render a fallback UI after an error occurs.
- **`componentDidCatch`** allows you to log error information or send it to an error reporting service.

---

### Example: Creating an Error Boundary

```jsx
jsx
CopyEdit
import React, { Component } from 'react';

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false, errorMessage: '' };
  }

  static getDerivedStateFromError(error) {
    // Update state to show fallback UI
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    // Log error details to an external service (optional)
    console.log(error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong. Please try again later.</h1>;
    }

    return this.props.children;
  }
}

```

In this example:

- The `ErrorBoundary` component has state `hasError` to track if an error occurs.
- The `getDerivedStateFromError` method updates the state when an error is caught.
- The `componentDidCatch` method logs the error and additional information, which can be sent to external services for monitoring.
- The component renders its children unless an error occurs, in which case it shows a fallback UI.

---

## 🔧 Using Error Boundaries in Your Application

To use an Error Boundary, wrap your components with it:

```jsx
jsx
CopyEdit
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>

```

This will ensure that if `MyComponent` throws an error, the Error Boundary will catch it, and the fallback UI will be shown instead of the app crashing.

---

## 🔧 What to do with it

- ✅ **Use Error Boundaries** to catch JavaScript errors and prevent the entire app from crashing.
- ✅ **Wrap critical components** in an Error Boundary to display a fallback UI when something goes wrong.
- ✅ **Log errors** to external services like Sentry or LogRocket to monitor errors in production.
- ✅ **Combine Error Boundaries** with other state management solutions for graceful error handling and recovery.

---

## ❌ What not to do with it

- ❌ Don’t use Error Boundaries for handling logic or business errors. They are only for rendering errors in the React component tree.
- ❌ Don’t wrap the entire app in a single Error Boundary. Use multiple Error Boundaries at different levels to catch and recover from errors more granularly.
- ❌ Don’t forget to handle fallback UI properly. Make sure to provide clear, actionable feedback to the user when something goes wrong.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Error Boundaries
- [EpicReact.dev by Kent C. Dodds – Error Boundaries](https://epicreact.dev/)
- Fullstackopen.com – Error Boundaries

# 🔄 useReducer (vs useState)

In React, both `useState` and `useReducer` are hooks that allow you to manage state in functional components. However, `useReducer` is typically more appropriate for managing complex state logic, whereas `useState` is better suited for simpler state management.

---

## 🔧 What is `useReducer`?

`useReducer` is a React hook that is used for managing more complex state logic. It is usually preferred when you have state transitions that depend on the previous state or when managing state involves multiple sub-values or actions.

It takes a **reducer function** (similar to Redux) and an initial state as arguments and returns the current state and a dispatch function.

---

## 🔧 `useReducer` vs `useState`

- **`useState`** is a hook for managing simple, localized state. You can update the state by passing the new state directly.
- **`useReducer`** is useful when the state logic becomes more complex or when you need to perform actions that involve updating multiple pieces of state simultaneously.

---

### Example: `useState`

```jsx
jsx
CopyEdit
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

In this example, `useState` is sufficient since the state is simple and doesn't involve complex logic.

---

### Example: `useReducer`

```jsx
jsx
CopyEdit
import { useReducer } from 'react';

const initialState = { count: 0 };

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>{state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>
    </div>
  );
}

```

In this example, `useReducer` is used because the state logic is more complex. You manage the state using actions and a reducer function.

---

## 🔧 When to Use `useReducer` Over `useState`?

- **Complex State Logic**: Use `useReducer` when your state changes involve more complex logic or multiple variables that need to be updated together.
- **State Dependent on Previous State**: If the new state depends on the previous state, `useReducer` can provide more control by using actions.
- **Better for Larger Applications**: If your app is growing, `useReducer` can make it easier to maintain and scale because the state logic is encapsulated in a single reducer function.
- **Use Case for Redux-like Patterns**: If you’re building a component that has behavior similar to Redux, `useReducer` might be a good fit.

---

## 🔧 What to do with it

- ✅ **Use `useReducer`** when you have more complex state transitions or need to manage state that depends on previous states.
- ✅ **Use `useReducer`** for scenarios like forms with multiple inputs, managing multiple related values, or when state updates are based on more complex actions.
- ✅ **Use `useState`** for simpler, more localized state that doesn’t require complex logic.

---

## ❌ What not to do with it

- ❌ Don’t use `useReducer` when your state logic is simple and doesn’t involve much interaction. In those cases, `useState` is more intuitive and easier to work with.
- ❌ Don’t overuse `useReducer` in small components where `useState` would be sufficient. It’s easy to over-engineer simple state management.

---

## 📚 If you want to learn more

- React Docs (react.dev) – useReducer
- [EpicReact.dev by Kent C. Dodds – useReducer](https://epicreact.dev/)
- Fullstackopen.com – useReducer

# 🧠 React Memoization: `React.memo`, `useMemo`, `useCallback`

Memoization is a technique to optimize performance by memorizing the results of expensive function calls and returning the cached result when the same inputs occur again. In React, memoization helps to avoid unnecessary re-renders and computations, improving app performance, especially in large applications.

---

## 🔧 `React.memo`

`React.memo` is a higher-order component that prevents unnecessary re-renders of a component if its props have not changed. It compares the previous props and the next props, and if they are the same, the component will not re-render.

---

### Syntax:

```jsx
jsx
CopyEdit
const MemoizedComponent = React.memo(Component);

```

---

### Example:

```jsx
jsx
CopyEdit
import React from 'react';

const ExpensiveComponent = ({ data }) => {
  console.log('Rendering ExpensiveComponent');
  return <div>{data}</div>;
};

const MemoizedExpensiveComponent = React.memo(ExpensiveComponent);

function App() {
  const [count, setCount] = React.useState(0);
  const [data, setData] = React.useState('Some data');

  return (
    <div>
      <MemoizedExpensiveComponent data={data} />
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

In this example, `MemoizedExpensiveComponent` will only re-render when the `data` prop changes, not when `count` changes.

---

### What to do with it:

- ✅ Use `React.memo` to memoize components that receive props and re-render only when those props change.
- ✅ Apply `React.memo` to **functional components** to improve performance in large component trees.

---

## 🔧 `useMemo`

`useMemo` is a React hook used to memoize the result of a computation. It only recomputes the value when one of the dependencies has changed, which helps avoid expensive recalculations on every render.

---

### Syntax:

```jsx
jsx
CopyEdit
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);

```

---

### Example:

```jsx
jsx
CopyEdit
import React, { useMemo, useState } from 'react';

function App() {
  const [count, setCount] = useState(0);

  const expensiveCalculation = useMemo(() => {
    console.log('Calculating...');
    return count * 2;
  }, [count]);

  return (
    <div>
      <p>Expensive calculation: {expensiveCalculation}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

```

In this example, `expensiveCalculation` will only be recomputed when `count` changes, preventing unnecessary recalculations on every render.

---

### What to do with it:

- ✅ Use `useMemo` for expensive computations or complex calculations that do not need to be recomputed on every render.
- ✅ Provide a **dependency array** to `useMemo` to control when the memoized value should be recalculated.

---

## 🔧 `useCallback`

`useCallback` is similar to `useMemo`, but it’s specifically used for memoizing functions. It returns a memoized version of the callback function that only changes if one of its dependencies changes, preventing unnecessary re-creations of the function.

---

### Syntax:

```jsx
jsx
CopyEdit
const memoizedCallback = useCallback(() => { /* callback */ }, [dependencies]);

```

---

### Example:

```jsx
jsx
CopyEdit
import React, { useState, useCallback } from 'react';

function Button({ onClick }) {
  console.log('Button rendered');
  return <button onClick={onClick}>Click me</button>;
}

function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div>
      <Button onClick={handleClick} />
      <p>Count: {count}</p>
    </div>
  );
}

```

In this example, `handleClick` is memoized using `useCallback`, so it won’t be re-created on every render. This can be especially useful when passing callbacks to child components.

---

### What to do with it:

- ✅ Use `useCallback` to memoize callback functions that are passed down to child components to prevent unnecessary re-renders.
- ✅ Use `useCallback` when you want to ensure that the same instance of a function is used unless its dependencies change.

---

## 🔧 When to Use Each:

- **`React.memo`**: Use this to optimize functional components that don’t need to re-render unless their props change.
- **`useMemo`**: Use this to optimize the performance of expensive calculations or complex operations that are dependent on certain variables.
- **`useCallback`**: Use this to memoize functions that are passed down to child components and avoid unnecessary re-creations of those functions on each render.

---

## 📚 If you want to learn more

- React Docs (react.dev) – React.memo
- [EpicReact.dev by Kent C. Dodds – React.memo](https://epicreact.dev/)
- Fullstackopen.com – React.memo

# 📝 Forms with Libraries: `Formik` / `React Hook Form`

Managing forms in React can become complex with validation, error handling, and state management. Form libraries like **Formik** and **React Hook Form** simplify form handling by abstracting common tasks such as validation, form submission, and field management.

---

## 🔧 Formik

`Formik` is a popular library for managing forms in React. It helps with handling form state, validation, and submission in a structured manner. Formik reduces the boilerplate code needed to manage complex forms in React applications.

---

### What is Formik?

Formik provides an easy way to manage form state, validation, and submission. It provides methods to control the form state, handle validation using schemas (often with **Yup**), and provides utilities for error handling.

---

### Syntax:

```jsx
jsx
CopyEdit
import { Formik, Field, Form, ErrorMessage } from 'formik';

<FormikinitialValues={{ name: '' }}
  validate={values => { /* validation logic */ }}
  onSubmit={(values) => { /* form submission logic */ }}
>
  <Form>
    <Field name="name" type="text" />
    <ErrorMessage name="name" component="div" />
    <button type="submit">Submit</button>
  </Form>
</Formik>

```

---

### Example:

```jsx
jsx
CopyEdit
import { Formik, Field, Form, ErrorMessage } from 'formik';

function SignupForm() {
  return (
    <FormikinitialValues={{ name: '', email: '' }}
      validate={(values) => {
        const errors = {};
        if (!values.name) errors.name = 'Required';
        if (!values.email) errors.email = 'Required';
        return errors;
      }}
      onSubmit={(values) => {
        console.log('Form data submitted:', values);
      }}
    >
      <Form>
        <Field name="name" type="text" />
        <ErrorMessage name="name" component="div" />

        <Field name="email" type="email" />
        <ErrorMessage name="email" component="div" />

        <button type="submit">Submit</button>
      </Form>
    </Formik>
  );
}

```

In this example, Formik handles the form state, validation, and submission logic.

---

### What to do with it:

- ✅ Use Formik when your form handling requires validation, error handling, or managing complex form state.
- ✅ Integrate **Yup** for schema-based validation.
- ✅ Leverage Formik’s **Field** and **ErrorMessage** components to simplify form creation and validation error display.

---

## 🔧 React Hook Form

`React Hook Form` is another form handling library that takes advantage of React hooks to handle forms efficiently. It is known for its minimal re-rendering approach and simple API for form validation and submission.

---

### What is React Hook Form?

React Hook Form leverages React hooks (`useState`, `useEffect`) to manage form state and validation. It provides a clean and performant API with minimal re-renders, making it ideal for large forms or apps that need optimal performance.

---

### Syntax:

```jsx
jsx
CopyEdit
import { useForm } from 'react-hook-form';

const { register, handleSubmit, formState: { errors } } = useForm();

<form onSubmit={handleSubmit(onSubmit)}>
  <input {...register('name', { required: 'Name is required' })} />
  {errors.name && <p>{errors.name.message}</p>}
  <button type="submit">Submit</button>
</form>

```

---

### Example:

```jsx
jsx
CopyEdit
import { useForm } from 'react-hook-form';

function SignupForm() {
  const { register, handleSubmit, formState: { errors } } = useForm();

  const onSubmit = (data) => {
    console.log('Form submitted with data:', data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input
        {...register('name', { required: 'Name is required' })}
        placeholder="Name"
      />
      {errors.name && <p>{errors.name.message}</p>}

      <input
        {...register('email', { required: 'Email is required' })}
        placeholder="Email"
      />
      {errors.email && <p>{errors.email.message}</p>}

      <button type="submit">Submit</button>
    </form>
  );
}

```

In this example, `React Hook Form` uses the `register` function to bind inputs, and validation is handled via simple `errors` objects.

---

### What to do with it:

- ✅ Use React Hook Form for minimal re-renders and better performance with large forms.
- ✅ Use the `register` function to register each input field.
- ✅ Take advantage of built-in validation support, or use a schema validation library like **Yup**.

---

## 🔧 Key Differences Between Formik and React Hook Form

1. **Re-rendering**:
    - Formik causes re-renders on form state changes, which can lead to performance issues with large forms.
    - React Hook Form minimizes re-renders, leading to better performance with larger forms.
2. **API**:
    - Formik has a more structured API with `Formik`, `Field`, and `ErrorMessage` components, making it more declarative.
    - React Hook Form provides a simple API focused around `useForm`, `register`, and `handleSubmit`, offering more control over form elements.
3. **Performance**:
    - React Hook Form is known for its better performance due to minimal re-renders and is more suitable for performance-critical apps.
4. **Integration with Schema Validation**:
    - Both Formik and React Hook Form integrate easily with schema-based validation libraries like **Yup**.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Forms
- [EpicReact.dev by Kent C. Dodds – Forms](https://epicreact.dev/)
- Fullstackopen.com – Forms

# 📝 Performance Optimization Basics

React applications can become slow and unresponsive if not optimized correctly. Optimizing the performance of your React app is crucial, especially as your application grows in complexity. Here are the fundamental performance optimization techniques that can help boost the performance of your React application.

---

## 🔧 React Performance Optimization Techniques

---

### 1. **Avoid Re-rendering Unnecessary Components**

React re-renders components by default when their state or props change. However, unnecessary re-renders can lead to performance issues, especially in large applications.

---

### What to do with it:

- ✅ **React.memo**: Wrap components with `React.memo` to memoize them and prevent unnecessary re-renders if the props have not changed.
- ✅ Use the **shouldComponentUpdate** lifecycle method (for class components) to prevent unnecessary updates.
- ✅ Use **useMemo** and **useCallback** hooks to memoize expensive calculations and functions.

---

### Example of `React.memo`:

```jsx
jsx
CopyEdit
const MyComponent = React.memo(({ data }) => {
  console.log('Rendering MyComponent');
  return <div>{data}</div>;
});

```

This ensures `MyComponent` is only re-rendered if `data` changes.

---

### Example of `useMemo`:

```jsx
jsx
CopyEdit
import { useMemo } from 'react';

function ExpensiveComponent({ inputData }) {
  const computedValue = useMemo(() => {
    return expensiveComputation(inputData);
  }, [inputData]); // recompute only when inputData changes

  return <div>{computedValue}</div>;
}

```

---

### 2. **Code-Splitting with React.lazy and Suspense**

**Code-splitting** allows you to load parts of your app on demand, rather than loading the entire app upfront. This improves the initial load time and reduces the size of the JavaScript bundle.

---

### What to do with it:

- ✅ Use **React.lazy** and **Suspense** to load components lazily.
- ✅ Split large third-party libraries or routes into separate chunks for on-demand loading.

---

### Syntax of `React.lazy` and `Suspense`:

```jsx
jsx
CopyEdit
import React, { Suspense, lazy } from 'react';

const MyComponent = lazy(() => import('./MyComponent'));

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <MyComponent />
    </Suspense>
  );
}

```

In this example, `MyComponent` is loaded lazily only when it is needed.

---

### 3. **Use PureComponent or React.memo**

**PureComponent** is a class component that implements `shouldComponentUpdate` with a shallow prop and state comparison. This prevents re-rendering if the props or state haven’t changed.

---

### What to do with it:

- ✅ Use **PureComponent** for class components to avoid unnecessary renders.
- ✅ Use **React.memo** for functional components to achieve similar benefits.

---

### Example of `PureComponent`:

```jsx
jsx
CopyEdit
class MyComponent extends React.PureComponent {
  render() {
    return <div>{this.props.name}</div>;
  }
}

```

---

### 4. **Debounce and Throttle User Input**

If your application reacts to user input frequently (such as typing or scrolling), unnecessary calls to state updates or API requests can degrade performance. **Debouncing** and **throttling** help control the frequency of these updates.

---

### What to do with it:

- ✅ **Debounce** input events to delay the execution until the user stops typing for a specified time.
- ✅ **Throttle** events to limit the number of times a function is called within a given period.

---

### Example of Debouncing with `useEffect`:

```jsx
jsx
CopyEdit
import { useState, useEffect } from 'react';

function SearchInput() {
  const [query, setQuery] = useState('');

  useEffect(() => {
    const timeoutId = setTimeout(() => {
      // Trigger search or API call
      console.log(query);
    }, 500);

    return () => clearTimeout(timeoutId); // Cleanup on unmount or change
  }, [query]);

  return (
    <inputtype="text"
      value={query}
      onChange={(e) => setQuery(e.target.value)}
    />
  );
}

```

---

### 5. **Virtualization for Large Lists**

Rendering a large list of items at once can lead to slow performance. Virtualization allows rendering only the visible items in the list, reducing the number of DOM nodes.

---

### What to do with it:

- ✅ Use **react-window** or **react-virtualized** to optimize large lists.
- ✅ Render only a subset of list items that are in the viewport, saving memory and improving performance.

---

### Example with `react-window`:

```jsx
jsx
CopyEdit
import { FixedSizeList as List } from 'react-window';

function VirtualizedList({ items }) {
  return (
    <Listheight={400}
      itemCount={items.length}
      itemSize={35}
      width={300}
    >
      {({ index, style }) => (
        <div style={style}>{items[index]}</div>
      )}
    </List>
  );
}

```

---

### 6. **Lazy Loading Images and Media**

For pages with many images, it's better to load images only when they are visible in the viewport, reducing the initial page load time.

---

### What to do with it:

- ✅ Use the **loading="lazy"** attribute in `<img>` tags to lazy-load images.
- ✅ Use libraries like **react-lazyload** to control when images or other media elements should load.

---

### Example of Lazy Loading Images:

```jsx
jsx
CopyEdit
<img src="image.jpg" alt="Lazy loaded" loading="lazy" />

```

This ensures the image is loaded only when it enters the viewport.

---

### 7. **Memoize Functions with `useCallback`**

If you pass functions as props to child components, they may cause unnecessary re-renders. Memoizing those functions can prevent this.

---

### What to do with it:

- ✅ Use **useCallback** to memoize functions and avoid unnecessary re-renders.

---

### Example of `useCallback`:

```jsx
jsx
CopyEdit
import { useState, useCallback } from 'react';

function ParentComponent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return <ChildComponent onClick={handleClick} />;
}

function ChildComponent({ onClick }) {
  return <button onClick={onClick}>Increment</button>;
}

```

---

## 📚 If you want to learn more

- React Docs (react.dev) – Optimizing Performance
- [EpicReact.dev by Kent C. Dodds – Performance](https://epicreact.dev/)
- Fullstackopen.com – Performance

# 📝 Code Splitting & Lazy Loading (React.lazy, Suspense)

Code splitting is a technique that allows you to split your bundle into smaller chunks and only load the necessary code when needed, improving the performance of your React app. With **React.lazy** and **Suspense**, you can implement lazy loading for your components and routes.

---

## 🔧 Code Splitting & Lazy Loading Overview

---

### **What is Code Splitting?**

**Code splitting** is the process of dividing your application into smaller, more manageable chunks. Instead of loading the entire JavaScript bundle on the initial page load, code splitting loads only the required code for the current page or view.

---

### **What is Lazy Loading?**

**Lazy loading** is the practice of deferring the loading of non-essential resources (like images or components) until they are actually needed (usually when they are in the viewport or accessed by the user). This can significantly reduce the initial load time of your application.

---

### **React.lazy & Suspense**

React's `React.lazy` and `Suspense` are built-in tools for implementing lazy loading in your React app. `React.lazy` is used to dynamically import components, while `Suspense` is used to manage the loading state while the component is being loaded.

---

## 🔧 How to Use React.lazy and Suspense

---

### 1. **React.lazy**

`React.lazy` allows you to dynamically import components when they are required, rather than loading them upfront.

---

### Syntax:

```jsx
jsx
CopyEdit
const Component = React.lazy(() => import('./Component'));

```

This syntax ensures that the component is loaded lazily when it’s rendered.

---

### Example:

```jsx
jsx
CopyEdit
import React, { Suspense } from 'react';

// Lazily load the Component
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <div>
      <h1>Welcome to my App</h1>
      {/* Suspense handles loading state */}
      <Suspense fallback={<div>Loading...</div>}>
        <LazyComponent />
      </Suspense>
    </div>
  );
}

export default App;

```

In this example:

- The `LazyComponent` is loaded lazily only when it is needed.
- The `Suspense` component wraps the lazy-loaded component and provides a fallback UI (e.g., a loading spinner or text) until the component is fully loaded.

---

### 2. **Suspense**

`Suspense` is a wrapper component used to handle loading states when working with `React.lazy` or asynchronous data fetching. It shows the `fallback` content (like a loading spinner) until the component is ready to render.

---

### Syntax:

```jsx
jsx
CopyEdit
<Suspense fallback={<div>Loading...</div>}>
  <Component />
</Suspense>

```

Here, `fallback` defines what to display while the component is being loaded.

---

### **Example of Lazy Loading with Suspense:**

```jsx
jsx
CopyEdit
import React, { Suspense } from 'react';

// Lazily load components
const HomePage = React.lazy(() => import('./HomePage'));
const AboutPage = React.lazy(() => import('./AboutPage'));

function App() {
  return (
    <div>
      <h1>My React App</h1>
      <Suspense fallback={<div>Loading Home...</div>}>
        <HomePage />
      </Suspense>
      <Suspense fallback={<div>Loading About...</div>}>
        <AboutPage />
      </Suspense>
    </div>
  );
}

export default App;

```

In this example:

- The `HomePage` and `AboutPage` components are lazily loaded.
- While each page is loading, a loading text is displayed in place of the content.

---

## 🛠️ Best Practices for Code Splitting & Lazy Loading

---

### 1. **Split Code Based on Routes (Route-based Splitting)**

For large apps, you can split your code based on routes so that only the components needed for the current route are loaded.

---

### Example of Route-based Lazy Loading with React Router:

```jsx
jsx
CopyEdit
import React, { Suspense } from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

// Lazy load components for routes
const Home = React.lazy(() => import('./Home'));
const About = React.lazy(() => import('./About'));

function App() {
  return (
    <Router>
      <Suspense fallback={<div>Loading...</div>}>
        <Switch>
          <Route path="/" exact component={Home} />
          <Route path="/about" component={About} />
        </Switch>
      </Suspense>
    </Router>
  );
}

export default App;

```

In this case, the `Home` and `About` components are only loaded when the user navigates to their respective routes.

---

### 2. **Minimize the Number of Lazy Loaded Components**

While lazy loading is beneficial, overusing it can lead to performance issues due to the overhead of additional requests. Only lazy-load components that are heavy or not immediately necessary for the user experience.

---

### 3. **Combine Multiple Components into One Lazy Load**

Instead of lazy-loading every small component individually, consider combining multiple smaller components into one larger, lazy-loaded chunk.

---

### Example:

```jsx
jsx
CopyEdit
const LazyComponents = React.lazy(() => import('./LargeComponentBundle'));

```

This approach can reduce the overhead of multiple lazy loading operations.

---

### 4. **Use `Suspense` with Data Fetching (React 18+)**

In React 18, you can also use `Suspense` for data fetching, meaning you can wrap async data-fetching logic in a `Suspense` component to improve performance.

---

### Example of Suspense with Data Fetching:

```jsx
jsx
CopyEdit
import React, { Suspense } from 'react';

function fetchData() {
  return new Promise(resolve => setTimeout(() => resolve('Data Loaded'), 2000));
}

const DataComponent = React.lazy(() =>
  fetchData().then(data => ({ default: () => <div>{data}</div> }))
);

function App() {
  return (
    <div>
      <h1>Suspense with Data Fetching</h1>
      <Suspense fallback={<div>Loading data...</div>}>
        <DataComponent />
      </Suspense>
    </div>
  );
}

export default App;

```

---

## 📚 If you want to learn more

- React Docs (react.dev) – Code-Splitting
- [EpicReact.dev by Kent C. Dodds – Code Splitting](https://epicreact.dev/)
- Fullstackopen.com – Code-Splitting

# 📝 Error Handling with Suspense (Future)

React's **Suspense** is not only useful for lazy loading but also plays a key role in error boundaries, providing a way to gracefully handle errors in components that are being lazily loaded or have asynchronous operations.

While error boundaries have been traditionally used for class components, React introduced new patterns in **Suspense** and **React 18** for handling errors in asynchronous code, including **data fetching** and **lazy-loaded components**.

---

## 🔧 Error Handling in React Suspense

---

### **What is Error Handling in Suspense?**

In **React 18** and beyond, **Suspense** is being expanded to handle asynchronous rendering, including **error boundaries** for lazy-loaded components and async data fetching. React will catch any errors in lazy-loaded components or during async operations, and allow you to display a fallback UI, rather than causing the entire app to crash.

---

### **Error Boundaries with Suspense**

React provides a way to catch errors in any components wrapped inside `Suspense` by using **Error Boundaries**. This allows you to define a fallback UI in case any error occurs while rendering or loading a component.

---

## 🔧 How to Handle Errors with Suspense

---

### 1. **Using an Error Boundary for Suspense**

React provides a special component called **ErrorBoundary** that allows you to catch JavaScript errors in any part of the component tree. You can use it to display a fallback UI if an error is thrown during the rendering of a lazy-loaded component.

---

### Example:

```jsx
jsx
CopyEdit
import React, { Suspense } from 'react';

// Error Boundary to catch errors
class ErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error('Error caught by boundary:', error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Something went wrong!</h1>;
    }
    return this.props.children;
  }
}

// Lazily load component
const LazyComponent = React.lazy(() => import('./LazyComponent'));

function App() {
  return (
    <div>
      <h1>Welcome to my App</h1>
      {/* Error boundary for lazy-loaded component */}
      <ErrorBoundary>
        <Suspense fallback={<div>Loading...</div>}>
          <LazyComponent />
        </Suspense>
      </ErrorBoundary>
    </div>
  );
}

export default App;

```

---

In this example:

- If the `LazyComponent` fails to load, the `ErrorBoundary` will catch the error and display a fallback message (`Something went wrong!`).
- You can define custom error handling logic in the `componentDidCatch` method.

---

### 2. **Error Boundaries for Data Fetching**

For async operations, such as data fetching, React 18 introduced the idea of wrapping `Suspense` with **Error Boundaries** to handle errors that occur during data fetching. This can be particularly useful when you're using `React.lazy` or `Suspense` for data fetching with external APIs or services.

---

### Example:

```jsx
jsx
CopyEdit
import React, { Suspense, useState, useEffect } from 'react';

// Async component that simulates data fetching
const fetchData = async () => {
  const response = await fetch('https://api.example.com/data');
  if (!response.ok) {
    throw new Error('Failed to fetch data');
  }
  return response.json();
};

// Data Fetching Component
const DataComponent = React.lazy(() => {
  return fetchData().then(data => ({
    default: () => <div>{data}</div>,
  }));
});

class DataErrorBoundary extends React.Component {
  state = { hasError: false };

  static getDerivedStateFromError(error) {
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    console.error('Error caught by boundary:', error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h1>Failed to load data!</h1>;
    }
    return this.props.children;
  }
}

function App() {
  return (
    <div>
      <h1>Data Fetching with Suspense</h1>
      <DataErrorBoundary>
        <Suspense fallback={<div>Loading data...</div>}>
          <DataComponent />
        </Suspense>
      </DataErrorBoundary>
    </div>
  );
}

export default App;

```

In this example:

- The `DataComponent` simulates data fetching, and if there's an error while fetching the data, the `DataErrorBoundary` catches the error and displays an error message (`Failed to load data!`).

---

## 🛠️ Best Practices for Error Handling with Suspense

---

### 1. **Always Wrap Suspense with Error Boundaries**

It's essential to wrap your `Suspense` components in an **ErrorBoundary** to handle any errors that might occur when lazy-loaded components or data fetching fails.

---

### 2. **Provide Fallback UI for Loading States**

Always use a fallback UI (like a loading spinner or loading text) within the `Suspense` component. This ensures the user has visual feedback while waiting for the content to load.

---

### 3. **Handle Specific Error Cases Gracefully**

Use custom error messages or fallbacks for different types of errors. For example, show a different error message for network failures versus component rendering failures.

---

### 4. **Gracefully Handle Asynchronous Data Fetching Errors**

When dealing with data fetching, especially when combined with `Suspense`, ensure you handle possible errors during fetching (e.g., no network, invalid API response). This helps you provide a better user experience in case of failures.

---

### 5. **Log Errors for Debugging**

Always log errors (either to the console or a logging service) in the `componentDidCatch` method of your `ErrorBoundary` to capture insights into what went wrong.

---

## 📚 If you want to learn more

- React Docs (react.dev) – Error Boundaries
- [EpicReact.dev by Kent C. Dodds – Error Boundaries](https://epicreact.dev/)
- Fullstackopen.com – Error Handling

# 📝 Concurrent Features (StartTransition, useDeferredValue)

React's **Concurrent Mode** brings new features that help improve the performance of React applications by allowing non-urgent updates to be deferred, giving more priority to the critical parts of the UI. Two such features are **`startTransition`** and **`useDeferredValue`**.

These features are used to optimize rendering performance by allowing React to handle updates more efficiently and asynchronously.

---

## 🔧 `startTransition`

---

### **What is `startTransition`?**

`startTransition` is a new API introduced in React's **Concurrent Mode** that allows you to mark certain state updates as **non-urgent**. By marking these updates, React can defer them and work on higher-priority updates first, preventing UI jank and ensuring that the app remains responsive.

---

### **Syntax**

```jsx
javascript
CopyEdit
import { startTransition } from 'react';

startTransition(() => {
  // Update state that is non-urgent
});

```

---

### **Example**

```jsx
jsx
CopyEdit
import React, { useState, useTransition } from 'react';

function MyComponent() {
  const [isPending, startTransition] = useTransition();
  const [value, setValue] = useState('');

  const handleChange = (e) => {
    const newValue = e.target.value;
    // Start the transition to update the state
    startTransition(() => {
      setValue(newValue);
    });
  };

  return (
    <div>
      <input value={value} onChange={handleChange} />
      {isPending && <span>Loading...</span>}
    </div>
  );
}

```

---

### **What to do with it**

- Use `startTransition` to wrap state updates that are not time-sensitive.
- Use it to **avoid blocking UI updates** and allow React to prioritize critical updates, such as user interactions or visible content.
- Ideal for **heavy rendering operations** or when there is a delay in non-essential updates (e.g., search filtering).

---

### **What not to do with it**

- Don’t use it for critical updates or when you want the UI to update immediately.
- Avoid wrapping state updates that need to reflect immediately (e.g., user input in forms).
- Don't wrap every state update in `startTransition`—only use it for **non-urgent updates**.

---

### **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Concurrent Mode → startTransition

---

## 🔧 `useDeferredValue`

---

### **What is `useDeferredValue`?**

`useDeferredValue` is a hook that allows you to defer an update to a state value, providing the ability to keep the UI responsive by delaying non-essential updates. It's particularly useful for cases where you are updating a value based on user input, but don't need to immediately render the result of that input.

---

### **Syntax**

```jsx
javascript
CopyEdit
import { useDeferredValue } from 'react';

const deferredValue = useDeferredValue(value);

```

---

### **Example**

```jsx
jsx
CopyEdit
import React, { useState, useDeferredValue } from 'react';

function SearchComponent() {
  const [searchTerm, setSearchTerm] = useState('');
  const deferredSearchTerm = useDeferredValue(searchTerm);

  return (
    <div>
      <inputtype="text"
        value={searchTerm}
        onChange={(e) => setSearchTerm(e.target.value)}
        placeholder="Search"
      />
      <div>
        <h2>Search Results for: {deferredSearchTerm}</h2>
        {/* Render search results here */}
      </div>
    </div>
  );
}

```

---

### **What to do with it**

- Use `useDeferredValue` when you want to **defer non-urgent updates** (like rendering search results) while keeping the UI responsive.
- It helps in scenarios like **live search** or **infinite scroll**, where the input is constantly changing, but the UI should prioritize showing user input and delay displaying the results.
- Perfect for improving user experience by preventing UI blocking on slow or costly operations.

---

### **What not to do with it**

- Avoid using it when you need to show the updated state immediately.
- Don't use it for state updates that **should not be deferred**, such as user-driven interactions (e.g., button clicks, form submissions).
- Don’t use it in a way that can lead to unexpected UI delays, especially for critical rendering operations.

---

### **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Concurrent Mode → useDeferredValue

---

## 🛠️ Best Practices for Concurrent Features

---

### 1. **StartTransition for Non-Urgent Updates**

Use `startTransition` for **non-urgent UI updates** to allow React to keep the UI responsive and prioritize important updates.

---

### 2. **Use `useDeferredValue` for Delaying Non-Critical UI Changes**

`useDeferredValue` is best suited for cases like **live search** or **scrolling** where non-urgent updates don’t need to block the UI from updating with new user input.

---

### 3. **Keep Critical Updates Unwrapped**

Don’t wrap user-critical updates, like form submissions, in `startTransition`. These updates should be immediate to provide a smooth experience.

---

### 4. **Test for User Experience**

Always test how the deferral of updates affects the overall user experience. You want to make sure it **doesn’t create undesirable delays** in rendering essential content.

# 📝 Testing React (Jest, React Testing Library)

Testing is a critical part of the development process. **Jest** and **React Testing Library** are the most popular tools for testing React applications. Together, they allow developers to write unit and integration tests for their React components, ensuring they work as expected in different scenarios.

---

## 🔧 **Jest**

---

### **What is Jest?**

**Jest** is a JavaScript testing framework maintained by Facebook. It's designed to work well with React but can be used to test any JavaScript codebase. Jest provides an easy-to-use API for writing tests, running assertions, and mocking dependencies.

---

### **Syntax**

```jsx
javascript
CopyEdit
import { render, screen } from '@testing-library/react';
import { MyComponent } from './MyComponent';

test('renders component correctly', () => {
  render(<MyComponent />);
  expect(screen.getByText('Hello World')).toBeInTheDocument();
});

```

---

### **Example**

```jsx
jsx
CopyEdit
import React from 'react';

function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

export default Greeting;

```

Test for the `Greeting` component:

```jsx
javascript
CopyEdit
import { render, screen } from '@testing-library/react';
import Greeting from './Greeting';

test('renders correct greeting message', () => {
  render(<Greeting name="John" />);
  const greeting = screen.getByText(/Hello, John!/i);
  expect(greeting).toBeInTheDocument();
});

```

---

### **What to do with it**

- Use Jest to write unit tests for your React components, ensuring that the components behave as expected in various situations.
- Jest is great for testing JavaScript logic, such as functions, modules, and APIs.
- It has built-in mocking capabilities to isolate code during tests.
- Utilize Jest’s **snapshot testing** for rendering UI to compare changes over time.

---

### **What not to do with it**

- Don't overuse snapshot testing for every single change. It can become hard to manage as your app grows.
- Avoid writing tests for every minor behavior. Focus on high-value tests that ensure your app works as expected.
- Don’t test for implementation details; focus on the **behavior** of your components.

---

### **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Testing → Jest

---

## 🔧 **React Testing Library**

---

### **What is React Testing Library?**

**React Testing Library (RTL)** is a set of helpers for testing React components in a way that mirrors how users interact with your application. It encourages testing components as a user would, focusing on **what the component renders**, rather than testing implementation details.

---

### **Syntax**

```jsx
javascript
CopyEdit
import { render, screen, fireEvent } from '@testing-library/react';
import MyComponent from './MyComponent';

test('handles button click', () => {
  render(<MyComponent />);
  fireEvent.click(screen.getByText('Click Me'));
  expect(screen.getByText('Button Clicked')).toBeInTheDocument();
});

```

---

### **Example**

```jsx
jsx
CopyEdit
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;

```

Test for the `Counter` component:

```jsx
javascript
CopyEdit
import { render, screen, fireEvent } from '@testing-library/react';
import Counter from './Counter';

test('increments count when button is clicked', () => {
  render(<Counter />);
  const button = screen.getByText('Increment');
  fireEvent.click(button);
  const count = screen.getByText('Count: 1');
  expect(count).toBeInTheDocument();
});

```

---

### **What to do with it**

- Use RTL to focus on testing **user interactions**, such as clicks, form submissions, and keyboard events.
- Test the **UI output** and how components **render and behave**, rather than testing internal logic.
- RTL encourages testing based on the DOM structure, like querying elements using `getByText`, `getByRole`, or `getByLabelText`.
- Write tests that simulate how users would interact with the app.

---

### **What not to do with it**

- Don’t test implementation details like internal state or component methods directly. Test **user-facing functionality**.
- Avoid using `find` and `query` methods unnecessarily. Stick to the `getBy` methods for more predictable tests.
- Don’t overmock or stub too much. Let the components and their dependencies render and behave as they normally would.

---

### **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Testing → React Testing Library

---

## 🛠️ Best Practices for Testing React

---

### 1. **Test User Behavior, Not Implementation**

When writing tests, always aim to test the **behavior** of your components from the user's perspective, not how the component works internally. This is the core philosophy of React Testing Library.

---

### 2. **Avoid Testing Implementation Details**

Don’t test the internal state of components, function calls, or private methods. Focus on testing what’s rendered on the screen and how it behaves in response to user actions.

---

### 3. **Test Edge Cases and Error Handling**

Cover edge cases in your tests, such as invalid inputs, missing data, or server errors, to ensure your application behaves correctly in all situations.

---

### 4. **Use `fireEvent` and `userEvent` for Interactions**

When simulating user interactions, use `fireEvent` (from RTL) for simple interactions like clicks, or use `userEvent` (which mimics more realistic user behavior) for actions like typing, clicking, etc.

---

### 5. **Leverage Jest Mocks and Spies**

Use Jest's built-in mocking and spying functionality to test how components interact with APIs, external libraries, or other components.

---

### 6. **Keep Tests Simple and Focused**

Tests should be easy to understand and maintain. Focus on one behavior per test and keep them concise.

---

### 7. **Write Tests to Reflect User Stories**

Write tests to reflect the **user stories** or features of your application. This ensures your tests stay relevant to the core use cases and user interactions.

---

### 8. **Use Snapshot Testing with Care**

While snapshot testing can be useful for ensuring consistent rendering, avoid overusing it. Focus on testing **critical functionality** and UI components rather than relying solely on snapshots.

---

### 9. **Test Async Code Effectively**

React Testing Library has built-in support for testing asynchronous code with `waitFor`, `findBy`, and `act`. Use these to test behavior that involves API calls or delayed updates.

# 📝 Higher-Order Components (HOCs)

A **Higher-Order Component (HOC)** is a function that takes a component and returns a new component with additional functionality. HOCs are a powerful pattern in React for reusing component logic, abstracting common behavior, and enhancing components with additional features.

---

## 🔧 **Definition**

A **Higher-Order Component (HOC)** is a function that accepts a component and returns a new component with additional props or logic. It's a pattern used for **code reuse** in React, allowing you to share logic across multiple components.

---

## 🔧 **Syntax**

```jsx
javascript
CopyEdit
function withExtraProps(WrappedComponent) {
  return function EnhancedComponent(props) {
    return <WrappedComponent {...props} extraProp="some value" />;
  };
}

```

---

## 🔧 **Example**

Let's say we have a simple `User` component, and we want to add some additional props to it using an HOC.

```jsx
jsx
CopyEdit
import React from 'react';

function User(props) {
  return (
    <div>
      <h2>{props.name}</h2>
      <p>{props.age}</p>
      {props.extraProp && <p>{props.extraProp}</p>}
    </div>
  );
}

function withAgeCheck(WrappedComponent) {
  return function EnhancedComponent(props) {
    const ageValid = props.age >= 18;
    return <WrappedComponent {...props} isAdult={ageValid} />;
  };
}

const EnhancedUser = withAgeCheck(User);

function App() {
  return <EnhancedUser name="John Doe" age={20} />;
}

export default App;

```

In this example:

- `User` is a basic component.
- `withAgeCheck` is the HOC that adds a new prop `isAdult`.
- `EnhancedUser` is the result of applying the HOC to the `User` component.

---

## 🔧 **What to do with it**

- Use HOCs to **re-usable logic** across different components, such as authentication, theme management, or lifecycle handling.
- Wrap components to inject additional behavior or modify their props.
- Combine multiple HOCs to enhance a component with different functionalities.
- Use HOCs to provide **conditional rendering** (e.g., showing different UI based on user roles, permissions, etc.).

---

## 🔧 **What not to do with it**

- Avoid **overusing HOCs**, as it can lead to complicated and hard-to-manage code. Consider using **hooks** for logic that can be reused.
- Don’t pass non-deterministic props (like random values or things dependent on execution order) through HOCs as it can lead to bugs or unexpected behavior.
- Avoid nesting HOCs too deeply, as it can make the component tree more difficult to follow and debug.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Advanced Guides → HOC
- "EpicReact.dev by Kent C. Dodds" – "React Patterns"
- "Fullstackopen.com" – "React HOCs" (if available)

---

## 🛠️ **Best Practices for Using HOCs**

1. **Keep HOCs Pure**
    
    Make sure the HOC does not mutate or modify the props directly. It should only **enhance** or **add** functionality to the component without causing side effects.
    
2. **Use Descriptive Names**
    
    Name your HOCs in a way that clearly describes what they do. For example, `withAuthorization` or `withTheme`.
    
3. **Avoid Prop Conflicts**
    
    When passing props to a wrapped component, ensure that the props don't conflict with the props already defined in the HOC. It's common to use **prop name prefixes** like `wrappedComponentProp` or `hocProp` to avoid naming collisions.
    
4. **Refactor to Hooks Where Possible**
    
    While HOCs are great for code reuse, hooks provide a more modern and often cleaner approach. Consider refactoring HOCs into hooks when possible.
    
5. **Consider Performance**
    
    Since HOCs create new components, they can affect performance. Try to avoid excessive re-renders or unnecessary wrapping of components. Use memoization techniques like `React.memo` or `useMemo` to optimize performance if needed.
    
6. **Don't Use HOCs for State Management**
    
    While HOCs can manage logic and pass props, it's better to use **context** or **state management libraries** like Redux for managing complex state across components.
    

# 📝 Render Props Pattern

The **Render Props** pattern is a technique for sharing code between components using a prop that is a function. The function can be used to render content dynamically. This allows components to share logic without having to directly modify their behavior or structure.

---

## 🔧 **Definition**

The **Render Props** pattern involves passing a function as a prop to a component. This function is then invoked within the component to return content or elements, allowing for **dynamic rendering** based on logic or state.

---

## 🔧 **Syntax**

```jsx
javascript
CopyEdit
function MyComponent({ render }) {
  return <div>{render()}</div>;
}

function App() {
  return <MyComponent render={() => <h1>Hello, World!</h1>} />;
}

```

In this example:

- `MyComponent` accepts a `render` function as a prop.
- The `render` function is invoked inside `MyComponent` to render the content dynamically.

---

## 🔧 **Example**

Here's a more practical example, where the Render Props pattern is used to share state logic between components.

```jsx
jsx
CopyEdit
import React, { useState } from 'react';

function MouseTracker({ render }) {
  const [mousePosition, setMousePosition] = useState({ x: 0, y: 0 });

  const handleMouseMove = (event) => {
    setMousePosition({ x: event.clientX, y: event.clientY });
  };

  return (
    <div onMouseMove={handleMouseMove}>
      {render(mousePosition)}
    </div>
  );
}

function App() {
  return (
    <MouseTrackerrender={({ x, y }) => (
        <p>
          Mouse position: {x}, {y}
        </p>
      )}
    />
  );
}

export default App;

```

In this example:

- `MouseTracker` is the component that tracks the mouse position.
- It passes a `render` prop to render the mouse position dynamically.
- The `render` prop receives the mouse position and renders it inside the `App` component.

---

## 🔧 **What to do with it**

- Use the **Render Props** pattern when you want to **share behavior** between components without directly modifying them.
- Leverage this pattern for **stateful logic** that can be shared across multiple components.
- Use it when you want to **inject dynamic content** or modify rendering behavior based on component state or props.
- Use render props for creating **reusable UI patterns** (e.g., handling mouse movements, key presses, etc.).

---

## 🔧 **What not to do with it**

- Don’t overuse render props for basic static content. For simple rendering, it's usually better to use **standard component composition** or **children props**.
- Avoid passing a new function as the render prop on every render, as this can cause unnecessary re-renders. Try to **memoize** functions when possible to avoid performance issues.
- Don’t mix render props with other patterns (like HOCs or Context API) in a way that makes the code harder to understand or maintain.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Advanced Guides → Render Props
- "EpicReact.dev by Kent C. Dodds" – "React Patterns"
- "Fullstackopen.com" – "React Patterns" (if available)

---

## 🛠️ **Best Practices for Using Render Props**

1. **Keep It Simple**
    
    When using render props, try to keep the logic within the function clean and simple. Avoid over-complicating the components with too many nested render props.
    
2. **Use Descriptive Names for Render Props**
    
    Instead of just using `render`, give the function prop a descriptive name, such as `children`, `renderContent`, or `renderFooter`, to make the code more readable and understandable.
    
3. **Memoize Render Props**
    
    To avoid unnecessary re-renders, memoize render functions that are passed as props. You can use `useCallback` or `React.memo` to avoid passing new functions on every render.
    
4. **Avoid Prop Drilling**
    
    If you find that you’re passing render props through many levels of components, it may be worth considering using **Context** or **state management libraries** instead of relying too heavily on render props.
    
5. **Keep UI and Logic Separate**
    
    While render props allow for dynamic rendering, be cautious not to mix too much **business logic** with rendering logic. Keep rendering as declarative and simple as possible.
    

# 📝 Compound Components

The **Compound Components** pattern is a technique in React where you create a set of components that work together to form a complete UI component. It allows for greater flexibility and **explicit control** over the shared state between the components, while still maintaining a clean API for developers.

---

## 🔧 **Definition**

**Compound Components** allow multiple components to work together as a cohesive unit, while keeping the logic and state centralized. The parent component holds the shared state and passes it down to the child components. The child components then interact with the shared state in a controlled manner, creating a more flexible and customizable UI.

---

## 🔧 **Syntax**

Here's an example of how Compound Components are structured:

```jsx
javascript
CopyEdit
function ParentComponent() {
  const [state, setState] = useState(false);

  return (
    <div>
      <ChildComponent1 state={state} />
      <ChildComponent2 setState={setState} />
    </div>
  );
}

```

In this example, `ParentComponent` holds the shared state (`state`) and passes it to its children (`ChildComponent1` and `ChildComponent2`) to work together.

---

## 🔧 **Example**

Here’s a practical example where we create a **Tab system** with compound components:

```jsx
jsx
CopyEdit
import React, { useState } from 'react';

function Tabs({ children }) {
  const [activeTab, setActiveTab] = useState(0);

  return (
    <div>
      {React.Children.map(children, (child, index) => {
        return React.cloneElement(child, {
          isActive: activeTab === index,
          onClick: () => setActiveTab(index),
        });
      })}
    </div>
  );
}

function TabList({ children }) {
  return <div>{children}</div>;
}

function Tab({ isActive, onClick, children }) {
  return (
    <button onClick={onClick} style={{ fontWeight: isActive ? 'bold' : 'normal' }}>
      {children}
    </button>
  );
}

function TabPanel({ isActive, children }) {
  return isActive ? <div>{children}</div> : null;
}

function App() {
  return (
    <Tabs>
      <TabList>
        <Tab>Tab 1</Tab>
        <Tab>Tab 2</Tab>
        <Tab>Tab 3</Tab>
      </TabList>
      <TabPanel isActive={true}>Content for Tab 1</TabPanel>
      <TabPanel isActive={false}>Content for Tab 2</TabPanel>
      <TabPanel isActive={false}>Content for Tab 3</TabPanel>
    </Tabs>
  );
}

export default App;

```

In this example:

- `Tabs` is the parent component, controlling the active tab state.
- `TabList` and `TabPanel` are the compound components that render the individual tabs and their respective content.
- `Tab` is a button that changes the active tab when clicked.
- `TabPanel` shows the content for the active tab.

---

## 🔧 **What to do with it**

- Use **Compound Components** when you need multiple components to **work together** with shared state but want to keep the API clean.
- Use this pattern when you need **flexibility** in how components interact, such as building complex forms, tab systems, accordions, or modal dialogs.
- Use compound components to **keep the parent in control** of the shared state while allowing children to focus on the specific behavior they manage.
- This pattern provides a natural way to implement **stateful behavior** without resorting to prop drilling.

---

## 🔧 **What not to do with it**

- Don’t overuse compound components for very simple scenarios. If the components are too simple or static, consider using regular parent-child composition instead.
- Avoid **tight coupling** of the components, as this can make it hard to reuse them outside the context of the parent. Keep each compound component modular where possible.
- Be cautious of **performance issues** when using this pattern with many nested components. Optimize using **memoization** techniques like `React.memo` to avoid unnecessary re-renders.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Advanced Guides → Compound Components
- "EpicReact.dev by Kent C. Dodds" – "Patterns"
- "Fullstackopen.com" – "Advanced React Patterns"

---

## 🛠️ **Best Practices for Using Compound Components**

1. **State in Parent**
    
    The **parent component** should manage the shared state and pass it down to child components. This provides **centralized control** over the state and makes it easier to manage and modify.
    
2. **Descriptive Props**
    
    Use **descriptive prop names** to clearly indicate the role of each child component. For example, use `isActive`, `onClick`, `activeTab`, etc., to provide a clear interface to the parent.
    
3. **Flexibility**
    
    Allow children to receive props that provide flexibility, like whether or not they are **active**, **expanded**, or **visible**. This ensures that compound components can be reused in various contexts.
    
4. **Composition Over Inheritance**
    
    Like other React patterns, prefer **composition** over **inheritance**. This allows for greater flexibility and reusability of components, especially in different layouts or use cases.
    
5. **Avoid Over-Complexity**
    
    While compound components can add powerful flexibility, they can also become difficult to maintain if overused. Keep the number of components within a reasonable limit to avoid confusion and ensure ease of maintenance.
    

# 📝 Controlled vs Uncontrolled Components (Deep Dive)

In React, managing form elements can be done in two primary ways: **Controlled Components** and **Uncontrolled Components**. Understanding the difference between these two is crucial for building robust, predictable, and easy-to-maintain applications.

---

## 🔧 **Definition**

- **Controlled Components**: A controlled component is one where form data (input values) is **controlled by React state**. The state of the form is stored in the component’s state, and every change in the input is handled by React's state and event handlers.
- **Uncontrolled Components**: An uncontrolled component is one where form data is handled by the **DOM** itself, not React. Instead of using React state to store the input data, you use **refs** to directly access the DOM elements, and the input value is updated by the user.

---

## 🔧 **Syntax**

### Controlled Component Example

```jsx
jsx
CopyEdit
import React, { useState } from 'react';

function ControlledForm() {
  const [inputValue, setInputValue] = useState('');

  const handleChange = (e) => {
    setInputValue(e.target.value);
  };

  return (
    <form>
      <inputtype="text"
        value={inputValue}
        onChange={handleChange}
      />
    </form>
  );
}

```

In this example, `inputValue` is part of the React component's state, and its value is updated via the `onChange` event handler.

### Uncontrolled Component Example

```jsx
jsx
CopyEdit
import React, { useRef } from 'react';

function UncontrolledForm() {
  const inputRef = useRef();

  const handleSubmit = (e) => {
    e.preventDefault();
    console.log(inputRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input ref={inputRef} type="text" />
      <button type="submit">Submit</button>
    </form>
  );
}

```

In this example, the input value is **not controlled by React state**. Instead, `inputRef` is used to directly reference the DOM element, and the value is accessed via `inputRef.current.value`.

---

## 🔧 **What to do with it**

### When to use **Controlled Components**:

1. **Predictable behavior**: Use controlled components when you need the input value to be tied to the React state. This provides **predictable behavior** and better **debugging** capabilities.
2. **Form validation**: If you need real-time form validation, controlled components are better as you can easily check the input values and display validation messages.
3. **Complex logic**: Use controlled components when you need to implement complex form logic, like enabling/disabling submit buttons based on input or dynamically updating other form fields based on the state.
4. **Global state management**: If you need the form data to be part of a larger state management system (like Redux or Context API), controlled components are preferable.

### When to use **Uncontrolled Components**:

1. **Simple forms**: If your form doesn't need to be tightly bound to React's state or if you only need to collect values without dynamic interaction, uncontrolled components are simpler and more efficient.
2. **Performance**: In cases where you don’t need frequent re-renders (for example, in large forms or inputs that don’t need validation), uncontrolled components can improve performance.
3. **Interfacing with non-React code**: If you need to interface with third-party libraries or APIs that require direct DOM manipulation, uncontrolled components can be useful.

---

## 🔧 **What not to do with it**

### What not to do with **Controlled Components**:

1. **Overuse for simple inputs**: Don’t use controlled components for every input if there is no need for state management. It could lead to unnecessary complexity and performance issues.
2. **Forget cleanup**: When using controlled components, remember to clean up event handlers and state changes, especially for dynamic forms.
3. **Avoid deep nesting**: Don’t excessively nest controlled components if they don’t need to be controlled. Keep it simple to avoid unneeded overhead.

### What not to do with **Uncontrolled Components**:

1. **Mixing uncontrolled and controlled inputs**: Don’t mix controlled and uncontrolled components within the same form without careful management. This can lead to inconsistent behavior and difficult-to-debug issues.
2. **Lack of validation**: Since uncontrolled components don’t have state tracking, you may miss real-time form validation or other input-related state checks.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Forms → Controlled Components
- "EpicReact.dev by Kent C. Dodds" – "Forms"
- "Fullstackopen.com" – "React Forms and State"

---

## 🛠️ **Best Practices for Controlled Components**

1. **Avoid unnecessary re-renders**: If you are dealing with complex forms, use techniques like `React.memo`, `useCallback`, or `useReducer` to avoid unnecessary re-renders.
2. **Debounce inputs**: For performance-heavy inputs (like search bars), use **debouncing** to prevent unnecessary updates on every keystroke.
3. **Simplify form logic**: For simple forms, use controlled components sparingly. It’s better to use **local state** or **Context API** if the form is part of a larger application.

## 🛠️ **Best Practices for Uncontrolled Components**

1. **Use refs carefully**: Always ensure that you manage and access refs correctly, especially when interacting with the DOM.
2. **Avoid uncontrolled components for complex forms**: If your form has complex interactions or needs validation, use controlled components for better control and maintainability.
3. **Optimize with lazy loading**: For large forms, consider **lazy loading** or **dynamic rendering** of form sections to improve performance.

# 📝 Accessibility in React

Accessibility (often abbreviated as **a11y**) is crucial for making web applications usable by people with disabilities. In React, ensuring accessibility involves a set of best practices and tools to create applications that work well with assistive technologies like screen readers, keyboard navigation, and more.

---

## 🔧 **Definition**

**Accessibility in React** refers to the practice of building web applications that are usable and navigable by all users, including those with disabilities. This includes providing keyboard accessibility, proper use of semantic HTML elements, and integrating support for screen readers, voice control, and other assistive devices.

---

## 🔧 **Syntax**

To make a React application accessible, you can apply several accessibility practices and HTML attributes to your components.

### Basic Example of Accessibility Improvements:

```jsx
jsx
CopyEdit
import React from 'react';

function AccessibleButton() {
  return (
    <button onClick={() => alert('Button clicked!')} aria-label="Click me">
      Click Me
    </button>
  );
}

export default AccessibleButton;

```

In this example, we added an `aria-label` attribute to the button for **screen reader** users. This helps users who can't see the button to understand its function.

### Keyboard Accessibility Example:

```jsx
jsx
CopyEdit
import React, { useState } from 'react';

function AccessibleModal() {
  const [isOpen, setIsOpen] = useState(false);

  const handleKeyDown = (e) => {
    if (e.key === 'Escape') {
      setIsOpen(false);
    }
  };

  return (
    isOpen && (
      <div role="dialog" aria-labelledby="modal-title" onKeyDown={handleKeyDown} tabIndex="0">
        <h2 id="modal-title">Accessible Modal</h2>
        <button onClick={() => setIsOpen(false)}>Close</button>
      </div>
    )
  );
}

export default AccessibleModal;

```

In this example, the modal has a `role="dialog"` and can be closed with the `Escape` key, making it navigable via the keyboard.

---

## 🔧 **What to do with it**

### Key Practices for **Accessibility** in React:

1. **Use Semantic HTML Elements**: Use proper HTML tags like `<button>`, `<a>`, `<header>`, `<main>`, and `<footer>` instead of generic divs or spans. These elements have built-in accessibility benefits.
2. **Provide Alternative Text for Images**: Always use the `alt` attribute on images to provide alternative text for screen readers.
    
    ```jsx
    jsx
    CopyEdit
    <img src="image.jpg" alt="A description of the image" />
    
    ```
    
3. **Use ARIA Attributes**: When a semantic HTML element doesn’t provide enough context, use ARIA (Accessible Rich Internet Applications) attributes like `aria-label`, `aria-hidden`, `aria-live`, etc., to improve accessibility.
    - **`aria-label`**: Adds a description to an element that may not have a visible label.
    - **`aria-hidden="true"`**: Hides an element from screen readers (useful when elements are purely decorative).
4. **Ensure Keyboard Navigation**: Make sure that all interactive elements are accessible with the keyboard (e.g., using the `Tab` key). You can control focus behavior and focus management using the `tabIndex` attribute.
5. **Focus Management**: When modals, dialogs, or new content are loaded, ensure the focus is directed to an appropriate element. This can be achieved using React’s `useEffect` to update the focus when the component mounts.
    
    ```jsx
    jsx
    CopyEdit
    useEffect(() => {
      if (isOpen) {
        document.getElementById('modal-title').focus();
      }
    }, [isOpen]);
    
    ```
    
6. **Forms**: Label elements should always be associated with form controls using the `htmlFor` attribute in React (i.e., `<label htmlFor="id">`), which improves accessibility for screen readers.
    
    ```jsx
    jsx
    CopyEdit
    <label htmlFor="email">Email:</label>
    <input type="email" id="email" />
    
    ```
    

---

## 🔧 **What not to do with it**

### Common Accessibility Pitfalls:

1. **Ignoring ARIA roles**: Don’t forget to use appropriate ARIA roles when building custom components. For example, if you're building a modal, use `role="dialog"` to indicate the nature of the component.
2. **Using non-semantic tags for interactive elements**: Don’t use non-semantic tags (like `<div>` or `<span>`) for interactive elements like buttons or links. Always prefer `<button>` for actions and `<a>` for links.
3. **Skipping labels for form inputs**: Never leave form inputs without proper labels. Input elements must always have an associated label for screen reader users to know what the field is for.
4. **Inaccessible keyboard interactions**: Don’t rely on mouse-only interactions. Make sure users can navigate all interactive elements with the keyboard. This includes providing keyboard events like `onKeyDown`, `onFocus`, and `onBlur`.
5. **Neglecting focus management**: Avoid neglecting focus management when transitioning between modals, overlays, or dynamic content. Ensure that focus is returned to a logical place after closing a modal or after content changes.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Accessibility → Introduction to Accessibility
- "EpicReact.dev by Kent C. Dodds" – "Testing Accessibility"
- "Fullstackopen.com" – "Accessibility and Forms"

---

## 🛠️ **Best Practices for React Accessibility**

1. **Use a11y linters and tools**: Tools like **eslint-plugin-jsx-a11y** can help identify accessibility issues in your React code. You can integrate it into your build process to ensure accessibility standards are maintained.
2. **Testing with screen readers**: Use screen reader tools like **VoiceOver** (macOS) or **NVDA** (Windows) to test how your app behaves for users with visual impairments.
3. **Accessible Custom Components**: When creating custom components like buttons, ensure they are accessible by default. Use semantic HTML and ensure they’re focusable and keyboard navigable.
4. **Consider color contrast**: Ensure text has sufficient color contrast with its background so users with visual impairments can read the content easily.

# 📝 React Portals

React Portals provide a first-class way to render children into a DOM node that exists outside the parent component’s hierarchy. They can be useful for rendering modals, tooltips, and other UI elements that need to break out of their parent’s CSS styling or visual structure.

---

## 🔧 **Definition**

**React Portals** allow you to render React components outside of their parent DOM hierarchy, which is helpful for cases like rendering modals, tooltips, or dropdowns. The content rendered in a portal can be part of a different DOM tree, allowing you to escape parent styles or DOM constraints.

---

## 🔧 **Syntax**

### Basic Syntax of Portals:

```jsx
jsx
CopyEdit
import ReactDOM from 'react-dom';

function Modal({ children }) {
  return ReactDOM.createPortal(
    children,
    document.getElementById('modal-root') // Destination DOM node
  );
}

```

In this example, the `Modal` component renders its children into a DOM node with the id `modal-root`, which is located outside the regular React DOM hierarchy.

---

## 🔧 **Example**

### Full Example of a Modal Using Portals:

```jsx
jsx
CopyEdit
import React, { useState } from 'react';
import ReactDOM from 'react-dom';

function Modal({ message, onClose }) {
  return ReactDOM.createPortal(
    <div className="modal-overlay">
      <div className="modal-content">
        <p>{message}</p>
        <button onClick={onClose}>Close</button>
      </div>
    </div>,
    document.getElementById('modal-root') // Specify the destination DOM node
  );
}

function App() {
  const [showModal, setShowModal] = useState(false);

  const toggleModal = () => setShowModal(!showModal);

  return (
    <div>
      <button onClick={toggleModal}>Open Modal</button>
      {showModal && <Modal message="This is a modal!" onClose={toggleModal} />}
    </div>
  );
}

export default App;

```

### HTML for Modal Root:

```html
html
CopyEdit
<!-- Index.html -->
<div id="root"></div> <!-- Regular app root -->
<div id="modal-root"></div> <!-- Modal root, where the portal will render -->

```

In this example, when the user clicks the "Open Modal" button, the `Modal` component is rendered into the `#modal-root` element, outside of the parent `div`.

---

## 🔧 **What to do with it**

### Key Uses for React Portals:

1. **Modals & Dialogs**: Use portals to render modals outside the parent component, avoiding issues with z-index and overflow.
    
    ```jsx
    jsx
    CopyEdit
    ReactDOM.createPortal(
      <ModalContent />,
      document.getElementById('modal-root')
    );
    
    ```
    
2. **Tooltips & Popups**: Tooltips and popups often need to render outside the flow of the parent component. Portals allow you to achieve this behavior.
3. **Avoid CSS Overflows**: Portals allow components to break free from parent elements with overflow restrictions, such as a scrollable container.
4. **Contextual UI Components**: Use portals to render contextual elements (e.g., dropdowns, popovers) that should not be clipped or hidden by parent elements.
5. **Accessibility**: Portals can be useful in managing focus and accessibility features by rendering content to the root of the DOM, helping screen readers and focus management.

---

## 🔧 **What not to do with it**

### Common Pitfalls with React Portals:

1. **Avoid Overusing Portals**: Don't use portals unnecessarily. They're best used for elements that need to "escape" their parent component's styling or constraints, not for basic UI components that don't require it.
2. **Overcomplicating Layouts**: Don’t overcomplicate the layout by rendering too many elements in portals. If your UI doesn’t require complex layering, it’s better to stick with traditional React rendering.
3. **Not Managing Focus**: Portals can break focus management. When you use portals for elements like modals, ensure that you manage the focus appropriately (e.g., move focus to the modal when it opens and back when it closes).
4. **Neglecting Cleanup**: Ensure cleanup is done when components rendered through portals are removed. For instance, removing modals or overlays should reset any focus management or keyboard listeners.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Portals → API Reference
- "EpicReact.dev by Kent C. Dodds" – "Portals & Modals"
- "Fullstackopen.com" – "React Portals"

---

## 🛠️ **Best Practices for React Portals**

1. **Use for Modals and Tooltips**: Portals are ideal for rendering modals, popups, tooltips, and dropdowns that need to break out of their parent container’s overflow or z-index stacking context.
2. **Focus Management**: Ensure that when a portal is opened (e.g., a modal), the focus is moved to an accessible element (like the modal) and returns to the previous element when closed.
3. **Manage Accessibility**: Consider using `aria-modal` and `aria-labelledby` for modals to improve accessibility. Always ensure that the content in the portal is usable with assistive technologies.
4. **Ensure Cleanup**: If you’re using portals for temporary UI elements, make sure to clean them up properly when they are no longer needed, to avoid memory leaks or unwanted side effects.

# 📝 `useImperativeHandle` with `forwardRef`

The `useImperativeHandle` hook is used in conjunction with `forwardRef` to customize the instance value that is exposed to the parent component when a child component is referenced. It provides a way to expose specific methods or properties to the parent component while keeping the child component encapsulated.

---

## 🔧 **Definition**

`useImperativeHandle` allows you to control what values are exposed to the parent component when using `ref`. It is commonly used with `forwardRef` to give the parent access to specific functions or methods within the child component.

---

## 🔧 **Syntax**

```jsx
jsx
CopyEdit
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const MyComponent = forwardRef((props, ref) => {
  const localRef = useRef();

  useImperativeHandle(ref, () => ({
    focus: () => {
      localRef.current.focus();
    },
    // Add other methods to expose
  }));

  return <input ref={localRef} />;
});

```

- `forwardRef` is used to forward the `ref` to the child component.
- `useImperativeHandle` is used to define what the `ref` will expose to the parent.

---

## 🔧 **Example**

### Example: Custom Input with `focus` Method Exposed

```jsx
jsx
CopyEdit
import React, { useState, useRef, useImperativeHandle, forwardRef } from 'react';

// Child Component
const CustomInput = forwardRef((props, ref) => {
  const inputRef = useRef();

  // Expose custom methods via ref
  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    },
    clear: () => {
      inputRef.current.value = '';
    },
  }));

  return <input ref={inputRef} placeholder="Enter text" />;
});

// Parent Component
function App() {
  const inputRef = useRef();

  const handleFocus = () => {
    inputRef.current.focus();  // Focus input using ref method
  };

  const handleClear = () => {
    inputRef.current.clear();  // Clear input value using ref method
  };

  return (
    <div>
      <CustomInput ref={inputRef} />
      <button onClick={handleFocus}>Focus Input</button>
      <button onClick={handleClear}>Clear Input</button>
    </div>
  );
}

export default App;

```

In this example:

- The `CustomInput` component exposes the `focus` and `clear` methods using `useImperativeHandle` and `forwardRef`.
- The parent component (`App`) uses `ref` to invoke these methods on the `CustomInput` component.

---

## 🔧 **What to do with it**

### Key Uses for `useImperativeHandle` with `forwardRef`:

1. **Expose Specific Methods to Parent**: It allows you to selectively expose only certain methods or properties of a child component to the parent, rather than exposing the entire DOM node.
    
    ```jsx
    jsx
    CopyEdit
    useImperativeHandle(ref, () => ({
      focus: () => { inputRef.current.focus(); }
    }));
    
    ```
    
2. **Implement Custom Component APIs**: Use `useImperativeHandle` to create a controlled API for your child component (e.g., methods to focus, reset, or trigger animations).
3. **Avoid Direct Manipulation**: Keep the child component encapsulated and avoid manipulating the DOM directly in the parent. Expose only the necessary functions.

---

## 🔧 **What not to do with it**

### Common Pitfalls with `useImperativeHandle` and `forwardRef`:

1. **Exposing Too Much**: Avoid exposing too many methods or properties to the parent. Keep the API minimal to maintain encapsulation.
2. **Overuse of `ref` for Manipulation**: Don’t over-rely on `useImperativeHandle` and `ref` to manipulate child components. React's declarative model should generally be the primary means of controlling state and behavior.
3. **Avoid Unnecessary `ref` Propagation**: If you don’t need to expose any methods or properties from the child component, don’t use `useImperativeHandle`. Instead, rely on props for managing behavior.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Forwarding Refs → `useImperativeHandle`
- "EpicReact.dev by Kent C. Dodds" – "React Refs and Imperative Handles"
- "Fullstackopen.com" – "Advanced React Concepts → useImperativeHandle"

---

## 🛠️ **Best Practices for `useImperativeHandle` with `forwardRef`**

1. **Keep the API Minimal**: Only expose necessary methods that make sense for the parent to control. This ensures that the child component stays encapsulated and the parent does not have excessive control over it.
2. **Avoid Direct DOM Manipulation**: Whenever possible, prefer the declarative React model over direct DOM manipulation, even when using `useImperativeHandle`. Only expose methods when absolutely necessary.
3. **Encapsulate Logic in Child**: Ensure that the methods you expose are related to the child component’s specific behavior, and avoid exposing too much internal logic.

# 📝 **Server-Side Rendering (Next.js)**

Server-Side Rendering (SSR) refers to the process of rendering a React application on the server, sending the fully rendered HTML to the client, and then allowing React to take over and hydrate the page. This results in faster initial load times and better SEO.

---

## 🔧 **Definition**

SSR in Next.js allows pages to be rendered on the server on each request. This is particularly useful for dynamic content that changes frequently or needs to be indexed by search engines for better SEO.

In Next.js, SSR is enabled using the `getServerSideProps` function. This function runs on the server before the page is rendered and can fetch data, which is passed to the page as props.

---

## 🔧 **Syntax**

### Basic Syntax for `getServerSideProps`

```jsx
jsx
CopyEdit
// pages/[page].js or pages/[slug].js
export async function getServerSideProps(context) {
  // Fetch data (e.g., from an API, database, etc.)
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();

  // Return the data as props
  return { props: { data } };
}

function Page({ data }) {
  return (
    <div>
      <h1>Data from SSR</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default Page;

```

- `getServerSideProps`: This function runs on the server and fetches the required data before rendering the page.
- `context`: Provides information about the request (e.g., query parameters, headers).
- The `props` returned from `getServerSideProps` are passed to the page component.

---

## 🔧 **Example**

### Example: Server-Side Rendering with Fetch API

```jsx
jsx
CopyEdit
// pages/products.js

export async function getServerSideProps() {
  const res = await fetch('https://api.example.com/products');
  const products = await res.json();

  return {
    props: {
      products,
    },
  };
}

function Products({ products }) {
  return (
    <div>
      <h1>Products List</h1>
      <ul>
        {products.map((product) => (
          <li key={product.id}>{product.name}</li>
        ))}
      </ul>
    </div>
  );
}

export default Products;

```

- The `getServerSideProps` function fetches data from an API before rendering the `Products` page.
- The page is rendered with the data and sent to the client.

---

## 🔧 **What to do with it**

### Key Uses for Server-Side Rendering in Next.js:

1. **SEO Optimization**: SSR ensures that search engines can crawl and index the fully rendered HTML, improving your app's SEO performance.
    - Use SSR for pages that require fast load times and need to be indexed by search engines (e.g., product listings, blog posts).
2. **Pre-fetching Data**: SSR allows you to fetch data before rendering the page, ensuring that the user sees the content immediately when they load the page.
3. **Dynamic Content**: Use SSR for pages where the content changes on every request or based on user input (e.g., dashboards, admin panels).

---

## 🔧 **What not to do with it**

### Common Pitfalls with SSR:

1. **Unnecessary SSR for Static Content**: Avoid using SSR for pages that don't require dynamic data or frequent updates. For these pages, **Static Site Generation (SSG)** or **Client-Side Rendering (CSR)** is preferred.
    - Use `getStaticProps` for static content that doesn't change on every request to improve performance.
2. **Blocking the UI**: SSR can introduce server load, especially if data fetching takes too long or if there's too much computation. Avoid blocking the UI with too much synchronous logic in the `getServerSideProps` function.
3. **Stateful Pages**: If your page is highly interactive (e.g., dynamic forms, real-time data), SSR might not be the best solution. Consider using CSR with API routes for interactive content.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Server-Side Rendering → Next.js → `getServerSideProps`
- "EpicReact.dev by Kent C. Dodds" – "Server-Side Rendering with Next.js"
- "Fullstackopen.com" – "Fullstack React → Server-Side Rendering"

---

## 🛠️ **Best Practices for Server-Side Rendering in Next.js**

1. **Leverage Static Site Generation (SSG) When Possible**: If your page content doesn’t change often or requires no server-side processing, consider using `getStaticProps` for faster page loads.
2. **Optimize Data Fetching**: Use caching or reduce the amount of data fetched to speed up the SSR process. This can help improve server performance.
3. **Use `getServerSideProps` Only for Dynamic Content**: Reserve SSR for pages that need to be updated on each request or require dynamic content, such as user dashboards or personalized pages.
4. **Handle Errors Gracefully**: Ensure proper error handling in your `getServerSideProps` function to avoid rendering issues. You can display fallback content or redirect users if the data fetching fails.

# 📝 **Static Site Generation (Next.js)**

Static Site Generation (SSG) in Next.js is the process of pre-rendering a page at build time, creating static HTML files that are served to users when they visit the page. This method is fast and great for SEO, as the HTML is already built and can be indexed by search engines.

---

## 🔧 **Definition**

SSG in Next.js allows pages to be pre-rendered at build time. This means the page content is generated once, saved as static HTML, and reused for each request. SSG is perfect for pages that do not need to change frequently, as the page content is generated during the build process.

In Next.js, SSG is enabled by using the `getStaticProps` function, which fetches data at build time, and `getStaticPaths` when generating dynamic routes.

---

## 🔧 **Syntax**

### Basic Syntax for `getStaticProps`

```jsx
jsx
CopyEdit
// pages/[page].js or pages/[slug].js
export async function getStaticProps() {
  // Fetch data (e.g., from an API, database, etc.)
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();

  // Return the data as props
  return { props: { data } };
}

function Page({ data }) {
  return (
    <div>
      <h1>Data from SSG</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default Page;

```

- `getStaticProps`: This function runs at build time and fetches data, which is passed as props to the page component.
- `context`: Provides information about the request (e.g., query parameters, headers) for dynamic routes.
- The `props` returned from `getStaticProps` are passed to the page component.

---

### Syntax for Dynamic Routes with `getStaticPaths`

```jsx
jsx
CopyEdit
// pages/posts/[id].js

export async function getStaticPaths() {
  const res = await fetch('https://api.example.com/posts');
  const posts = await res.json();

  // Generate paths for each post
  const paths = posts.map(post => ({
    params: { id: post.id.toString() },
  }));

  return { paths, fallback: false };
}

export async function getStaticProps({ params }) {
  const res = await fetch(`https://api.example.com/posts/${params.id}`);
  const post = await res.json();

  return { props: { post } };
}

function Post({ post }) {
  return (
    <div>
      <h1>{post.title}</h1>
      <p>{post.content}</p>
    </div>
  );
}

export default Post;

```

- `getStaticPaths`: This function is used to specify which dynamic pages should be generated at build time. It returns an array of paths and a `fallback` strategy.
- `getStaticProps`: Fetches the data for each dynamic page at build time and passes it as props.

---

## 🔧 **Example**

### Example: Static Site Generation for a Blog

```jsx
jsx
CopyEdit
// pages/blog.js

export async function getStaticProps() {
  const res = await fetch('https://api.example.com/blog');
  const blogPosts = await res.json();

  return {
    props: { blogPosts },
  };
}

function Blog({ blogPosts }) {
  return (
    <div>
      <h1>Blog Posts</h1>
      <ul>
        {blogPosts.map(post => (
          <li key={post.id}>
            <h2>{post.title}</h2>
            <p>{post.summary}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default Blog;

```

- The `getStaticProps` function fetches the blog posts at build time.
- The page is statically generated and served with the pre-fetched data.

---

## 🔧 **What to do with it**

### Key Uses for Static Site Generation in Next.js:

1. **SEO Optimization**: SSG provides fully rendered HTML at build time, which is ideal for SEO, as search engines can easily crawl and index the content.
2. **Performance**: Static pages are fast because they are pre-built and served as HTML. This makes SSG a great choice for sites with content that doesn’t change frequently.
3. **Pre-rendering for Public Pages**: Use SSG for public pages that don't require frequent data updates, like blog posts, product landing pages, or documentation.

---

## 🔧 **What not to do with it**

### Common Pitfalls with Static Site Generation:

1. **Use SSR (Server-Side Rendering) for Dynamic Pages**: Avoid using SSG for pages that need to display frequently changing or dynamic data (e.g., real-time dashboards). In such cases, SSR with `getServerSideProps` is a better choice.
2. **Overusing Dynamic Routes with SSG**: Be cautious when generating too many dynamic routes at build time, especially for content that changes often. This can increase the build time and lead to unnecessary static page generation.
3. **Heavy Pages at Build Time**: If your pages require heavy data fetching or complex logic at build time, it may increase the build time significantly. Consider optimizing the data fetching process.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Static Site Generation → Next.js → `getStaticProps`, `getStaticPaths`
- "EpicReact.dev by Kent C. Dodds" – "Static Site Generation with Next.js"
- "Fullstackopen.com" – "Fullstack React → Static Site Generation"

---

## 🛠️ **Best Practices for Static Site Generation in Next.js**

1. **Use `getStaticProps` for Static Data**: Only use SSG for data that doesn’t change frequently. Examples include blog posts, marketing pages, or documentation.
2. **Optimize Build Time**: Avoid unnecessary data fetching during the build process to speed up the build time. If your data is large or slow to fetch, consider optimizing the request or caching the data.
3. **Leverage Incremental Static Regeneration (ISR)**: For pages that need to be updated after deployment, use ISR to update static pages without rebuilding the entire site.
4. **Dynamic Routes with `getStaticPaths`**: Use `getStaticPaths` for generating static pages for dynamic routes at build time. This is useful for blog posts, product pages, or user-generated content.

# 📝 **React DevTools & Debugging**

React DevTools is a browser extension that helps developers inspect and debug React applications. It provides insights into component hierarchies, props, state, and renders, allowing developers to debug and optimize their applications with ease.

---

## 🔧 **Definition**

React DevTools is a set of debugging tools that allows you to inspect the React component tree, view and edit component props and state, profile render performance, and track other aspects of React applications, such as hooks, contexts, and the component's lifecycle.

React DevTools consists of two parts:

1. **Browser extension** – Available for Chrome and Firefox, allows you to inspect React components directly in the browser.
2. **Standalone app** – A desktop application to use DevTools outside the browser.

---

## 🔧 **Syntax**

### Inspecting Components

1. Install the React DevTools extension in your browser (Chrome or Firefox).
2. Open DevTools in the browser (right-click on the page → Inspect or `Ctrl + Shift + I` / `Cmd + Option + I`).
3. Switch to the **React** tab in DevTools.
4. You will see the component hierarchy of your React app.

The tree shows:

- **Props**: Information passed to the component.
- **State**: The current state of the component.
- **Hooks**: If using hooks, you can see the state of each hook.

---

## 🔧 **Example**

### Example: Inspecting a Functional Component

```jsx
jsx
CopyEdit
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}

export default Counter;

```

1. Open the **React** tab in the DevTools.
2. Select the `<Counter />` component from the tree.
3. You’ll see the `count` value in the **State** section and can change it interactively.
4. You can also view the `setCount` function in the **Props** or **Hooks** section, depending on how it's used.

---

## 🔧 **What to do with it**

### Key Uses for React DevTools:

1. **Inspecting Components**: View the component tree to understand the structure of your React app, see props, state, and context.
2. **Debugging State and Props**: Quickly inspect and edit the state and props of individual components to troubleshoot bugs or adjust UI behavior.
3. **Profiling Performance**: Use the **Profiler** tab to measure how long each component takes to render, which can help you identify performance bottlenecks.
4. **Testing Changes**: Modify props, state, or even component internals in the DevTools to experiment and see how the UI updates in real-time, helping you quickly debug.
5. **Inspecting Hooks**: If using React hooks, you can view and modify the state of hooks like `useState`, `useEffect`, `useReducer`, etc.

---

## 🔧 **What not to do with it**

### Common Pitfalls:

1. **Don’t rely solely on DevTools for debugging**: While React DevTools is powerful, use it as a tool for inspection. It doesn't replace regular logging, testing, or traditional debugging techniques.
2. **Avoid making changes in the DevTools in production**: While it's convenient to modify the state or props through DevTools, doing this in production can be dangerous and may lead to unexpected behaviors. Always ensure that changes made in DevTools are for development purposes only.
3. **Be mindful of sensitive data**: If you're debugging in production, make sure not to expose sensitive information through props or state in DevTools. Always hide sensitive data from UI components in production.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Debugging → React Developer Tools
- "EpicReact.dev by Kent C. Dodds" – "React DevTools"
- "Fullstackopen.com" – "React → Debugging with React DevTools"

---

## 🛠️ **Best Practices for Using React DevTools**

1. **Use Profiler for Performance Optimization**: Profiling in React DevTools can help you identify unnecessary re-renders. Use it to optimize your app's performance by avoiding unnecessary state updates or re-renders.
2. **Inspect the Hook Values**: When using hooks, inspect them through React DevTools to ensure they are holding the correct values. This is especially useful for debugging issues with `useEffect`, `useState`, and `useReducer`.
3. **Check Component Renders**: Use the **highlight updates** option in the DevTools settings to highlight components that are re-rendering. This can help pinpoint unnecessary renders and optimize your code.
4. **Track Context and Provider Updates**: If your app uses context, React DevTools provides the ability to track context values and see how they flow through your component tree. This is useful for debugging issues related to prop drilling and state management.

# 📝 **State Management Libraries (Redux, Zustand, Recoil)**

State management libraries help handle and centralize the state of an application, making it easier to manage and share state across components. They are especially useful in large applications where multiple components need access to shared state.

This note covers three popular state management libraries: **Redux**, **Zustand**, and **Recoil**.

---

## 🔧 **Definition**

### **Redux**

Redux is a state management library that works on the principle of a global state container. It follows a strict unidirectional data flow where the state is immutable and can only be changed through dispatching actions, which are processed by reducers.

### **Zustand**

Zustand is a small and fast state management library that focuses on simplicity and scalability. Unlike Redux, Zustand doesn’t require actions or reducers, and the state is mutable. Zustand’s API is minimal, and it provides hooks to manage state within React components.

### **Recoil**

Recoil is a state management library for React that allows you to manage state in a more declarative way using atoms and selectors. It is designed to integrate seamlessly with React’s concurrent mode and offers fine-grained control over updates to the state.

---

## 🔧 **Syntax**

### **Redux**

```bash
bash
CopyEdit
npm install redux react-redux

```

**Store:**

```jsx
javascript
CopyEdit
import { createStore } from 'redux';

const initialState = {
  count: 0,
};

const reducer = (state = initialState, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return { count: state.count + 1 };
    case 'DECREMENT':
      return { count: state.count - 1 };
    default:
      return state;
  }
};

const store = createStore(reducer);

```

**Dispatching Actions:**

```jsx
javascript
CopyEdit
store.dispatch({ type: 'INCREMENT' });
store.dispatch({ type: 'DECREMENT' });

```

**Connecting React Components:**

```jsx
javascript
CopyEdit
import { useDispatch, useSelector } from 'react-redux';

const Counter = () => {
  const count = useSelector((state) => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
    </div>
  );
};

```

---

### **Zustand**

```bash
bash
CopyEdit
npm install zustand

```

**Creating a Store:**

```jsx
javascript
CopyEdit
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

```

**Using the Store in Components:**

```jsx
javascript
CopyEdit
const Counter = () => {
  const { count, increment, decrement } = useStore();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

```

---

### **Recoil**

```bash
bash
CopyEdit
npm install recoil

```

**Creating Atoms:**

```jsx
javascript
CopyEdit
import { atom, selector, useRecoilState } from 'recoil';

const countState = atom({
  key: 'countState',
  default: 0,
});

```

**Using Atoms in Components:**

```jsx
javascript
CopyEdit
const Counter = () => {
  const [count, setCount] = useRecoilState(countState);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};

```

---

## 🔧 **Example**

### Example with Redux

```jsx
javascript
CopyEdit
import { useSelector, useDispatch } from 'react-redux';

const Counter = () => {
  const count = useSelector((state) => state.count);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
    </div>
  );
};

```

### Example with Zustand

```jsx
javascript
CopyEdit
import create from 'zustand';

const useStore = create((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
  decrement: () => set((state) => ({ count: state.count - 1 })),
}));

const Counter = () => {
  const { count, increment, decrement } = useStore();

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

```

### Example with Recoil

```jsx
javascript
CopyEdit
import { atom, useRecoilState } from 'recoil';

const countState = atom({
  key: 'countState',
  default: 0,
});

const Counter = () => {
  const [count, setCount] = useRecoilState(countState);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </div>
  );
};

```

---

## 🔧 **What to do with it**

1. **Choose based on complexity**:
    - **Redux** is great for large applications with complex state logic and multiple layers of state management.
    - **Zustand** is ideal for small to medium applications where simplicity and ease of use are crucial.
    - **Recoil** is suitable for applications that need fine-grained control over state updates and work well with React's concurrent mode.
2. **Use Redux for centralized state management**: For apps with many components needing access to global state, Redux is a solid choice due to its predictable flow and middleware support (e.g., for async actions).
3. **Choose Zustand for simplicity**: Zustand is a lightweight solution that avoids the boilerplate of Redux and fits well with small applications or where quick state updates are needed.
4. **Use Recoil for complex React state**: Recoil’s atom and selector-based approach fits well with larger React applications where you need to work with derived state and fine-grained control over component updates.

---

## 🔧 **What not to do with it**

1. **Avoid unnecessary complexity**: If your application doesn’t have complex state needs, using Redux or Recoil can lead to unnecessary complexity. Consider using React’s built-in `useState` and `useContext` first.
2. **Don’t overuse global state**: Overusing global state can lead to performance issues and difficult-to-maintain code. Only use a state management library when necessary and keep state local when possible.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – State Management → "Context API"
- "EpicReact.dev by Kent C. Dodds" – "State Management in React"
- "Fullstackopen.com" – "State Management → Redux, Context API, Zustand, Recoil"

# 📝 **React Query / TanStack Query (Data Caching)**

React Query (now known as TanStack Query) is a powerful data-fetching library for React. It helps with data caching, synchronization, and background data fetching, providing hooks and utility functions to manage server-side data in a client-side application.

---

## 🔧 **Definition**

### **React Query / TanStack Query**

React Query (TanStack Query) is a library that simplifies data fetching, caching, synchronization, and state management in React applications. It provides hooks for fetching, caching, and synchronizing data, and automatically manages background refetching, caching, and error handling.

The library abstracts away many complexities of server state management, making it easy to integrate with REST APIs, GraphQL, and other data sources.

---

## 🔧 **Syntax**

### **Installation**

```bash
bash
CopyEdit
npm install @tanstack/react-query

```

### **Basic Setup with QueryClientProvider**

```jsx
javascript
CopyEdit
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new QueryClient();

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <YourComponents />
    </QueryClientProvider>
  );
}

```

---

## 🔧 **Example**

### **Basic Fetching Data with useQuery**

React Query simplifies data fetching with `useQuery` and provides automatic caching.

```jsx
javascript
CopyEdit
import { useQuery } from '@tanstack/react-query';

const fetchData = async () => {
  const response = await fetch('/api/data');
  if (!response.ok) {
    throw new Error('Error fetching data');
  }
  return response.json();
};

function DataFetcher() {
  const { data, error, isLoading } = useQuery(['data'], fetchData);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
}

```

---

### **Mutating Data with useMutation**

`useMutation` is used for creating, updating, or deleting data on the server.

```jsx
javascript
CopyEdit
import { useMutation } from '@tanstack/react-query';

const updateData = async (newData) => {
  const response = await fetch('/api/data', {
    method: 'POST',
    body: JSON.stringify(newData),
  });
  if (!response.ok) throw new Error('Error updating data');
  return response.json();
};

function DataUpdater() {
  const mutation = useMutation(updateData);

  const handleSubmit = async (newData) => {
    mutation.mutate(newData);
  };

  return (
    <div>
      <button onClick={() => handleSubmit({ key: 'value' })}>
        Update Data
      </button>
      {mutation.isLoading && <p>Updating...</p>}
      {mutation.isError && <p>Error: {mutation.error.message}</p>}
    </div>
  );
}

```

---

## 🔧 **Key Features**

1. **Data Caching**: React Query automatically caches the data, so once data is fetched, it doesn’t need to be fetched again unless necessary. Cached data is returned instantly from the cache and can be refetched in the background.
2. **Background Refetching**: It refetches data in the background to keep it up to date automatically. You can configure how often it should refetch or whether it should refetch at all.
3. **Pagination and Infinite Query Support**: React Query provides built-in support for paginated or infinite queries with powerful query caching capabilities.
4. **Optimistic Updates**: React Query allows for optimistic UI updates, enabling a smooth user experience even during mutations.
5. **Automatic Retries**: It automatically retries failed queries for a configurable number of attempts.

---

## 🔧 **What to do with it**

1. **Cache Server Data**: Use React Query to cache and fetch data from the server. This avoids unnecessary network requests and optimizes app performance.
2. **Leverage Background Fetching**: Use the background refetching feature to keep your app data fresh. React Query will automatically update your UI when new data is available.
3. **Use Optimistic Updates**: Optimistic updates allow you to update the UI before the mutation is successful, providing immediate feedback to the user.
4. **Handling Errors Gracefully**: Use React Query’s built-in error handling to show meaningful error messages to users when data fetching or mutations fail.

---

## 🔧 **What not to do with it**

1. **Avoid Overusing React Query for Client-side State**: React Query is primarily meant for server-side state. Use React’s `useState` and `useContext` for local UI state management.
2. **Don’t Cache Sensitive Data**: Be cautious about caching sensitive data, such as passwords or personal user information. Always consider security when caching.
3. **Don’t Forget to Clean Up**: While React Query handles cleanup automatically in most cases, remember to manage your queries properly to avoid memory leaks in complex scenarios.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – Data Fetching → "React Query"
- "EpicReact.dev by Kent C. Dodds" – "Data Fetching with React Query"
- "Fullstackopen.com" – "State Management → React Query"

# 📝 **React with TypeScript (Basic to Advanced)**

React with TypeScript enhances the development experience by providing type safety, autocompletion, and better tooling. It’s a powerful combination for building maintainable and scalable React applications.

---

## 🔧 **Definition**

### **React with TypeScript**

React with TypeScript is the use of TypeScript alongside React to add static typing to JavaScript, helping catch potential errors early in the development process. TypeScript improves code quality and maintainability by enforcing type constraints and provides a better developer experience with autocompletion and type checking.

---

## 🔧 **Syntax**

### **Installation**

First, ensure that TypeScript is installed:

```bash
bash
CopyEdit
npm install typescript @types/react @types/react-dom

```

Then, set up the `tsconfig.json` file for the project.

---

### **Basic Example (Type-safe Functional Component)**

```tsx
tsx
CopyEdit
import React from 'react';

type Props = {
  name: string;
  age: number;
};

const Greeting: React.FC<Props> = ({ name, age }) => {
  return <h1>Hello, {name}. You are {age} years old.</h1>;
};

export default Greeting;

```

---

### **Type Safety for Event Handlers**

```tsx
tsx
CopyEdit
import React, { useState } from 'react';

const Counter: React.FC = () => {
  const [count, setCount] = useState<number>(0);

  const increment = (event: React.MouseEvent<HTMLButtonElement>) => {
    setCount(count + 1);
  };

  return <button onClick={increment}>Count: {count}</button>;
};

export default Counter;

```

---

## 🔧 **Example**

### **Handling Form Inputs with TypeScript**

```tsx
tsx
CopyEdit
import React, { useState } from 'react';

type FormData = {
  name: string;
  email: string;
};

const Form: React.FC = () => {
  const [formData, setFormData] = useState<FormData>({ name: '', email: '' });

  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const { name, value } = e.target;
    setFormData((prevData) => ({ ...prevData, [name]: value }));
  };

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    alert(`Name: ${formData.name}, Email: ${formData.email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <inputtype="text"
        name="name"
        value={formData.name}
        onChange={handleChange}
        placeholder="Name"
      />
      <inputtype="email"
        name="email"
        value={formData.email}
        onChange={handleChange}
        placeholder="Email"
      />
      <button type="submit">Submit</button>
    </form>
  );
};

export default Form;

```

---

## 🔧 **Key Concepts**

1. **Type Definitions for Props and State**: TypeScript allows you to define explicit types for component props and state, preventing incorrect values from being passed.
2. **Type-safe Event Handlers**: You can define the type of events and form inputs to avoid runtime errors by ensuring the correct data types.
3. **Generics in TypeScript**: TypeScript's generic system allows creating reusable components with flexible types, such as `React.FC` (Function Component) and `useState<T>`.
4. **Custom Hooks with Types**: TypeScript enhances the ability to define custom hooks with proper types for state and functions.
5. **Type-safe Context API**: When using React's Context API, TypeScript helps in maintaining type safety across the application for global states.

---

## 🔧 **What to do with it**

1. **Ensure Type Safety**: Use TypeScript to ensure that props, states, and events conform to the correct types, reducing the likelihood of bugs.
2. **Use Type Definitions for External Libraries**: Make sure to install the correct `@types` for libraries like `react-router`, `axios`, etc., to maintain proper type safety when interacting with third-party libraries.
3. **Leverage TypeScript's Type Inference**: Let TypeScript infer types where possible, reducing verbosity without sacrificing type safety.
4. **Write Type-safe Custom Hooks**: Ensure that custom hooks like `useState`, `useEffect`, etc., are typed correctly to enforce constraints on your components.

---

## 🔧 **What not to do with it**

1. **Avoid Using `any`**: Using `any` defeats the purpose of TypeScript and weakens type safety. Stick to using specific types or `unknown` if necessary.
2. **Don’t Overcomplicate Types**: Avoid over-engineering types with unnecessary complexity. Stick to simple and readable types to maintain the developer experience.
3. **Don’t Skip Type Definitions for Props**: Skipping type definitions for component props could lead to unintended bugs, as it allows anything to be passed into the component.
4. **Avoid Explicit `as` Casting**: Use `as` casting sparingly, as it bypasses TypeScript’s type checking and can introduce hidden bugs.

---

## 🔧 **Advanced Concepts (TypeScript + React)**

1. **Union and Intersection Types for Props**: Combine types with union (`|`) and intersection (`&`) to create more flexible and reusable components.

```tsx
tsx
CopyEdit
type ButtonProps = {
  onClick: () => void;
} & (
  | { type: 'submit'; label: string }
  | { type: 'reset'; label: string }
);

```

1. **Generics in React Components and Hooks**: Use generics to create components and hooks that can handle different types of data.

```tsx
tsx
CopyEdit
function List<T>({ items }: { items: T[] }) {
  return <ul>{items.map((item, index) => <li key={index}>{item}</li>)}</ul>;
}

```

1. **Type-safe Context API**: Use TypeScript with React’s Context API to enforce type safety on context values and consumers.

```tsx
tsx
CopyEdit
type ThemeContextType = { theme: 'light' | 'dark'; toggleTheme: () => void };

const ThemeContext = React.createContext<ThemeContextType | undefined>(undefined);

```

1. **Type-safe Ref with `useRef`**: Define a type for refs when using `useRef` to prevent type errors when accessing the DOM or other values.

```tsx
tsx
CopyEdit
const inputRef = useRef<HTMLInputElement>(null);

```

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – "TypeScript" → "TypeScript with React"
- "EpicReact.dev by Kent C. Dodds" – "TypeScript" → "React with TypeScript"
- "Fullstackopen.com" – "TypeScript and React"

# 📝 **Design Patterns in React (Container/Presentational, Hooks-based)**

Design patterns in React are reusable solutions to common problems faced in React development. These patterns help improve code readability, maintainability, and reusability.

---

## 🔧 **Definition**

### **Container/Presentational Pattern**

The Container/Presentational pattern divides the concerns of a React component into two distinct categories:

- **Container Component**: Responsible for managing state and business logic, and it handles data fetching, state updates, and interactions with other components.
- **Presentational Component**: Responsible for rendering the UI and displaying data. It doesn’t manage state, but instead receives props for data and events.

---

### **Hooks-based Pattern**

The Hooks-based pattern leverages React's Hooks to separate logic from UI rendering, improving component readability and reusability. This pattern involves creating custom hooks to encapsulate business logic, state management, and side effects.

---

## 🔧 **Syntax**

### **Container/Presentational Example**

```tsx
tsx
CopyEdit
// Container Component (Manages State)
import React, { useState, useEffect } from 'react';
import { PresentationalComponent } from './PresentationalComponent';

const ContainerComponent: React.FC = () => {
  const [data, setData] = useState<string[]>([]);

  useEffect(() => {
    // Fetching data (or any business logic)
    fetchData().then((result) => setData(result));
  }, []);

  return <PresentationalComponent data={data} />;
};

const fetchData = async (): Promise<string[]> => {
  // Simulate an API call
  return ['Item 1', 'Item 2', 'Item 3'];
};

export default ContainerComponent;

```

```tsx
tsx
CopyEdit
// Presentational Component (UI-only)
import React from 'react';

type Props = {
  data: string[];
};

const PresentationalComponent: React.FC<Props> = ({ data }) => {
  return (
    <div>
      <h1>Data List:</h1>
      <ul>
        {data.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
};

export default PresentationalComponent;

```

---

### **Hooks-based Example**

```tsx
tsx
CopyEdit
// Custom Hook for fetching data
import { useState, useEffect } from 'react';

const useFetchData = (url: string) => {
  const [data, setData] = useState<any[]>([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchData = async () => {
      const response = await fetch(url);
      const result = await response.json();
      setData(result);
      setLoading(false);
    };

    fetchData();
  }, [url]);

  return { data, loading };
};

export default useFetchData;

```

```tsx
tsx
CopyEdit
// Using Custom Hook in a Component
import React from 'react';
import useFetchData from './useFetchData';

const DataFetchingComponent: React.FC = () => {
  const { data, loading } = useFetchData('/api/data');

  if (loading) return <p>Loading...</p>;

  return (
    <div>
      <h1>Fetched Data:</h1>
      <ul>
        {data.map((item, index) => (
          <li key={index}>{item}</li>
        ))}
      </ul>
    </div>
  );
};

export default DataFetchingComponent;

```

---

## 🔧 **Example**

### **Container/Presentational Pattern Example**

```tsx
tsx
CopyEdit
// Container Component
import React, { useState, useEffect } from 'react';
import { PresentationalComponent } from './PresentationalComponent';

const ContainerComponent: React.FC = () => {
  const [items, setItems] = useState<string[]>([]);

  useEffect(() => {
    setTimeout(() => {
      setItems(['Apple', 'Banana', 'Orange']);
    }, 1000);
  }, []);

  return <PresentationalComponent items={items} />;
};

export default ContainerComponent;

```

```tsx
tsx
CopyEdit
// Presentational Component
import React from 'react';

type Props = {
  items: string[];
};

const PresentationalComponent: React.FC<Props> = ({ items }) => {
  return (
    <div>
      <h2>Fruits List</h2>
      {items.length === 0 ? (
        <p>Loading...</p>
      ) : (
        <ul>
          {items.map((item, index) => (
            <li key={index}>{item}</li>
          ))}
        </ul>
      )}
    </div>
  );
};

export default PresentationalComponent;

```

---

## 🔧 **What to do with it**

1. **Separate Concerns**: Use the Container/Presentational pattern to clearly separate the logic of data fetching and state management (Container) from the rendering of the UI (Presentational).
2. **Reusable Logic with Custom Hooks**: With the Hooks-based pattern, create custom hooks for reusable logic (like fetching data or managing state) to be shared across multiple components.
3. **Keep Presentational Components Pure**: Ensure Presentational components are purely concerned with rendering UI and receiving data and callbacks through props.
4. **Enhance Code Readability**: By using the Hooks-based pattern and separating logic into custom hooks, the code becomes cleaner, more modular, and easier to debug.

---

## 🔧 **What not to do with it**

1. **Don’t Mix Business Logic with UI**: Avoid embedding state management or data fetching directly in Presentational components. It leads to unmanageable and untestable code.
2. **Don’t Overuse Custom Hooks**: While custom hooks are useful, avoid making everything into a hook when it could be simpler to handle in the component itself.
3. **Avoid Prop Drilling**: When passing data through several layers of components, consider using the Context API or state management libraries instead of passing props down multiple levels.
4. **Don’t Over-Abstract Logic**: Over-abstraction of logic into custom hooks or higher-order components can make the code harder to understand and maintain, especially in small apps.

---

## 🔧 **Advanced Concepts**

1. **Render Props Pattern**: A design pattern where a component uses a function as a prop to share code between components, providing flexibility for rendering. This is often used for dynamic UI patterns.
2. **Higher-Order Components (HOCs)**: An advanced pattern in React for reusing component logic. An HOC is a function that takes a component and returns a new component with enhanced functionality (e.g., adding authentication, data fetching, etc.).
3. **Compound Components Pattern**: A pattern that enables components to communicate through implicit state shared between them, providing a flexible API while maintaining encapsulation.
4. **React Context API**: When you need to pass data deeply through your component tree, the Context API provides a way to share values without prop drilling.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – "Patterns" → "Container/Presentational Components"
- "EpicReact.dev by Kent C. Dodds" – "Design Patterns" → "Container/Presentational and Hooks-based"
- "Fullstackopen.com" – "React and State Management" → "Design Patterns"

# 📝 **Monorepo & Component Libraries (Storybook, Bit.dev)**

Monorepo and component libraries help scale development, streamline collaboration, and improve maintainability by centralizing reusable components, UI elements, and shared logic. Tools like **Storybook** and **Bit.dev** provide a structured approach to building and managing component libraries.

---

## 🔧 **Definition**

### **Monorepo**

A **monorepo** is a software development strategy where multiple projects (often related) are stored in a single repository. This can include multiple services, packages, or front-end and back-end components.

Benefits of using a monorepo:

- Easier management of dependencies between projects.
- Simpler version control and release management.
- Better collaboration and code sharing across teams.

---

### **Component Libraries**

A **component library** is a collection of reusable UI components that can be used across different projects or applications. These libraries help maintain consistency in design and improve the efficiency of development by reusing pre-built components.

**Storybook** and **Bit.dev** are popular tools to help create and manage component libraries.

---

### **Storybook**

**Storybook** is an open-source tool for developing UI components in isolation. It provides a sandbox environment where you can build, view, and test UI components independently of your application.

Key features:

- **Component Isolation**: Build and view components without needing a full application context.
- **Interactive Playground**: Test different states of components (e.g., with different props or states).
- **Addons**: Enhance Storybook with useful tools for documentation, accessibility checks, or testing.

---

### **Bit.dev**

**Bit.dev** is a platform for managing and sharing reusable components across projects and teams. It allows teams to create a **distributed component library** where each component is versioned and can be shared across repositories or even organizations.

Key features:

- **Distributed Components**: Components are stored and versioned independently, allowing for more granular control over dependencies and versions.
- **Component Collaboration**: Share, discover, and collaborate on reusable components across teams.
- **Component Usage Tracking**: Track which components are being used where, and manage updates across projects.

---

## 🔧 **Syntax**

### **Storybook Setup Example**

```bash
bash
CopyEdit
# Install Storybook for React
npx sb init

```

Once Storybook is initialized, you can create stories for your components.

```tsx
tsx
CopyEdit
// Button.stories.tsx
import React from 'react';
import { Button } from './Button';

export default {
  title: 'Components/Button',
  component: Button,
};

export const Default = () => <Button label="Click Me" />;
export const Disabled = () => <Button label="Disabled" disabled />;

```

Run Storybook with the following command:

```bash
bash
CopyEdit
npm run storybook

```

---

### **Bit.dev Setup Example**

1. **Install Bit CLI**

```bash
bash
CopyEdit
npm install bit-bin --global

```

1. **Initialize a Bit workspace**:

```bash
bash
CopyEdit
bit init

```

1. **Track components**:

```bash
bash
CopyEdit
bit add src/components/button --main button.js

```

1. **Tag components (create version)**:

```bash
bash
CopyEdit
bit tag --all 1.0.0

```

1. **Export components to Bit.dev**:

```bash
bash
CopyEdit
bit export user.collection

```

---

## 🔧 **Example**

### **Storybook Example: Button Component**

```tsx
tsx
CopyEdit
// Button Component (Button.tsx)
import React from 'react';

type ButtonProps = {
  label: string;
  disabled?: boolean;
};

export const Button: React.FC<ButtonProps> = ({ label, disabled = false }) => {
  return <button disabled={disabled}>{label}</button>;
};

```

```tsx
tsx
CopyEdit
// Storybook for Button Component (Button.stories.tsx)
import React from 'react';
import { Button } from './Button';

export default {
  title: 'Button',
  component: Button,
};

export const Default = () => <Button label="Click Me" />;
export const Disabled = () => <Button label="Disabled" disabled />;

```

Once you've written the story, you can launch Storybook:

```bash
bash
CopyEdit
npm run storybook

```

---

## 🔧 **What to do with it**

1. **Use Storybook to Develop Components in Isolation**: Build, test, and view components in isolation, making it easier to develop UI components without the need for a full application context.
2. **Share and Collaborate on Components with Bit.dev**: Use Bit.dev to share reusable components across different projects and teams, improving collaboration and code reusability.
3. **Version Control and Dependency Management**: With a monorepo, you can manage dependencies and versions of your components more effectively, ensuring that updates and changes are easily integrated into all dependent projects.
4. **Document Your Components**: Use Storybook's documentation capabilities to automatically generate a style guide and interactive documentation for your component library.

---

## 🔧 **What not to do with it**

1. **Avoid Overcomplicating Your Setup**: Don’t overcomplicate your component library by including too many small or unnecessary components. Focus on reusable and modular UI elements.
2. **Don’t Ignore Versioning**: When sharing components across multiple projects, make sure to version your components properly. Using Bit.dev's versioning ensures consistency across your projects.
3. **Don’t Skip Testing**: Make sure your components are well-tested in isolation using Storybook’s integration with testing tools.
4. **Avoid Mixing Components from Different Contexts**: Components should be isolated in their functionality and context. Avoid coupling business logic or app-specific logic directly in your component library.

---

## 🔧 **Advanced Concepts**

1. **Monorepo & Bit.dev Integration**: In a monorepo, Bit.dev can help manage and distribute components independently. It helps you share individual components without needing to publish them as a separate package.
2. **Storybook Addons**: Leverage Storybook’s addons like **Actions**, **Knobs**, and **A11y** to enhance your component development by testing interactivity, customizing inputs, and checking accessibility.
3. **Component Libraries in Large Teams**: Use Bit.dev in larger teams to track which components are being used across different repositories. This helps ensure consistency and avoids duplicate components.
4. **Dynamic Component Generation**: You can create dynamic components with Storybook by passing dynamic data or states via controls, allowing for flexible and interactive component libraries.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – "UI Patterns" → "Component Libraries with Storybook"
- "EpicReact.dev by Kent C. Dodds" – "Reusable Components" → "Building a Component Library with Storybook"
- "Fullstackopen.com" – "React and State Management" → "Advanced UI Patterns"

# 📝 **React Native (Intro)**

**React Native** is a popular framework for building mobile applications using JavaScript and React. It enables developers to create cross-platform applications for both **iOS** and **Android** with a shared codebase, leveraging native components for high performance.

---

## 🔧 **Definition**

**React Native** allows developers to build mobile apps using the same principles as React for web applications. Instead of using web components like `<div>` or `<span>`, React Native uses native components like `<View>`, `<Text>`, and `<Button>`. This enables applications to have the performance of native apps, while maintaining the flexibility and developer experience of React.

React Native components map directly to the platform's native UI components, providing a seamless experience for both users and developers.

---

## 🔧 **Syntax**

React Native uses the same **JSX syntax** as React, but the components are tailored for mobile app development. You can create mobile apps by defining a set of React components, and these components will render native UI elements.

Here's the basic syntax for React Native:

```jsx
jsx
CopyEdit
import React from 'react';
import { View, Text, StyleSheet } from 'react-native';

const App = () => {
  return (
    <View style={styles.container}>
      <Text style={styles.text}>Hello, React Native!</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
  },
  text: {
    fontSize: 20,
  },
});

export default App;

```

---

## 🔧 **Example**

Here's an example of a simple React Native component:

```jsx
jsx
CopyEdit
import React from 'react';
import { View, Text, TouchableOpacity } from 'react-native';

const ButtonComponent = () => {
  const handlePress = () => {
    alert('Button Pressed!');
  };

  return (
    <View style={{ alignItems: 'center', justifyContent: 'center', marginTop: 50 }}>
      <TouchableOpacitystyle={{
          backgroundColor: '#1e90ff',
          paddingVertical: 10,
          paddingHorizontal: 20,
          borderRadius: 5,
        }}
        onPress={handlePress}
      >
        <Text style={{ color: 'white', fontSize: 16 }}>Press Me</Text>
      </TouchableOpacity>
    </View>
  );
};

export default ButtonComponent;

```

---

## 🔧 **What to do with it**

1. **Use Native Components**: React Native allows you to use mobile-specific components like `View`, `Text`, `Image`, `ScrollView`, and more, to build your app’s UI.
2. **Leverage Platform-Specific Features**: With React Native, you can access platform-specific features such as camera, GPS, notifications, etc., using native modules.
3. **Hot Reloading**: React Native provides a powerful feature called **Hot Reloading**, allowing you to instantly see changes in your app without rebuilding it from scratch.
4. **Cross-Platform Development**: React Native allows you to write a single codebase that works across both iOS and Android, helping you save time and effort when developing apps for multiple platforms.

---

## 🔧 **What not to do with it**

1. **Avoid Overusing Native Modules**: While React Native allows you to integrate native modules for certain platform-specific features, overuse of native modules can increase the complexity and reduce the portability of your app.
2. **Don’t Expect Native Performance in All Cases**: While React Native provides high performance for most apps, performance can sometimes lag behind fully native apps, especially for complex animations or highly intensive tasks.
3. **Don’t Skip Optimization**: React Native can lead to memory issues or slower performance if components are not properly optimized. Be sure to use tools like **Hermes** (React Native's JavaScript engine) to optimize performance.

---

## 🔧 **Advanced Concepts**

1. **Native Modules and Native Code Integration**: React Native lets you integrate native code for platform-specific needs. For example, if you need to access a native library that isn't supported by React Native, you can write native code in Java/Swift/Objective-C and link it to React Native.
2. **Navigation in React Native**: For navigation, React Native offers various libraries such as **React Navigation** and **React Native Navigation** to manage app navigation between screens, tabs, and stacks.
3. **State Management**: For handling app-wide state, libraries like **Redux**, **Recoil**, or **Context API** can be used with React Native, similar to how they are used in React for web apps.
4. **Styling in React Native**: React Native uses a styling system similar to CSS, but it doesn’t support all CSS properties. Instead, styles are created with the `StyleSheet` API, which compiles the styles into native code.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – "Core Concepts" → "Introduction to React Native"
- "EpicReact.dev by Kent C. Dodds" – "Advanced React" → "React Native Integration"
- "Fullstackopen.com" – "React Native Basics" → "Setting Up a React Native App"

# 📝 **React Architecture (Folders, Services, Domain Separation)**

In a scalable and maintainable React application, proper architecture is key. A well-structured folder organization helps in managing complexity, promotes reusability, and makes collaboration easier. React’s flexibility allows for multiple approaches to structure, but there are common best practices and patterns.

---

## 🔧 **Definition**

**React Architecture** refers to the way you organize your app's codebase, how you manage services, and how you separate concerns (domains) in your app. A proper architecture ensures that the application remains modular, easy to scale, and maintainable in the long term. Key architectural practices involve:

- **Folder Structure**: Organizing files and folders in a way that makes sense for your project and team.
- **Services**: Managing communication with external APIs, handling business logic, and managing state.
- **Domain Separation**: Dividing the app into well-defined, isolated sections based on functionality (e.g., user authentication, dashboard, admin).

---

## 🔧 **Folder Structure**

A common and scalable folder structure ensures separation of concerns, maintainability, and ease of scaling. Below is a suggested folder structure for a React application:

```
bash
CopyEdit
src/
├── assets/            # Static files like images, fonts, etc.
├── components/        # Reusable UI components (buttons, cards, etc.)
├── services/          # API calls, business logic, etc.
├── features/          # Domain-specific features or modules
│   ├── auth/          # Authentication-related logic (login, signup, etc.)
│   ├── dashboard/     # Dashboard-related components and logic
│   └── user/          # User-related components, API calls, etc.
├── hooks/             # Custom hooks for reusability
├── context/           # React Context for global state management
├── utils/             # Utility functions
├── config/            # Configurations (environment variables, etc.)
├── App.js             # Main application component
└── index.js           # Entry point for React app

```

---

## 🔧 **Services**

**Services** in React typically refer to the abstraction layer that interacts with external APIs, handles business logic, and manages state. Keeping services in a separate folder ensures that API calls and data logic do not clutter the UI components.

Example of a simple API service:

```
js
CopyEdit
// services/api.js
const API_URL = 'https://api.example.com/';

export const fetchData = async (endpoint) => {
  try {
    const response = await fetch(`${API_URL}${endpoint}`);
    if (!response.ok) {
      throw new Error('Network response was not ok');
    }
    return response.json();
  } catch (error) {
    throw new Error('Fetching error: ' + error.message);
  }
};

```

This service can be imported and used in components like so:

```
js
CopyEdit
import { useEffect, useState } from 'react';
import { fetchData } from '../services/api';

const DataFetcher = () => {
  const [data, setData] = useState(null);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetchData('data-endpoint')
      .then(setData)
      .catch(setError);
  }, []);

  if (error) return <div>Error: {error.message}</div>;
  if (!data) return <div>Loading...</div>;

  return <pre>{JSON.stringify(data, null, 2)}</pre>;
};

```

---

## 🔧 **Domain Separation**

Domain separation involves splitting the application into logical domains, each representing a specific functionality. Each domain (or feature) contains everything it needs: UI components, services, hooks, and state management.

For example:

- **Auth Domain**: Handles all authentication-related features like login, logout, and user session management.
- **Dashboard Domain**: Handles the user's dashboard interface, data fetching, and presentation logic.
- **User Domain**: Manages user-related functionalities such as profile settings, preferences, etc.

Here's how you might separate a domain into its own folder structure:

```
bash
CopyEdit
src/
└── features/
    ├── auth/
    │   ├── authService.js   # Service for authentication (login/logout)
    │   ├── authReducer.js   # State management related to authentication
    │   ├── LoginForm.js     # UI component for the login form
    │   └── AuthContext.js   # Context for auth-related global state
    ├── dashboard/
    │   ├── dashboardService.js  # Service for fetching dashboard data
    │   ├── dashboardReducer.js  # State management for the dashboard
    │   └── Dashboard.js         # Dashboard UI component
    └── user/
        ├── userService.js     # Service for handling user data
        ├── userReducer.js     # State management for user data
        └── UserProfile.js     # UI component for the user's profile page

```

By separating each domain, you reduce dependencies between features and keep your application modular and easy to scale.

---

## 🔧 **What to do with it**

1. **Follow Separation of Concerns**: Separate the business logic (services) from UI components to maintain readability and modularity.
2. **Use Services for API Calls**: Keep API logic in a separate service layer to avoid cluttering components with complex data fetching logic.
3. **Organize by Feature or Domain**: Group components, hooks, and services that belong to the same functionality together in one folder.
4. **State Management**: Use context, Redux, or any state management tool within the respective feature/domain folder to manage state efficiently.
5. **Optimize Reusability**: Keep UI components reusable and general-purpose; separate domain-specific logic from reusable components.

---

## 🔧 **What not to do with it**

1. **Don’t Overcomplicate the Folder Structure**: Avoid splitting things into too many small folders unless it’s necessary. It should remain readable and navigable.
2. **Avoid Global Business Logic**: Don’t place business logic in your UI components or in a global file. Always have separate services or hooks for business logic.
3. **Don’t Mix Components Across Features**: Keep domain-specific components within their respective feature/domain folder. Mixing them makes the app harder to scale.

---

## 🔧 **If you want to learn more, visit this page:**

- "React Docs (react.dev)" – "Advanced Guides" → "Architecting Your React App"
- "EpicReact.dev by Kent C. Dodds" – "Code Organization" → "Separation of Concerns"
- "Fullstackopen.com" – "React & State Management" → "Folder Structure Best Practices"
