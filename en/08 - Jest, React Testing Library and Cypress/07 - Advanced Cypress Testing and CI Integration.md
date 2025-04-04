
# Advanced Cypress Testing and CI Integration

This course covers advanced Cypress features including component testing, cross-browser support, performance, CI/CD integration, and scalable testing practices for modern applications.

---

## Table of Contents

- [Component Testing with Cypress](#component-testing-with-cypress)  
- [Parallelization and Load Balancing in Test Runs](#parallelization-and-load-balancing-in-test-runs)  
- [Managing Flaky and Dynamic Content](#managing-flaky-and-dynamic-content)  
- [Testing Performance and Accessibility in Cypress](#testing-performance-and-accessibility-in-cypress)  
- [Cross-Browser and Mobile Testing](#cross-browser-and-mobile-testing)  
- [Integrating Cypress in CI/CD Pipelines](#integrating-cypress-in-cicd-pipelines)  
- [Writing Scalable Cypress Test Suites](#writing-scalable-cypress-test-suites)  
- [Environment Configuration and Secrets Management](#environment-configuration-and-secrets-management)  
- [Cypress Plugins and Extending Functionality](#cypress-plugins-and-extending-functionality)  
- [Migrating Tests Between Frameworks (Jest ⇄ Cypress)](#migrating-tests-between-frameworks-jest-⇄-cypress)  
- [Conclusion](#conclusion)

---

## Component Testing with Cypress

**Definition**: Test individual React components in isolation using Cypress component testing mode.

**Example**:
```js
import MyComponent from './MyComponent';
describe('MyComponent', () => {
  it('renders correctly', () => {
    cy.mount(<MyComponent />);
    cy.contains('Hello').should('exist');
  });
});
```

---

## Parallelization and Load Balancing in Test Runs

**Definition**: Split test execution across machines to reduce total run time using Cypress Dashboard.

**Example**:
```bash
npx cypress run --record --parallel --group e2e-tests
```

Ensure your project is set up with `cypress.json` and a `projectId`.

---

## Managing Flaky and Dynamic Content

**Definition**: Handle timing inconsistencies and non-deterministic content with retries and proper waits.

**Best Practices**:
- Avoid hard `wait()`, prefer `cy.wait('@alias')`.
- Use `should()` and `retry-ability`.

**Example**:
```js
cy.get('.alert').should('contain.text', 'Success');
```

---

## Testing Performance and Accessibility in Cypress

**Definition**: Leverage plugins to run a11y and perf audits (e.g. Lighthouse, Axe).

**Example**:
```js
import 'cypress-axe';
cy.injectAxe();
cy.checkA11y();
```

Performance test using `cypress-audit`:
```bash
npx cypress run --spec 'performance.cy.js'
```

---

## Cross-Browser and Mobile Testing

**Definition**: Run tests in multiple browsers and viewports.

**Example**:
```bash
npx cypress run --browser chrome
```

Set viewport:
```js
cy.viewport('iphone-6');
cy.visit('/');
```

---

## Integrating Cypress in CI/CD Pipelines

**Definition**: Run tests headlessly in CI tools like GitHub Actions, GitLab CI, CircleCI, etc.

**GitHub Actions Example**:
```yaml
- name: Run Cypress tests
  uses: cypress-io/github-action@v4
  with:
    record: true
    start: npm start
    wait-on: 'http://localhost:3000'
```

---

## Writing Scalable Cypress Test Suites

**Definition**: Organize test cases modularly, group by domain or user flows.

**Best Practices**:
- Reuse custom commands.
- Modularize selectors and constants.

**Example**:
```
/cypress/
  /e2e/
    login.cy.js
    dashboard.cy.js
  /support/
    commands.js
    selectors.js
```

---

## Environment Configuration and Secrets Management

**Definition**: Use `cypress.config.js` or environment variables for managing secrets and configs.

**Example**:
```js
// cypress.config.js
env: {
  apiUrl: 'https://api.example.com',
  username: process.env.USERNAME,
}
```

Use in test:
```js
cy.request(`${Cypress.env('apiUrl')}/users`);
```

---

## Cypress Plugins and Extending Functionality

**Definition**: Extend Cypress via plugins (file uploads, visual diffs, etc.)

**Example**:
```js
// cypress/plugins/index.js
const injectDevServer = require('@cypress/react/plugins/react-scripts');
module.exports = (on, config) => {
  injectDevServer(on, config);
  return config;
};
```

Popular plugins:
- `cypress-axe`
- `cypress-audit`
- `cypress-file-upload`

---

## Migrating Tests Between Frameworks (Jest ⇄ Cypress)

**Definition**: Adapt unit/integration tests to Cypress component tests or vice versa.

**Strategies**:
- Extract shared logic into test utils.
- Use `mount()` in Cypress as alternative to `render()` in Jest.
- Translate `userEvent` → `cy.get().type()` / `click()`.

**Example**:
Jest:
```js
render(<Login />);
userEvent.click(screen.getByText('Submit'));
```

Cypress:
```js
cy.mount(<Login />);
cy.contains('Submit').click();
```

---

## Conclusion

**Key Takeaways**:
1. Cypress supports full E2E and component testing with powerful debugging tools.
2. Integrate into CI/CD pipelines with parallelization for speed.
3. Improve test quality with accessibility and performance plugins.
4. Organize and scale your test architecture for large projects.
5. Use environment variables and plugins to maintain flexibility and security.

**Practical Exercise**:
- Set up a CI pipeline that:
  - Runs Cypress tests in parallel.
  - Includes an a11y check using `cypress-axe`.
  - Uses environment variables for auth tokens.
