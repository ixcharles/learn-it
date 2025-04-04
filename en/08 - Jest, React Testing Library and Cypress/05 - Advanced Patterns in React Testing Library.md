
# Advanced Patterns in React Testing Library

This course explores advanced testing strategies with React Testing Library (RTL), focusing on realistic application scenarios like routing, state management, and handling complex component behavior.

---

## Table of Contents

- [Testing with Router, Redux, and Async State Management](#testing-with-router-redux-and-async-state-management)  
- [Testing Error Boundaries and Suspense](#testing-error-boundaries-and-suspense)  
- [Building and Using Custom Render Functions](#building-and-using-custom-render-functions)  
- [Strategies for Reusable Test Utilities](#strategies-for-reusable-test-utilities)  
- [Testing Lazy Loaded Components](#testing-lazy-loaded-components)  
- [Handling Race Conditions and Flaky Tests](#handling-race-conditions-and-flaky-tests)  
- [Structuring Test Suites in Complex Apps](#structuring-test-suites-in-complex-apps)  
- [RTL Best Practices and Anti-Patterns](#rtl-best-practices-and-anti-patterns)  
- [Conclusion](#conclusion)

---

## Testing with Router, Redux, and Async State Management

**Definition**: Wrap components with router and Redux providers to test navigation and global state.

**Example**:
```js
render(
  <Provider store={store}>
    <MemoryRouter initialEntries={['/profile']}>
      <App />
    </MemoryRouter>
  </Provider>
);
expect(screen.getByText(/profile/i)).toBeInTheDocument();
```

---

## Testing Error Boundaries and Suspense

**Definition**: Test fallback UIs by triggering errors or delays in lazy-loaded components.

**Example**:
```js
jest.spyOn(console, 'error').mockImplementation(() => {}); // suppress error output
render(<ErrorBoundary><ComponentThatThrows /></ErrorBoundary>);
expect(screen.getByText(/something went wrong/i)).toBeInTheDocument();
```

Suspense test:
```js
render(
  <Suspense fallback={<span>Loading...</span>}>
    <LazyComponent />
  </Suspense>
);
expect(screen.getByText(/loading/i)).toBeInTheDocument();
```

---

## Building and Using Custom Render Functions

**Definition**: Custom `render` functions centralize providers for cleaner, reusable tests.

**Example**:
```js
const customRender = (ui, options) =>
  render(<AppProviders>{ui}</AppProviders>, options);

// usage
customRender(<Dashboard />);
```

---

## Strategies for Reusable Test Utilities

**Definition**: Extract shared logic, queries, and helpers into test utility files.

**Example**:
```js
// test-utils.js
export const getSubmitButton = () =>
  screen.getByRole('button', { name: /submit/i });
```

Use in test:
```js
import { getSubmitButton } from './test-utils';
expect(getSubmitButton()).toBeEnabled();
```

---

## Testing Lazy Loaded Components

**Definition**: Wrap lazy components in `Suspense` and assert fallback states before resolution.

**Example**:
```js
const LazyPage = React.lazy(() => import('./LazyPage'));
render(
  <Suspense fallback={<span>Loading...</span>}>
    <LazyPage />
  </Suspense>
);
expect(screen.getByText(/loading/i)).toBeInTheDocument();
```

---

## Handling Race Conditions and Flaky Tests

**Definition**: Use `waitFor`, assert intermediate states, and avoid `setTimeout`-based tests.

**Tips**:
- Always assert loading indicators.
- Avoid relying on fixed delays.
- Prefer `findBy*` for async queries.

---

## Structuring Test Suites in Complex Apps

**Definition**: Group tests logically by domain, feature, or user flow.

**Example**:
```
/__tests__
  /auth
    login.test.js
  /dashboard
    widgets.test.js
```

Use `describe()` blocks for grouping:
```js
describe('Dashboard Widgets', () => {
  test('loads metrics', () => {});
});
```

---

## RTL Best Practices and Anti-Patterns

**Best Practices**:
- Use queries that reflect user interaction (e.g., `getByRole`, `getByLabelText`).
- Prefer `userEvent` over `fireEvent`.

**Anti-Patterns**:
- Avoid `getByTestId` unless necessary.
- Avoid implementation details like internal state or class names.

---

## Conclusion

**Key Takeaways**:
1. Use providers and wrappers to simulate realistic app environments.
2. Abstract test setup with reusable custom render functions.
3. Handle async UI safely with `waitFor`, `findBy`, and Suspense fallbacks.
4. Keep tests focused, organized, and readable with shared utilities.
5. Avoid relying on DOM implementation details and unstable test IDs.

**Practical Exercise**:
- Create a lazy-loaded profile page with a fallback.
- Test rendering it with `React.Suspense`.
- Simulate a Redux-driven toggle and assert the UI changes.
