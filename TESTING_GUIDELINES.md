# Educado Testing Guidelines

This document provides a comprehensive guide to using Jest for unit testing, and Cypress for E2E testing. 
Guidelines includes focus on structuring your tests to help you write efficient, uniform, and organized test suites. This guide also specifies which directory folder structure to use, and the file naming convention.

> **✔️ Do: ✔️**\
> use Jest for unit testing _backend_.

> **✔️ Do: ✔️**\
> use Jest for unit testing utility functions only in _mobile_ and _frontend_.

> **✔️ Do: ✔️**\
> use Cypress for E2E testing in _frontend_. 

> **⚠️ Don't: ⚠️**\
> use Jest for snapshot/UI testing in _mobile_ and _frontend_.

> **⚠️ Don't: ⚠️**\
> use Cypress for E2E testing in _mobile_.
> _(As of 2023-Nov-28 it does not work well with React Native)_


## Table of contentss
- [History](#History)
- [Prerequisites](#Prerequisites)
- [Jest unit testing](#Jest-unit-testing)
  - [Where to put unit tests?](#Where-to-put-unit-tests?)
  - [What should i name my unit test files?](#What-should-i-name-my-unit-test-files?)
  - [When testing endpoints](#When-testing-endpoints)
  - [How to structure unit tests?](#How-to-structure-unit-tests?)
  - [Running unit tests](#Running-unit-tests)
- [Cypress E2E testing](#Cypress-E2E-testing)
  - [Where to put E2E tests?](#Where-to-put-E2E-tests)
  - [What should i name my unit test files?](#What-should-i-name-my-unit-test-files?)
  - [How to structure E2E tests?](#How-to-structure-E2E-tests?)
  - [Running E2E tests](#Running-E2E-tests)


## History

<details>
  <summary>Expand change history</summary>
  
| Date        | Notes                                                                        |
| ----------- | ---------------------------------------------------------------------------- |
| 2023-Oct-12 | 1st release of testing guidelines                                            |
| 2023-Oct-12 | Changed formulation of test cases                                            |
| 2023-Nov-17 | Changed convention of Describe when endpoint testing                         |
| 2023-Nov-28 | Refactor and added Cypress                                                   |

</details>


## Prerequisites

Before you begin, ensure that you have Node.js and npm (Node Package Manager) installed on your system. If you suspect that a dependency is missing, try to install missing packages using npm:
```bash
npm i
```

# Jest unit testing

## Where to put unit tests?

Each repo contains a  `__tests__` folder (in mobile this folder is simply called `__test__`), which should follow the same folder path structure as the actual files you want to test.
- <i>Folder structure example with mailRoutes:</i>

```
Educado-backend
│
├── __tests__
│   ├── routes
│   │   └──mailRoutes.test.js
│   └── ...
│
└── routes
    ├── mailRoutes.js
    └ ...
```

So if your file is inside a route folder, you should add your test file inside a router folder, inside the test folder.

## What should i name my unit test files?

you should use the same name for your test file, as the actual file you are trying to test, and use .test.js as the postfix.
- e.g: <b>homePage.js</b> ---> <i>test file will be named</i> ---> <b>homePage.test.js</b>


> **✔️ Do: ✔️**\
> use <b>.test.js</b> as postfix.

> **⚠️ Don't: ⚠️**\
> use <b>.spec.js</b> as postfix.

### When testing endpoints:

> **✔️ Do: ✔️**\
> Use the HTTP method and endpoint url as **describe()** parameter.
>
> for example: **describe('GET /students/:id/subscriptions')**

> **⚠️ Don't: ⚠️**\
> Just name it whatever you feel.
>
> _The describe() convention with url endpoints makes it easier to write TEST_DOCUMENTATION upon releases._

## How to structure unit tests?

To ensure a uniform at descriptive way of structuring tests among developer teams, we commit to using below functions:
### `describe(name, function)`
used to create a block, that groups related tests together. Test cases should always be inside `describe()` blocks. The block should contain a name and a function as parameters, <i>eg</i>:
```javascript
describe('Cats', () => {
  // test logic here
});
```
<i>More info can be found here: https://jestjs.io/docs/api#describename-fn</i>

### `it(name, function)`

used to define an individual test within a test suite. The test case should contain a name that describes the test, and a function, <i>e.g</i>:

```javascript
describe('Cats', () => {
    it('Scratches when angry', () => {
        // specific test here
    });

    it('Meows when hungry', () => {
        // specific test here
    });
});

describe('Dogs', () => {
    it('Barks when bored', () => {
        // specific test here
    });
});
```

> **✔️ Do: ✔️**\
> use `it()`.

> **⚠️ Don't: ⚠️**\
> use `test()`.

<i>More info can be found here: https://jestjs.io/docs/api#testname-fn-timeout</i>

### `beforeAll(function)`

A setup function that allows you to define code that should run once before any of the test cases within a describe block are executed. <i>e.g:</i>

```javascript
describe('Cats', () => {

    beforeAll(() => {
        // initializations/setup before all test in this block
    });

    it('Scratches when angry', () => {
        // specific test here
    });

    it('Meows when hungry', () => {
        // specific test here
    });
});

describe('Dogs', () => {

    beforeAll(() => {
        // initializations/setup before all test in this block
    });

    it('Barks when bored', () => {
        // specific test here
    });
});
```



### `afterAll(function)` 

Runs once after all the test cases within a describe block have completed, allowing you to perform cleanup tasks or release shared resources used in your test suite. <i>e.g:</i>

```javascript
...
describe('Dogs', () => {

    beforeAll(() => {
        // initializations/setup before all test in this block
    });

    it('Barks when bored', () => {
        // specific test here
    });

    afterAll(() => {
        // perform clean up, like close mock db, etc.
    });
});
```

<i>More info can be found here: https://jestjs.io/docs/api#beforeallfn-timeout</i>

### `beforeEach()` 
A setup function that runs before each individual test case within a describe block, providing a way to set up a consistent starting state or resources for each test case. <i>e.g:</i>

```javascript
...
describe('Dogs', () => {

    beforeAll(() => {
        // initializations/setup before all test in this block
    });

    beforeEach(() => {
        // set up resource or start state
    });

    it('Barks when bored', () => {
        // specific test here
    });

    afterAll(() => {
        // perform clean up, like close mock db, etc.
    });
});
```

<i>More info can be found here: https://jestjs.io/docs/api#beforeeachfn-timeout</i>

### `afterEach()`

A function that runs after each individual test case within a describe block, allowing you to clean up or reset resources, ensuring a clean state before the next test case is executed.

```javascript
...
describe('Dogs', () => {

    beforeAll(() => {
        // initializations/setup before all test in this block
    });

    beforeEach(() => {
        // set up resource or start state
    });

    it('Barks when bored', () => {
        // specific test here
    });

    afterEach(() => {
        // perform clean up or reset resources or state etc.
    });

    afterAll(() => {
        // perform clean up, like close mock db, etc.
    });
});
```

<i>More info can be found here: https://jestjs.io/docs/api#aftereachfn-timeout</i>

## Running unit tests

All tests in the repository can be run using:

```bash
npm run test
```
If you want to run tests in a specific file only, this can be done with the following command:
- in below example, the file you want to test is named register.test.js
```bash
npm test register
```

# Cypress E2E testing

## Where to put E2E tests?

The frontend repo contains a `cypress` folder, which contains `E2E` and `fixtures` folders. `E2E` contains the actual tests, while `fixtures` contains utilities.
- <i>Folder structure example with CoursePage:</i>

```
EDUCADO-FRONTEND
├── app
|    ├── cypress
|    |    ├── E2E
|    |    |    ├── courses
|    |    |    |     └── CoursePage.cy.ts
|    |    |    ...
│    |    └── fixtures
│    └── ...
...
```

So if your file is inside a `Courses` folder, you should add your test file inside a `Courses` folder.

## What should i name my unit test files?

you should use the same name for your test file, as the actual file you are trying to test, and use `.cy.ts` as the postfix.

## How to structure E2E tests?

To ensure a uniform at descriptive way of structuring tests among developer teams, we commit to using below functions:
### `describe(name, function)`
used to create a block, that groups related tests together. Test cases should always be inside `describe()` blocks. The block should contain a name and a function as parameters, <i>eg</i>:
```javascript
describe('Cats', () => {
  // test logic here
});
```
<i>More info can be found here: [Cypress docs](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests#Test-Structure)</i>

### `it(name, function)`

used to define an individual test within a test suite. The test case should contain a name that describes the test, and a function, <i>e.g</i>:
- e.g: <b>CoursePage.ts</b> ---> <i>test file will be named</i> ---> <b>CoursePage.cy.ts</b>

> **✔️ Do: ✔️**\
> use <b>.cy.ts</b> as postfix.

### `before(function)`

A setup function that allows you to define code that should run once before any of the test cases within a describe block are executed. <i>e.g:</i>

```javascript
describe('Cats', () => {

    before(() => {
        // initializations/setup before all test in this block
    });

    it('Scratches when angry', () => {
        // specific test here
    });

    it('Meows when hungry', () => {
        // specific test here
    });
});

describe('Dogs', () => {

    before(() => {
        // initializations/setup before all test in this block
    });

    it('Barks when bored', () => {
        // specific test here
    });
});
```



### `after(function)` 

Runs once after all the test cases within a describe block have completed, allowing you to perform cleanup tasks or release shared resources used in your test suite. <i>e.g:</i>

```javascript
...
describe('Dogs', () => {

    before(() => {
        // initializations/setup before all test in this block
    });

    it('Barks when bored', () => {
        // specific test here
    });

    after(() => {
        // perform clean up, like close mock db, etc.
    });
});
```

<i>More info can be found here: [Cypress docs](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests#Hooks)</i>

### `beforeEach()` 
A setup function that runs before each individual test case within a describe block, providing a way to set up a consistent starting state or resources for each test case. <i>e.g:</i>

```javascript
...
describe('Dogs', () => {

    before(() => {
        // initializations/setup before all test in this block
    });

    beforeEach(() => {
        // set up resource or start state
    });

    it('Barks when bored', () => {
        // specific test here
    });

    after(() => {
        // perform clean up, like close mock db, etc.
    });
});
```

<i>More info can be found here: [Cypress docs](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests#Hooks)</i>

### `afterEach()`

A function that runs after each individual test case within a describe block, allowing you to clean up or reset resources, ensuring a clean state before the next test case is executed.

```javascript
...
describe('Dogs', () => {

    before(() => {
        // initializations/setup before all test in this block
    });

    beforeEach(() => {
        // set up resource or start state
    });

    it('Barks when bored', () => {
        // specific test here
    });

    afterEach(() => {
        // perform clean up or reset resources or state etc.
    });

    after(() => {
        // perform clean up, like close mock db, etc.
    });
});
```

<i>More info can be found here: [Cypress docs](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests#Hooks)</i>

## Running E2E tests

When running Cypress tests, it is important to have a server running. This can be done with following command:

```bash
npm run cypress-server
```
After making sure the server is running, tests can be run using following command:
```bash
npx cypress open
```

