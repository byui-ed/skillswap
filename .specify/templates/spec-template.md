# SkillSwap

## Project Description

SkillSwap is a peer-to-peer web application for exchanging knowledge. Users create profiles, list skills they can teach, and request skills they want to learn. They can discover listings and contact their owners to propose an exchange.

## Purpose and Target Audience

**Purpose:** Make it easy for people to find learning partners and arrange clear, mutually agreed skill exchanges.

**Target audience:** People who want to teach or learn skills without relying on paid courses, including hobbyists, students, professionals, and community members.

## User Stories and Acceptance Criteria

### US1 — Sign Up

As a prospective user, I want to create an account so I can publish listings and contact other users.

**Acceptance criteria**
- A visitor can register with the required account details and valid credentials.
- Invalid or already-used account details produce a clear error without creating an account.
- A successful registration creates an authenticated session and takes the user to their profile or dashboard.
- Passwords are never stored or returned in plaintext.

### US2 — Create a Skill Listing

As a signed-in user, I want to publish a skill I can teach or want to learn so others can find a potential exchange.

**Acceptance criteria**
- A user can create a listing with a title, description, listing type (offering or requesting), and optional category and availability.
- Required fields are validated, and validation errors identify the fields to correct.
- A successful creation makes the listing visible in browse results and its detail view.
- Each listing is associated with its creator.

### US3 — Read and Discover Listings

As a visitor or user, I want to browse listings and view their details so I can find relevant skills and potential exchange partners.

**Acceptance criteria**
- Users can browse published listings and open a detail view.
- A listing shows its title, description, type, optional category and availability, and owner’s public profile information.
- Users can filter listings by offering/requesting and search by skill title or description.
- Unavailable or deleted listings are not presented as active listings.
- Private account information is not exposed in listing results or details.

### US4 — Update a Skill Listing

As a listing owner, I want to edit my listing so its information stays accurate.

**Acceptance criteria**
- The owner can edit the listing’s fields and save valid changes.
- Updated information appears in browse results and the detail view.
- Invalid changes are rejected with actionable validation errors.
- A user who does not own the listing cannot update it.

### US5 — Delete a Skill Listing

As a listing owner, I want to remove my listing when it is no longer available.

**Acceptance criteria**
- The owner can delete their listing after confirming the action.
- A deleted listing no longer appears in browse results or can be accessed as an active listing.
- A user who does not own the listing cannot delete it.
- Repeating a deletion request returns a clear not-found response or equivalent outcome.

## API Endpoints

All endpoints use JSON. Authentication is required for account-specific operations. The server validates request data and enforces listing ownership.

| Method | Endpoint | Purpose |
|---|---|---|
| `POST` | `/api/auth/register` | Register an account |
| `POST` | `/api/auth/login` | Authenticate an account |
| `POST` | `/api/auth/logout` | End the current session |
| `GET` | `/api/listings` | Browse listings; supports search, type, and category filters |
| `POST` | `/api/listings` | Create a listing |
| `GET` | `/api/listings/{id}` | Retrieve a listing’s details |
| `PATCH` | `/api/listings/{id}` | Update an owned listing |
| `DELETE` | `/api/listings/{id}` | Delete an owned listing |

Use appropriate HTTP status codes, including `400` for invalid input, `401` for unauthenticated requests, `403` for ownership violations, and `404` for missing listings.

## Implementation Priority

1. **P1 — Foundation:** Account registration and authentication; listing data model and validation.
2. **P1 — Listing lifecycle:** Create, browse, view, update, and delete listings with ownership checks.
3. **P2 — Discovery:** Search and filter listings; responsive, accessible user interface.
4. **P2 — Exchange readiness:** Clear contact or exchange-proposal entry point that does not expose private contact details by default.

## Technical Constraints

- Use Next.js App Router, TypeScript with strict mode, and Tailwind CSS.
- Do not use TypeScript `any`; validate untrusted input at runtime.
- Prefer Server Components; use Client Components only where interaction or browser APIs require them.
- Use Route Handlers for API endpoints and keep secrets and server-only logic out of client code.
- Prefer Tailwind utilities; add custom CSS only when necessary.
- Test core workflows, validation, authentication, and ownership restrictions.