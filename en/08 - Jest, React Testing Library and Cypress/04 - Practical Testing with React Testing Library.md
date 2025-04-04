
# Practical Testing with React Testing Library

React Testing Library (RTL) promotes testing components in a way that simulates real user interactions. This course focuses on using RTL effectively to write tests that reflect how users interact with your React app.

---

## Table of Contents

- [Setting Up React Testing Library (RTL)](#setting-up-react-testing-library-rtl)  
- [Queries: `getBy`, `queryBy`, `findBy`, and Their Variants](#queries-getby-queryby-findby-and-their-variants)  
- [Rendering Components and Working with JSX](#rendering-components-and-working-with-jsx)  
- [Simulating User Interactions with `fireEvent` and `userEvent`](#simulating-user-interactions-with-fireevent-and-userevent)  
- [Testing Forms and Controlled Components](#testing-forms-and-controlled-components)  
- [Assertions for DOM Elements and Accessibility](#assertions-for-dom-elements-and-accessibility)  
- [Working with Portals and Modals](#working-with-portals-and-modals)  
- [Testing Hooks and Custom Hooks](#testing-hooks-and-custom-hooks)  
- [Mocking Contexts and Providers](#mocking-contexts-and-providers)  
- [Using `waitFor`, `waitForElementToBeRemoved`, and `act`](#using-waitfor-waitforelementtoberemoved-and-act)  
- [Conclusion](#conclusion)

---

## Setting Up React Testing Library (RTL)

**Definition**: RTL integrates with Jest and can be installed in any React project.

**Example**:
```bash
npm install --save-dev @testing-library/react @testing-library/jest-dom
```

---

## Queries: `getBy`, `queryBy`, `findBy`, and Their Variants

**Definition**: Queries are functions for selecting elements in the DOM.

- `getBy`: Throws if not found.
- `queryBy`: Returns null if not found.
- `findBy`: Asynchronous version of `getBy`.

**Example**:
```js
const button = screen.getByRole('button', { name: /submit/i });
```

---

## Rendering Components and Working with JSX

**Definition**: Use `render()` to render components inside a virtual DOM for testing.

**Example**:
```js
import { render, screen } from '@testing-library/react';
render(<button>Click Me</button>);
expect(screen.getByText('Click Me')).toBeInTheDocument();
```

---

## Simulating User Interactions with `fireEvent` and `userEvent`

**Definition**: `userEvent` simulates real user behavior; `fireEvent` triggers native events directly.

**Example**:
```js
import userEvent from '@testing-library/user-event';
userEvent.type(input, 'hello');
userEvent.click(button);
```

---

## Testing Forms and Controlled Components

**Definition**: Test form behavior by simulating input and submit actions.

**Example**:
```js
const input = screen.getByLabelText(/name/i);
userEvent.type(input, 'John');
expect(input).toHaveValue('John');
```

---

## Assertions for DOM Elements and Accessibility

**Definition**: Use `@testing-library/jest-dom` for improved, semantic assertions.

**Example**:
```js
expect(button).toBeEnabled();
expect(label).toHaveAccessibleName('Username');
```

---

## Working with Portals and Modals

**Definition**: Test modals rendered outside the DOM tree by querying globally.

**Example**:
```js
expect(screen.getByRole('dialog')).toBeVisible();
```

If needed, append modal container to `document.body` during setup.

---

## Testing Hooks and Custom Hooks

**Definition**: Use `@testing-library/react-hooks` (deprecated) or wrap hooks in test components.

**Example**:
```js
function TestComponent() {
  const value = useCustomHook();
  return <div>{value}</div>;
}
render(<TestComponent />);
expect(screen.getByText('expected value')).toBeInTheDocument();
```

---

## Mocking Contexts and Providers

**Definition**: Wrap components with context providers to supply mocked values.

**Example**:
```js
render(
  <AuthContext.Provider value={{ user: 'Jane' }}>
    <Profile />
  </AuthContext.Provider>
);
```

---

## Using `waitFor`, `waitForElementToBeRemoved`, and `act`

**Definition**: Use these helpers to handle async behavior and DOM updates.

**Example**:
```js
await waitFor(() => {
  expect(screen.getByText(/loaded/i)).toBeInTheDocument();
});
await waitForElementToBeRemoved(() => screen.queryByText(/loading/i));
```

---

## Conclusion

**Key Takeaways**:
1. RTL promotes user-centric testing by querying and interacting like a real user.
2. Use `userEvent` for more accurate simulations.
3. Wrap components in context providers when necessary.
4. Handle async operations using `findBy`, `waitFor`, and `act`.
5. Use `jest-dom` for better, accessible assertions.

**Practical Exercise**:
- Create a simple form with a text input and submit button.
- Test typing into the input and submitting the form.
- Use `waitFor` to test async validation message rendering.
