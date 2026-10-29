# Framework Familiarization Lab

Reusable project specification · Backend + Frontend · Target: 1 focused day per framework

## Project: TaskFlow

A small task management application with authentication, CRUD operations, filtering, and a clean client-server architecture.

* REST API
* JWT authentication
* SOLID / OOP
* HTTP client
* State management
* Performance

## Part 1 — Backend Framework Lab

Objective: Learn how to build a maintainable, class-based backend using a new framework, following separation of concerns and SOLID principles.

### 1. Project requirements

Implement these features:

- Register and log in users.
- Authenticate requests using short-lived access tokens.
- Refresh access tokens using refresh tokens.
- Log out and invalidate refresh tokens.
- Create, list, update, and delete tasks.
- Allow users to access only their own tasks.
- Filter and paginate task lists.
- Validate incoming requests and return consistent errors.
- Test the application through an API client.

### 2. Folder architecture

Use this as a reference architecture, adapting it to the idioms of each framework.

```


app/
├── main.py
├── core/
│   ├── config.py
│   ├── security.py
│   └── exceptions.py
├── api/
│   └── routes/
│       ├── auth.py
│       └── tasks.py
├── controllers/
│   ├── auth_controller.py
│   └── task_controller.py
├── services/
│   ├── auth_service.py
│   └── task_service.py
├── repositories/
│   ├── user_repository.py
│   ├── task_repository.py
│   └── refresh_token_repository.py
├── models/
│   ├── user.py
│   └── task.py
├── schemas/
│   ├── auth.py
│   └── task.py
├── dependencies/
│   └── auth.py
├── middleware/
├── utils/
├── constants/
└── tests/
    ├── test_auth.py
    └── test_tasks.py


```

Use the structure to understand responsibilities, not as a mandate to create a file for every concept. For example, FastAPI may use dependencies and Pydantic models, while NestJS uses modules, providers, and guards.

### 3. Architecture and SOLID checklist

- Single Responsibility Principle: Controllers handle HTTP concerns; services implement business rules; repositories handle persistence.
- Open/Closed Principle: Extend behavior through well-defined interfaces rather than repeatedly modifying unrelated code.
- Liskov Substitution Principle: Implementations of an interface should remain interchangeable without breaking expected behavior.
- Interface Segregation Principle: Define focused interfaces instead of large interfaces that every implementation must satisfy.
- Dependency Inversion Principle: Business services depend on abstractions rather than concrete database or infrastructure classes.
- Use constructor injection where supported.
- Separate application configuration from business logic.
- Use DTOs to control request and response shapes.
- Keep framework-specific request and response objects out of most business services.
- Understand how the framework handles asynchronous errors and dependency lifecycles.

For example, the dependency direction should be:

Controller

* HTTP input and output
* Service
* Business rules
* Repository interface
* Data access abstraction
* Database implementation

### 4. Authentication and security

This is an essential part of the exercise. Implement the following flows:

- `POST /auth/register` — validate input, hash the password, create the user.
- `POST /auth/login` — verify credentials and issue tokens.
- `POST /auth/refresh` — verify and rotate the refresh token.
- `POST /auth/logout` — revoke the refresh token and clear its cookie.
- `GET /auth/me` — return the authenticated user's public profile.
- Authentication middleware or guard for protected routes.
- Authorization checks for task ownership.
- Expiry handling and invalid-token responses.
- Refresh-token reuse detection and revocation policy.

Security details to understand

- JWTs are typically signed, not encrypted. Their payload is readable unless you deliberately use a suitable encryption scheme.
- Use a short-lived access token and a longer-lived refresh token.
- Store refresh tokens in `HttpOnly`, `Secure`, appropriately configured `SameSite` cookies for browser clients. Protect cookie-based flows against CSRF where necessary.
- Store refresh-token hashes or equivalent revocation records server-side; rotate tokens on refresh.
- Clearing a cookie alone does not invalidate a previously issued token. Server-side revocation is required for refresh-token invalidation.
- Never store passwords or raw refresh tokens in logs.
- Keep secrets in environment configuration, not source code.

