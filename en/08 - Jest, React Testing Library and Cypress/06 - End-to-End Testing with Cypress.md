
# End-to-End Testing with Cypress

This course introduces Cypress for end-to-end (E2E) testing, enabling full interaction and validation of real browser behavior in modern web apps.

---

## Table of Contents

- [Installing and Configuring Cypress](#installing-and-configuring-cypress)  
- [Cypress Folder Structure and CLI Usage](#cypress-folder-structure-and-cli-usage)  
- [Writing Your First E2E Test](#writing-your-first-e2e-test)  
- [Interacting with the DOM and Simulating User Behavior](#interacting-with-the-dom-and-simulating-user-behavior)  
- [Assertions and Chaining Commands](#assertions-and-chaining-commands)  
- [Working with Fixtures, Aliases, and Custom Commands](#working-with-fixtures-aliases-and-custom-commands)  
- [Network Requests and API Interception (`cy.intercept`)](#network-requests-and-api-interception-cyintercept)  
- [Screenshots, Videos, and Test Reports](#screenshots-videos-and-test-reports)  
- [Handling Authenticated Routes and Sessions](#handling-authenticated-routes-and-sessions)  
- [Debugging Cypress Tests](#debugging-cypress-tests)  
- [Conclusion](#conclusion)

---

## Installing and Configuring Cypress

**Definition**: Cypress is installed as a dev dependency and bootstrapped with a simple CLI command.

**Example**:
```bash
npm install cypress --save-dev
npx cypress open
```

---

## Cypress Folder Structure and CLI Usage

**Definition**: Cypress uses a structured folder layout to organize tests, fixtures, and support files.

**Example**:
```
cypress/
  e2e/         → test specs
  fixtures/    → static test data
  support/     → custom commands and setup
```

Run tests:
```bash
npx cypress run
```

---

## Writing Your First E2E Test

**Definition**: Cypress tests follow the Mocha syntax and run directly in the browser.

**Example**:
```js
describe('Home Page', () => {
  it('loads successfully', () => {
    cy.visit('/');
    cy.contains('Welcome').should('be.visible');
  });
});
```

---

## Interacting with the DOM and Simulating User Behavior

**Definition**: Cypress provides commands to simulate real user interactions.

**Example**:
```js
cy.get('input[name="email"]').type('user@example.com');
cy.get('button[type="submit"]').click();
```

---

## Assertions and Chaining Commands

**Definition**: Cypress uses `should()` and `expect()` for assertions, often chained after actions.

**Example**:
```js
cy.get('.alert').should('contain.text', 'Success');
```

Chaining example:
```js
cy.get('input').type('hello').should('have.value', 'hello');
```

---

## Working with Fixtures, Aliases, and Custom Commands

**Definition**: Fixtures are static files used for mocking; aliases help reuse elements; commands extend Cypress.

**Example**:
```js
cy.fixture('user.json').as('userData');
cy.get('@userData').then(user => {
  cy.get('input[name="email"]').type(user.email);
});
```

Custom command:
```js
Cypress.Commands.add('login', (email, password) => {
  cy.get('#email').type(email);
  cy.get('#password').type(password);
  cy.get('button[type="submit"]').click();
});
```

---

## Network Requests and API Interception (`cy.intercept`)

**Definition**: Intercept and mock HTTP requests to control backend responses in tests.

**Example**:
```js
cy.intercept('GET', '/api/user', { fixture: 'user.json' }).as('getUser');
cy.visit('/');
cy.wait('@getUser');
```

---

## Screenshots, Videos, and Test Reports

**Definition**: Cypress can capture artifacts to assist in debugging and reporting.

**Example**:
```bash
npx cypress run --record
```

In tests:
```js
cy.screenshot();
cy.screenshot('custom-name');
```

Reports configured via plugins like `mochawesome`.

---

## Handling Authenticated Routes and Sessions

**Definition**: You can automate login flows or set session cookies/token programmatically.

**Example**:
```js
cy.setCookie('auth_token', 'abc123');
cy.visit('/dashboard');
```

Or use API login:
```js
cy.request('POST', '/api/login', { username, password })
  .then((resp) => cy.setCookie('auth_token', resp.body.token));
```

---

## Debugging Cypress Tests

**Definition**: Use `.debug()`, `cy.pause()`, and browser dev tools to inspect test states.

**Example**:
```js
cy.get('button').debug();
cy.pause();
```

View logs in the Cypress runner for real-time feedback.

---

## Conclusion

**Key Takeaways**:
1. Cypress enables full E2E browser-based testing with minimal setup.
2. Use `cy.get`, `.type`, `.click`, and `.should` for clear, readable tests.
3. Intercept and mock network requests using `cy.intercept`.
4. Utilize fixtures, aliases, and custom commands for cleaner tests.
5. Debug visually with screenshots, video, and `cy.pause()`.

**Practical Exercise**:
- Create a login test that:
  - Intercepts the login API.
  - Types into form fields.
  - Clicks submit and asserts success.
  - Uses a fixture for user data.
