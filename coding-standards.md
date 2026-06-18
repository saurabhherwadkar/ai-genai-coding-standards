# Coding Standards

> Given this code base only in this folder, DO NOT change the core functionality since it is working.
> Apply the following standards very slowly, step by step.

---

## Table of Contents

1. [Single Responsibility Principle](#single-responsibility-principle)
2. [Refactoring](#refactoring)
3. [Commenting](#commenting)
4. [Unit Testing](#unit-testing)
5. [Framework and Dependency Management](#framework-and-dependency-management)
6. [Logging](#logging)
7. [Naming Conventions](#naming-conventions)
8. [Security and Vulnerability Management](#security-and-vulnerability-management)
9. [Error Handling](#error-handling)
10. [Performance Optimization](#performance-optimization)
11. [Spacing and Linting](#spacing-and-linting)
12. [Async and Decoupled Patterns](#async-and-decoupled-patterns)
13. [README.md Standards](#readmemd-standards)
14. [.gitignore](#gitignore)
15. [External Configuration](#external-configuration)

---

## Single Responsibility Principle

- Each function or class should have a well-defined single responsibility.
- A function should do one thing and do it well.
- If a function name requires "and" to describe it, split it into two functions.
- Classes should encapsulate one cohesive concept or domain entity.

---

## Refactoring

- Refactor code into as many methods and supporting classes as required.
- Extract reusable logic into helper or utility methods.
- Group related methods into dedicated classes or modules.
- Eliminate code duplication by identifying shared patterns.
- Keep methods short — aim for no more than 20–30 lines per method.

---

## Commenting

- Add plenty of commenting for anyone to understand the code base.
- Add one code comment per line explaining what the line does and why.
- Every file should have a header comment describing its purpose.
- Every function should have a docstring explaining its parameters, return value, and behavior.
- Every class should have a docstring explaining its responsibility.
- Use inline comments to clarify non-obvious logic or business rules.

---

## Unit Testing

- Write unit test cases for the entire code base for maximum possible coverage.
- Aim for the highest achievable code coverage percentage.
- Test both happy paths and edge cases.
- Test error conditions and boundary values.
- Use mocking where external dependencies are involved.
- Name test methods descriptively to indicate what scenario they cover.
- Organize tests to mirror the source code structure.

---

## Framework and Dependency Management

- Always use and update to the latest version of frameworks and dependent libraries.
- Pin dependency versions explicitly in the dependency/package file.
- Regularly audit dependencies for known vulnerabilities.
- Remove unused dependencies to reduce attack surface and bloat.
- Document any version-specific constraints or compatibility notes.

---

## Logging

- Add logs at the following levels: `ERROR`, `WARN`, `INFO`, `DEBUG`.
- Log level should be configurable through a settings/properties file.
- Use `ERROR` for failures that require immediate attention.
- Use `WARN` for unexpected situations that are recoverable.
- Use `INFO` for high-level operational flow and milestones.
- Use `DEBUG` for detailed diagnostic information useful during development.
- Never log sensitive data such as passwords, tokens, or PII.
- Include contextual information in log messages (timestamps, correlation IDs, module names).

---

## Naming Conventions

- Use descriptive names for variables, functions, and data types to make the code easy to understand.
- Variable names should convey their purpose, not their type.
- Function names should describe the action being performed.
- Class names should be nouns representing the concept they encapsulate.
- Avoid abbreviations unless they are universally understood.
- Be consistent with naming conventions across the entire codebase.

---

## Security and Vulnerability Management

- Implement coding best practices to protect against vulnerability management risks.
- Validate and sanitize all external inputs.
- Never hardcode secrets, API keys, or credentials in source code.
- Use parameterized queries to prevent injection attacks.
- Apply the principle of least privilege for file and network access.
- Escape output to prevent cross-site scripting (XSS) where applicable.
- Keep dependencies updated to patch known CVEs.
- Store sensitive configuration in environment variables or encrypted vaults.

---

## Error Handling

- Add adequate error handling to capture known runtime and unforeseen errors.
- Use try/catch (or equivalent) blocks around operations that can fail.
- Catch specific exception types before generic ones.
- Provide meaningful error messages that aid debugging without leaking internals.
- Implement graceful degradation where possible.
- Never swallow exceptions silently — always log or re-raise.
- Use custom exception/error classes for domain-specific failures.
- Implement global/unhandled exception handlers as a safety net.

---

## Performance Optimization

- Code should always be optimized for the MOST EFFICIENT usage of memory, processor, and disk.
- Avoid unnecessary object creation or deep copies.
- Use appropriate data structures for the operation (e.g., sets for lookups, queues for FIFO).
- Release resources (file handles, connections, streams) promptly after use.
- Avoid blocking operations in the main execution thread.
- Profile and benchmark before and after optimization changes.
- Cache expensive computations where inputs are repeated.
- Minimize disk I/O by batching reads/writes where possible.

---

## Spacing and Linting

- Ensure adequate spacing and linting in code.
- Use a linter and formatter appropriate to the language (e.g., ESLint, Prettier, Black, Flake8).
- Configure linting rules in a shared config file committed to the repository.
- Maintain consistent indentation (spaces vs. tabs — pick one and enforce it).
- Use blank lines to separate logical sections within a file.
- Keep line length within a readable limit (80–120 characters).
- Run linting as part of the CI/CD pipeline to enforce standards automatically.

---

## Async and Decoupled Patterns

- Use async and decoupled patterns wherever possible.
- Prefer non-blocking I/O for network and file operations.
- Use message queues or event-driven patterns to decouple components.
- Avoid tight coupling between modules — depend on abstractions, not implementations.
- Use dependency injection to allow swapping implementations.
- Favor composition over inheritance for flexible behavior reuse.
- Design interfaces/contracts between modules to allow independent development and testing.

---

## README.md Standards

- The `README.md` should always be kept up to date.
- The README should have a table of contents at the top.
- **Section 1:** Explain the project, its project structure, and dependencies.
- **Section 2:** Explain how to deploy this project.
- **Section 3:** Give instructions on how to set up any external systems or configurations if applicable.
- Add an end-to-end flow diagram at the top of the README file (using Mermaid or ASCII art).

---

## .gitignore

- Add a `.gitignore` file for the project language with relevant files and patterns.
- Ignore build outputs, compiled artifacts, and temporary files.
- Ignore IDE/editor-specific files and folders.
- Ignore OS-generated files (e.g., `.DS_Store`, `Thumbs.db`).
- Ignore dependency directories (e.g., `node_modules/`, `venv/`, `.venv/`).
- Ignore environment/secrets files (e.g., `.env`, `*.pem`, `*.key`).
- Never commit log files or local database files.

---

## External Configuration

- Capture as many variables as possible in an external properties/configuration file which can change from environment to environment.
- Use separate config files or profiles for development, staging, and production.
- Never hardcode environment-specific values (URLs, ports, credentials, feature flags).
- Support overriding configuration via environment variables.
- Document all configuration keys, their expected values, and defaults.
- Load configuration at application startup and validate required values are present.
- Use a consistent format for the config file (e.g., `.env`, `.yaml`, `.json`, `.properties`).
