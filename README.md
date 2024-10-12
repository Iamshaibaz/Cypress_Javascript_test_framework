# Cypress_Javascript_test_framework

## Cypress Test Automation Setup

This project demonstrates how to set up and run automated tests using [Cypress](https://www.cypress.io/).

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (version 12 or higher)
- **npm** (comes with Node.js) or **yarn**
- **Git**

### Checking Installed Versions

To verify that Node.js and npm are installed, run the following commands in your terminal:

```bash
node -v
npm -v
```

If Node.js and npm are not installed, download and install them from [here](https://nodejs.org/).

## Project Setup

1. **Clone the repository**:
    ```bash
    git clone https://github.com/your-username/your-repo-name.git
    cd your-repo-name
    ```

2. **Install Cypress** and other project dependencies:
    ```bash
    npm install cypress --save-dev
    ```

3. **Open Cypress** to verify the installation:
    ```bash
    npx cypress open
    ```

This will launch the Cypress Test Runner where you can start running your tests.

## Folder Structure

Once Cypress is installed, you will have the following directory structure:

```
cypress/
  ├── fixtures/    # Test data files in JSON format
  ├── integration/ # Test files (your test cases go here)
  ├── plugins/     # Extend Cypress with plugins
  └── support/     # Helper files like custom commands
cypress.json        # Cypress configuration file
```

### Test Files

Place your test files under the `cypress/integration/` folder. Test files should typically have the `.spec.js` extension.

## Running Tests

You can run tests in different modes depending on your requirements:

1. **Interactive Mode (with Cypress UI)**:
    ```bash
    npx cypress open
    ```
   This opens the Cypress Test Runner where you can run individual test files interactively.

2. **Headless Mode (without Cypress UI)**:
    ```bash
    npx cypress run
    ```
   This runs all tests in the command line, which is especially useful for CI/CD pipelines.

## Example Test

Here is a simple example of a Cypress test:

```javascript
describe('My First Test', () => {
  it('Visits the app and checks for a title', () => {
    cy.visit('/')
    cy.title().should('include', 'My App')
  })
})
```

## Cypress Configuration

The `cypress.json` file is used to configure your Cypress setup. For example:

```json
{
  "baseUrl": "http://localhost:3000",
  "viewportWidth": 1280,
  "viewportHeight": 720,
  "defaultCommandTimeout": 6000,
  "chromeWebSecurity": false
}
```

## Continuous Integration (CI)

To integrate Cypress with a CI service (like GitHub Actions or GitLab CI), use the following configuration:

### GitHub Actions Example

Here is an example workflow for running Cypress tests on GitHub Actions:

```yaml
name: Run Cypress Tests

on: [push, pull_request]

jobs:
  cypress-run:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Install Node.js
        uses: actions/setup-node@v2
        with:
          node-version: 16

      - name: Install dependencies
        run: npm install

      - name: Run Cypress tests
        run: npx cypress run
```

## Writing Tests

Tests in Cypress are written using JavaScript. Here's a basic example:

```javascript
describe('Simple Test', () => {
  it('Checks if a button exists', () => {
    cy.visit('https://example.com')
    cy.get('button').should('exist')
  })
})
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