For a one-day exercise, implement a working refresh/revocation flow with a simple persistent token store. A complete production-grade session security system is a separate task.

### 5. Request validation and response conventions

- Validate body, parameters, query strings, and headers as appropriate.
- Reject invalid IDs, missing fields, malformed data, and unsupported values.
- Centralize error handling.
- Use appropriate HTTP status codes.
- Return consistent error codes and validation details.
- Avoid exposing stack traces, secrets, or internal database errors to clients.
- Use explicit response DTOs to avoid leaking password hashes or internal fields.

Example success response:

```
{
  "success": true,
  "data": {
    "id": "task_123",
    "title": "Learn Fastify",
    "completed": false
  }
}
```

Example error response:

```
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Request validation failed",
    "details": [
      {
        "field": "title",
        "message": "Title is required"
      }
    ]
  }
}
```

Use a consistent envelope for your learning exercise; the exact response contract can vary by API design.

### 6. Backend testing checklist

- Test every route's success path.
- Test malformed requests and missing fields.
- Test missing, expired, and invalid access tokens.
- Test refresh-token rotation and reuse of old tokens.
- Test logout and subsequent refresh attempts.
- Test that one user cannot access another user's tasks.
- Test nonexistent resources and database errors.
- Test that responses never expose sensitive fields.
- Add a health endpoint, such as `GET /health`.

### 7. One-day backend schedule

| Time      | Deliverable                                                 |
| --------- | ----------------------------------------------------------- |
| 0–1 hour  | Setup, configuration, routing, and folder structure         |
| 1–2 hours | CRUD endpoints, validation, and response formatting         |
| 2–3 hours | Controllers, services, repositories, and OOP boundaries     |
| 3–5 hours | Login, JWT verification, refresh, logout, and authorization |
| 5–6 hours | Centralized errors and automated tests                      |
| 6–7 hours | Review framework-specific features and document learnings   |

Scope note: If you're new to authentication, prioritize a working secure flow over finishing every item. Use an existing password-hashing library and the framework's standard validation/security facilities.

## Part 2 — Frontend Framework Lab

Objective: Learn how a framework renders UI on its target platform, manages state, handles network requests, navigates between screens, and integrates with platform APIs.

Use the same TaskFlow application. The UI should work with the backend above, but you can use a mock API if the backend is not ready.

### 1. Required screens

