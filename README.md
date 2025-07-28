[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19993957&assignment_repo_type=AssignmentRepo)
# Testing and Debugging MERN Applications

This assignment focuses on implementing comprehensive testing strategies for a MERN stack application, including unit testing, integration testing, and end-to-end testing, along with debugging techniques.

## Assignment Overview

You will:
1. Set up testing environments for both client and server
2. Write unit tests for React components and server functions
3. Implement integration tests for API endpoints
4. Create end-to-end tests for critical user flows
5. Apply debugging techniques for common MERN stack issues

## Project Structure

```
mern-testing/
├── client/                 # React front-end
│   ├── src/                # React source code
│   │   ├── components/     # React components
│   │   ├── tests/          # Client-side tests
│   │   │   ├── unit/       # Unit tests
│   │   │   └── integration/ # Integration tests
│   │   └── App.jsx         # Main application component
│   └── cypress/            # End-to-end tests
├── server/                 # Express.js back-end
│   ├── src/                # Server source code
│   │   ├── controllers/    # Route controllers
│   │   ├── models/         # Mongoose models
│   │   ├── routes/         # API routes
│   │   └── middleware/     # Custom middleware
│   └── tests/              # Server-side tests
│       ├── unit/           # Unit tests
│       └── integration/    # Integration tests
├── jest.config.js          # Jest configuration
└── package.json            # Project dependencies
```

## Getting Started

1. Accept the GitHub Classroom assignment invitation
2. Clone your personal repository that was created by GitHub Classroom
3. Follow the setup instructions in the `Week6-Assignment.md` file
4. Explore the starter code and existing tests
5. Complete the tasks outlined in the assignment

## Files Included

- `Week6-Assignment.md`: Detailed assignment instructions
- Starter code for a MERN application with basic test setup:
  - Sample React components with test files
  - Express routes with test files
  - Jest and testing library configurations
  - Example tests for reference

## Requirements

- Node.js (v18 or higher)
- MongoDB (local installation or Atlas account)
- npm or yarn
- Basic understanding of testing concepts

## Testing Tools

- Jest: JavaScript testing framework
- React Testing Library: Testing utilities for React
- Supertest: HTTP assertions for API testing
- Cypress/Playwright: End-to-end testing framework
- MongoDB Memory Server: In-memory MongoDB for testing

## Submission

Your work will be automatically submitted when you push to your GitHub Classroom repository. Make sure to:

1. Complete all required tests (unit, integration, and end-to-end)                                                                                                      Client (React Front-end)
Unit tests:

Which components should be covered?
E.g.:

A form input (with validation logic)?

A reusable Button or Navbar?

A custom hook (e.g. useApi, useFormState)?

Integration tests:

Are there component interactions or flows you'd like covered?
E.g.:

Form submission triggers API call and updates UI.

Parent-child component data passing and state updates.

2. Server (Express + Mongoose Back-end)
Unit tests:

Which controllers or utilities?

E.g. user registration controller, authentication middleware, data validation logic.

Integration tests:

Which routes and model interactions?

E.g. /api/users, /api/posts: test request to route → controller → mock DB → response.

Do you want to mock the database (e.g. using mongodb-memory-server) or use a test MongoDB instance?

3. End-to-End (Cypress)
Are there specific user flows to automate?

Common scenarios:

Sign up / log in → create data (e.g. a “post”) → view or edit it.

Form submission and UI feedback.

Do you have login credentials or test accounts beforehand? Any seed data?

                
2. Achieve at least 70% code coverage for unit tests                                                                                                                     module.exports = {
  collectCoverage: true,
  coverageDirectory: 'coverage',
  collectCoverageFrom: [
    'client/src/**/*.{js,jsx}',
    'server/src/**/*.{js,ts}',
    '!**/node_modules/**',
    '!**/tests/**',
  ],
  coverageThreshold: {
    global: {
      branches: 70,
      functions: 70,
      lines: 70,
      statements: 70,
   import { render, screen, fireEvent } from '@testing-library/react';
import Button from '../../components/Button';

describe('Button component', () => {
  test('renders button text', () => {
    render(<Button>Click me</Button>);
    expect(screen.getByText('Click me')).toBeInTheDocument();
  });

  test('calls onClick handler when clicked', () => {
    const onClick = jest.fn();
    render(<Button onClick={onClick}>Click</Button>);
    fireEvent.click(screen.getByText('Click'));
    expect(onClick).toHaveBeenCalledTimes(1);               
4. Document your testing strategy in the README.md                                                                                                                      Testing Strategy

This project follows a comprehensive testing strategy to ensure code quality and reliability across the full MERN stack. The testing approach covers **unit tests**, **integration tests**, and **end-to-end (E2E) tests**.

---

## 1. Unit Tests

### Purpose
Unit tests focus on testing individual components, functions, or modules in isolation to verify their correctness. This includes:

- React components and hooks (client)
- Express controllers, middleware, and utility functions (server)

### Tools
- **Jest**: Test runner and assertion library.
- **React Testing Library**: For testing React components.
- **Jest Mocks**: To mock dependencies such as Mongoose models on the server.

### Location
- Client unit tests: `client/src/tests/unit/`
- Server unit tests: `server/tests/unit/`

### Coverage
We aim to maintain at least **70% code coverage** for unit tests to ensure critical parts of the codebase are well-tested.

### Running Tests
```bash
npm run test:unit
5. Include screenshots of your test coverage reports                                                                                                                     Test Coverage Reports

Here are screenshots showing our current test coverage status.

### Coverage Summary

![Coverage Summary](docs/images/coverage-summary.png)

### Component Coverage Example

![Component Coverage](docs/images/component-coverage.png)            
6. Demonstrate debugging techniques in your code
import React, { useEffect, useState } from 'react';

export default function UserProfile({ userId }) {
  const [user, setUser] = useState(null);

  useEffect(() => {
    console.log('UserProfile mounted for userId:', userId);  // Debug start of effect
    fetch(`/api/users/${userId}`)
      .then((res) => res.json())
      .then((data) => {
        console.log('Fetched user data:', data);  // Debug fetched data
        setUser(data);
      })
      .catch((err) => {
        console.error('Error fetching user:', err);  // Debug fetch error
      });
  }, [userId]);

  if (!user) return <p>Loading...</p>;

  return (
    <div>
      <h1>{user.name}</h1>
      {/* ... */}
    </div>
  );
}
## Resources

- [Jest Documentation](https://jestjs.io/docs/getting-started)
- [React Testing Library Documentation](https://testing-library.com/docs/react-testing-library/intro/)
- [Supertest Documentation](https://github.com/visionmedia/supertest)
- [Cypress Documentation](https://docs.cypress.io/)
- [MongoDB Testing Best Practices](https://www.mongodb.com/blog/post/mongodb-testing-best-practices) 
