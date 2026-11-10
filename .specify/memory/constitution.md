# Constitution

## Purpose

Build a trustworthy, accessible peer-to-peer platform where people can offer skills to teach, request skills to learn, and arrange fair skill exchanges.

## Governing Principles

### 1. Trust, Safety, and Respect

- Treat user safety and respectful participation as product requirements.
- Collect only the personal information needed to provide the service; protect it and never expose private contact details by default.
- Provide clear ways to report abuse, block users, and manage listings.
- Do not imply that users, skills, or exchanges have been verified unless they have been.

### 2. Fair and Transparent Exchange

- Make offers, requests, availability, and exchange expectations clear before users commit.
- Support barter and other explicitly agreed exchange terms without ranking people by perceived worth.
- Let users control their listings and withdraw from proposed exchanges.
- Avoid dark patterns, misleading claims, and undisclosed fees.

### 3. Accessibility and Inclusion

- Design for keyboard navigation, screen readers, responsive layouts, and readable contrast.
- Use inclusive, plain language and avoid assumptions about users’ identity, location, or ability.
- Provide useful empty, loading, validation, and error states.

### 4. Reliable, User-Centered Delivery

- Prioritize understandable flows for creating skill listings, finding matches, and managing exchanges.
- Validate user input at appropriate boundaries and return actionable error messages.
- Prefer maintainable, incremental changes over unnecessary complexity.

## Technical Standards

### 5. TypeScript

- Use TypeScript strict mode.
- Do not use `any`. Prefer precise types, `unknown` with narrowing, and explicit return types where they improve clarity.
- Validate untrusted input at runtime; TypeScript types alone do not validate external data.
- Keep shared domain types in clear, reusable modules.

### 6. Next.js

- Use the Next.js App Router and file-based routing.
- Prefer Server Components. Add `'use client'` only when browser APIs, local state, or event handlers require a Client Component.
- Keep server-only logic and secrets out of client modules.
- Use Route Handlers for HTTP endpoints, with explicit method behavior, input validation, and appropriate status codes.
- Keep data access and business rules separate from presentation where practical.

### 7. Tailwind CSS

- Use utility-first Tailwind classes for styling.
- Reuse consistent design tokens and component patterns.
- Avoid custom CSS unless utilities cannot reasonably meet the requirement; document the reason when custom CSS is added.
- Keep class lists readable and preserve responsive and accessibility-related states.

### 8. Naming and Organization

- Use `PascalCase` for React components and type names.
- Use `camelCase` for variables, functions, and object properties.
- Use `kebab-case` for route segments and lowercase filenames where practical.
- Name modules and tests after the feature or behavior they represent.
- Prefer descriptive names over abbreviations.

## Quality and Collaboration

### 9. Testing

- Add or update tests for behavior changed by each feature or fix.
- Test important user flows, validation, permissions, and failure states.
- Use unit tests for isolated logic and integration or end-to-end tests for critical flows.
- Ensure tests are deterministic and do not depend on real user data or external services.
- Run relevant tests, linting, and type checks before submitting changes.

### 10. Team Collaboration

- Keep changes focused and explain user-visible or architectural tradeoffs in pull requests.
- Review changes for accessibility, privacy, security, and consistency with this constitution.
- Update documentation and tests when behavior or setup changes.
- Resolve disagreements in favor of user safety, accessibility, maintainability, and these principles.

## Governance

This constitution governs product and engineering decisions. Any exception must be documented with its rationale, scope, and follow-up plan. Amendments should be reviewed by the team and reflected in relevant documentation and tests.