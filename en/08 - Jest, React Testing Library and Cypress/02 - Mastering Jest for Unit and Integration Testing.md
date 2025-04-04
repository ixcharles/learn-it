
# Mastering Jest for Unit and Integration Testing

Jest is a powerful and flexible testing framework widely used in React applications. This course covers core and advanced features of Jest for writing effective unit and integration tests.

---

## Table of Contents

- [Setting Up Jest in a React Project](#setting-up-jest-in-a-react-project)  
- [Test File Structure and Naming Conventions](#test-file-structure-and-naming-conventions)  
- [Understanding `describe`, `it`, and `test` Blocks](#understanding-describe-it-and-test-blocks)  
- [Matchers and Assertions (`expect`)](#matchers-and-assertions-expect)  
- [Mocks, Spies, and Manual Mocks](#mocks-spies-and-manual-mocks)  
- [Mocking Modules and Dependencies](#mocking-modules-and-dependencies)  
- [Handling Asynchronous Tests with Promises and async/await](#handling-asynchronous-tests-with-promises-and-asyncawait)  
- [Snapshot Testing](#snapshot-testing)  
- [Code Coverage and Configuration](#code-coverage-and-configuration)  
- [Custom Matchers and Extending Jest](#custom-matchers-and-extending-jest)  
- [Conclusion](#conclusion)

---

## Setting Up Jest in a React Project

**Definition**: Jest can be added to any React project with minimal setup. If using Create React App (CRA), Jest is pre-configured.

**Example**:
```bash
npm install --save-dev jest
```

For non-CRA projects, add a test script:
```json
"scripts": {
  "test": "jest"
}
```

---

## Test File Structure and Naming Conventions

**Definition**: Jest automatically finds tests in `__tests__` folders or files ending in `.test.js` or `.spec.js`.

**Example**:
```
/src
  /components
    Button.js
    Button.test.js
```

---

## Understanding `describe`, `it`, and `test` Blocks

**Definition**: Jest organizes tests using `describe`, with individual test cases defined using `test` or `it` (alias).

**Example**:
```js
describe('Math', () => {
  it('adds numbers', () => {
    expect(1 + 2).toBe(3);
  });
});
```

---

## Matchers and Assertions (`expect`)

**Definition**: Jest provides `expect()` with a rich set of matchers to assert expected outcomes.

**Example**:
```js
expect(value).toBe(42);
expect(arr).toContain(3);
expect(obj).toHaveProperty('key');
```

---

## Mocks, Spies, and Manual Mocks

**Definition**: Mocks replace real functions to isolate behavior. Spies track calls to functions.

**Example**:
```js
const mockFn = jest.fn();
mockFn('hello');
expect(mockFn).toHaveBeenCalledWith('hello');
```

---

## Mocking Modules and Dependencies

**Definition**: Jest can mock modules automatically or manually using `jest.mock()`.

**Example**:
```js
jest.mock('./api');
import { fetchData } from './api';

fetchData.mockResolvedValue({ name: 'Test' });
```

---

## Handling Asynchronous Tests with Promises and async/await

**Definition**: Use `async/await` or return a promise to handle async logic in tests.

**Example**:
```js
test('fetches data', async () => {
  const data = await getData();
  expect(data).toBeDefined();
});
```

---

## Snapshot Testing

**Definition**: Jest can serialize and save UI output to compare future renders.

**Example**:
```js
import { render } from '@testing-library/react';
import Button from './Button';

test('renders correctly', () => {
  const { asFragment } = render(<Button>Click</Button>);
  expect(asFragment()).toMatchSnapshot();
});
```

---

## Code Coverage and Configuration

**Definition**: Jest can track which lines of code are tested using `--coverage`.

**Example**:
```bash
npm test -- --coverage
```

Configuration via `jest.config.js`:
```js
module.exports = {
  collectCoverage: true,
  coverageDirectory: "coverage",
};
```

---

## Custom Matchers and Extending Jest

**Definition**: You can write or import custom matchers to improve readability.

**Example**:
```js
expect.extend({
  toBeWithinRange(received, min, max) {
    const pass = received >= min && received <= max;
    return {
      message: () => `expected ${received} to be within ${min} - ${max}`,
      pass,
    };
  },
});

expect(10).toBeWithinRange(5, 15);
```

---

## Conclusion

**Key Takeaways**:
1. Jest is a complete testing framework with built-in mocking, assertions, and coverage.
2. Structure tests clearly using `describe` and `test`.
3. Use mocks to isolate behavior and test edge cases.
4. Handle asynchronous code with `async/await` or returned promises.
5. Snapshot and coverage testing help validate and measure test effectiveness.

**Practical Exercise**:
- Set up a basic utility function and test it using Jest.
- Write one snapshot test for a small component.
- Mock a function that returns a promise and verify its output.
