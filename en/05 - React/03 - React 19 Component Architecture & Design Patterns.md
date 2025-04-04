
# React 19 Component Architecture & Design Patterns

Mastering React’s component architecture and design patterns enables developers to build scalable, maintainable, and reusable UIs. This course focuses on key structural and compositional strategies in React 19.

---

## Table of Contents
- [Component Composition Patterns](#component-composition-patterns)  
  - [Children as Functions](#children-as-functions)  
  - [Compound Components](#compound-components)  
- [Render Props vs Custom Hooks](#render-props-vs-custom-hooks)  
- [Higher-Order Components (HOCs)](#higher-order-components-hocs)  
- [Smart and Dumb Components](#smart-and-dumb-components)  
- [Container and Presentational Components](#container-and-presentational-components)  
- [Controlled vs Uncontrolled Patterns](#controlled-vs-uncontrolled-patterns)  
- [Code Organization and Folder Structure Best Practices](#code-organization-and-folder-structure-best-practices)  
- [Conclusion & Key Takeaways](#conclusion--key-takeaways)  
- [Practical Exercise](#practical-exercise)

---

## Component Composition Patterns

### Children as Functions
**Definition:** A pattern where components accept a function as a child to render dynamic content.  
**Example:**
```jsx
const MouseTracker = ({ children }) => {
  const [pos, setPos] = useState({ x: 0, y: 0 });
  return <div onMouseMove={e => setPos({ x: e.clientX, y: e.clientY })}>{children(pos)}</div>;
};

// Usage
<MouseTracker>{pos => <p>Mouse at {pos.x}, {pos.y}</p>}</MouseTracker>
```

### Compound Components
**Definition:** A group of related components sharing state via context to work as a unified module.  
**Example:**
```jsx
const ToggleContext = createContext();

const Toggle = ({ children }) => {
  const [on, setOn] = useState(false);
  return (
    <ToggleContext.Provider value={{ on, toggle: () => setOn(o => !o) }}>
      {children}
    </ToggleContext.Provider>
  );
};

Toggle.Button = () => {
  const { toggle } = useContext(ToggleContext);
  return <button onClick={toggle}>Toggle</button>;
};

Toggle.Content = ({ children }) => {
  const { on } = useContext(ToggleContext);
  return on ? <div>{children}</div> : null;
};
```

---

## Render Props vs Custom Hooks

**Definition:** Both patterns promote logic reuse, but custom hooks are simpler and more composable in modern React.  
**Render Props Example:**
```jsx
<DataFetcher render={data => <List items={data} />} />
```

**Custom Hook Example:**
```jsx
const data = useDataFetcher();
<List items={data} />
```

---

## Higher-Order Components (HOCs)

**Definition:** Functions that wrap a component to enhance it with additional props or logic.  
**Example:**
```jsx
const withUser = Component => props => {
  const user = useUser();
  return <Component {...props} user={user} />;
};

const ProfileWithUser = withUser(Profile);
```

---

## Smart and Dumb Components

**Definition:** Smart components handle logic and data; dumb (presentational) components focus only on UI rendering.  
**Example:**
```jsx
// Smart
const CommentContainer = () => {
  const comments = useComments();
  return <CommentList comments={comments} />;
};

// Dumb
const CommentList = ({ comments }) => (
  <ul>{comments.map(c => <li key={c.id}>{c.text}</li>)}</ul>
);
```

---

## Container and Presentational Components

**Definition:** A formalized smart/dumb pattern where containers fetch/process data and pass it to stateless presentational components.  
**Example:**
```jsx
const TodoContainer = () => {
  const todos = useTodos();
  return <TodoList todos={todos} />;
};

const TodoList = ({ todos }) => (
  <ul>{todos.map(todo => <li key={todo.id}>{todo.title}</li>)}</ul>
);
```

---

## Controlled vs Uncontrolled Patterns

**Definition:** Controlled components are tied to state via `value` and `onChange`; uncontrolled components use refs for direct DOM access.  
**Controlled Example:**
```jsx
<input value={text} onChange={e => setText(e.target.value)} />
```

**Uncontrolled Example:**
```jsx
<input ref={inputRef} defaultValue="Hello" />
```

---

## Code Organization and Folder Structure Best Practices

**Definition:** Organizing code by feature or component improves scalability and maintainability.  
**Recommended Structure:**
```
/src
  /components
    /Form
      Form.jsx
      Form.css
      index.js
  /hooks
    useForm.js
  /contexts
    ThemeContext.js
  /pages
    Home.jsx
    About.jsx
  /utils
    formatDate.js
```

---

## Conclusion & Key Takeaways

- Component composition (compound, children-as-function) enables flexible UI structures.  
- Custom hooks are the modern solution for logic reuse, replacing HOCs and render props.  
- Smart/presentational patterns separate concerns for cleaner code.  
- Controlled components provide better form and UI state handling.  
- Consistent folder structure aids collaboration and scalability.

---

## Practical Exercise

Build a `Modal` component using the **Compound Component** pattern:
1. Create a `Modal` root component with internal `isOpen` state.
2. Add `Modal.OpenButton`, `Modal.CloseButton`, and `Modal.Content`.
3. Use context to coordinate internal components.