[How to Generate App Icon for Android Using Android Studio | by Sarika Ks | Medium](https://images.openai.com/static-rsc-4/0cA-LmzUeC43yd7DZ4zOvLMinmxMUjlk1832NAlCnUWNJM2qzCbzYcNtTla9UkCsOfqclc5orD6eNzUPDK6HcnGKjq1FeabpXqX8J8pB0f0A28NaC6wy4FVoPSn_sQ53ypiKxtyI9bGm7HdZdvyhPud_TxxcBchu00678CfyzHU?purpose=inline)

Login and registration

Form state, validation, authentication, loading, and error states.

[Task Management Platform by Maia Burjanadze on Dribbble](https://images.openai.com/static-rsc-4/TE2GiDiDvp_RIhifTVBRjGxxPdtv-zgIYmTJdyQGNANXmdzQdIzI4hSRrkHjJk-Nj8FLdMiQR_GmiJi8vGfc_3q5DoulcSxShoFii3zrNN9u0kCvOukhuKm7qt-llytVq9-uuPRpw1xyRWhTGRGt3d0IMyFyDn7ZXAYEL9S1-VM?purpose=inline)

Task list

Fetch data, render lists, search, filter, refresh, and paginate.

[TaskMorph - A Task Management App :: Behance](https://images.openai.com/static-rsc-4/aqlbdZXt5ufsfblewllleE7-IrneNSVzRQZll98ia4In9UPLfd2shzq7VxOYxNiVT3S7JkGMf_XqA-Hx8HitsBndmjgdwI3eMglQZu2d7lj-hyoISntGeIDOCFhs4JabkvD-iwuejvub4Kx_N5PurmtbRQFPOdPZEnKyhqhsLi4?purpose=inline)

Create and edit task

Forms, validation, mutations, navigation, and optimistic updates if appropriate.

### 2. Frontend architecture

Adapt the implementation to the framework instead of forcing a React-specific structure onto every platform.

```

src/
├── app/ or navigation/
│   ├── routes
│   └── navigation-config
├── screens/ or pages/
│   ├── Login
│   ├── TaskList
│   └── TaskEditor
├── components/
│   ├── Button
│   ├── Input
│   ├── TaskItem
│   └── LoadingState
├── features/
│   ├── auth/
│   └── tasks/
├── services/
│   ├── http-client
│   ├── auth-api
│   └── task-api
├── state/
│   ├── auth-state
│   └── task-state
├── hooks/ or composables/
├── utils/
├── constants/
├── platform/
│   ├── storage
│   └── device-capabilities
└── tests/

```

### 3. Rendering and component fundamentals

- Understand component creation, composition, and reuse.
- Understand props, local state, and data flow.
- Understand the framework's rendering lifecycle.
- Understand reactivity, reconciliation, or change detection.
- Render collections with stable keys or identity tracking.
- Handle conditional rendering and empty states.
- Implement forms and validation.
- Avoid unnecessary state and duplicated sources of truth.
- Separate presentation components from data-fetching logic where appropriate.
- Understand the difference between framework rendering and native platform rendering.

### 4. HTTP client and API integration

- Build a reusable HTTP client or use the framework's recommended client.
- Configure a base URL and environment-specific settings.
- Handle GET, POST, PATCH, and DELETE requests.
- Serialize request bodies and parse responses.
- Handle loading, success, empty, and error states.
- Map server validation errors to form fields.
- Handle timeouts, network failures, and cancellation.
- Add request/response interceptors or middleware where appropriate.
- Attach access tokens to protected requests.
- Handle expired access tokens and refresh requests.
- Prevent concurrent failed requests from triggering multiple refresh operations.
- Retry failed requests safely and avoid infinite refresh loops.
- Understand CORS and cookie credentials for browser clients.

Important: Authentication storage differs by platform. Browsers can use `HttpOnly` cookies, which JavaScript cannot read. Mobile and desktop apps may instead need platform-secure storage and an appropriately designed token transport. Do not assume the browser cookie model transfers directly to every client.

### 5. State management

- Distinguish local UI state, shared application state, and server state.
- Manage form values and validation errors.
- Manage authenticated user and session status.
- Manage task lists, filters, and selected task state.
- Understand derived/computed state.
- Understand context, stores, reducers, or the framework's native state system.
- Handle loading and error transitions consistently.
- Avoid duplicating server data across unrelated stores.
- Understand caching, invalidation, and refetching.
- Handle logout and session expiration globally.

Use the framework's native state primitives first. Add a dedicated state library only when the exercise demonstrates a real need.

### 6. Routing and navigation

- Define routes or screens.
- Pass route parameters and query parameters.
- Navigate between task list and editor.
- Handle deep links or URL-based navigation where supported.
- Protect authenticated routes.
- Redirect unauthenticated users to login.
- Handle back navigation and unknown routes.
- Understand nested navigation and navigation lifecycle.
- Preserve or restore state when navigating, where appropriate.

### 7. Rendering performance and optimization

- Measure initial load and screen transition performance.
- Identify unnecessary component renders or reactive updates.
- Avoid expensive computations during rendering.
- Use memoization only where measurement justifies it.
- Optimize long lists using pagination or virtualization.
- Split code or lazily load routes where supported.
- Optimize images, assets, and bundle size.
- Avoid unnecessary network requests and duplicate fetching.
- Cancel obsolete requests when screens or components are disposed.
- Use profiling tools to locate actual bottlenecks.

Platform-specific performance

- Web: bundle size, hydration, browser main-thread work, layout shifts, and Core Web Vitals.
- Mobile: startup time, memory use, scrolling performance, native bridge or interop costs, and battery usage.
- Desktop: startup time, memory use, window responsiveness, IPC costs, and packaging overhead.

Do not try to optimize all these dimensions blindly. Identify the target platform, measure a baseline, and investigate one bottleneck.

### 8. Platform APIs and lifecycle

Build a small platform abstraction and exercise at least one real platform-specific capability.

| Platform     | Example exercise                                                        |
| ------------ | ----------------------------------------------------------------------- |
| Web          | `localStorage`, clipboard, browser history, or online/offline events    |
| React Native | Secure storage, app lifecycle, keyboard, or share sheet                 |
| Desktop      | Filesystem access, clipboard, window lifecycle, or native notifications |

Also understand:

- Permissions and capability restrictions.
- Lifecycle events and cleanup.
- Persistent storage vs in-memory state.
- Secure storage appropriate to the platform.
- Network changes and offline/error behavior.
- Platform-specific build and debugging tools.

### 9. Frontend testing

- Test reusable components.
- Test form validation and submission.
- Test API loading, success, and error states.
- Test authentication redirects.
- Test refresh-token failure and logout behavior.
- Test list rendering, filtering, and empty states.
- Profile the application on the actual target platform.
- Test one platform-specific capability.

### 10. One-day frontend schedule

| Time      | Deliverable                                       |
| --------- | ------------------------------------------------- |
| 0–1 hour  | Setup, entry point, components, and routing       |
| 1–2 hours | Screens, forms, state, and rendering              |
| 2–3 hours | HTTP client and task API integration              |
| 3–4 hours | Authentication flow and protected navigation      |
| 4–5 hours | Error/loading states and platform API             |
| 5–6 hours | Profiling, optimization, and tests                |
| 6–7 hours | Review framework internals and document learnings |

## Part 3 — Framework comparison log

Every time you complete the lab in a new framework, record the differences instead of simply marking the project complete.

# Framework Familiarization Notes

**Framework:**\
**Language:**\
**Target platform:**\
**Date:**

## 1. Setup and execution

- How is the project initialized?
- How does development and production execution work?
- What are the build and debugging tools?

## 2. Architecture

- How are routes registered?
- How are modules, services, and dependencies organized?
- How is dependency injection or composition handled?
- What is the idiomatic folder structure?

## 3. Request lifecycle / rendering lifecycle

- How does an HTTP request travel through the backend?
- How does a UI update propagate through the frontend?
- Where do middleware, hooks, effects, or lifecycle methods execute?

## 4. State and data

- How is application state managed?
- How are API requests made and cached?
- How are errors and cancellations handled?

## 5. Security and platform behavior

- How are authentication and secure storage handled?
- What platform APIs are available?
- What limitations or permissions apply?

## 6. Performance

- What profiling tools are available?
- What are the common performance pitfalls?
- What did I measure and improve?

## 7. Trade-offs

- What does this framework make easy?
- What requires additional libraries?
- What differs from frameworks I already know?

## 8. Further investigation

- Concepts I understand:
- Concepts I need to revisit:
- Documentation worth bookmarking:

## Definition of done

## Progress tracker

### 0/8

### Backend

* CRUD API with validation and consistent responses

* Controllers, services, repositories, and clear dependency boundaries

* Authentication, refresh rotation, logout, and authorization

* Centralized errors and automated tests

### Frontend

* Screens, reusable components, and navigation

* HTTP client with loading and error handling

* State management and authentication flow

* One platform API and a measured performance check

The standard is not to master a framework in seven hours. It is to learn its conventions, implement one representative vertical slice, identify unfamiliar concepts, and know where to look in the documentation. Repeating this lab will make switching frameworks much faster without confusing familiarity with mastery.
