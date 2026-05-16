# Express.js Interview Questions and Answers

Prepared for an experienced full-stack developer interview target, around a 6-year level. Resume context used: Node.js, Express.js, Next.js, React, PostgreSQL, MongoDB, Prisma, Redis, WebSocket, ELD and fleet management, Shopify and BigCommerce ecommerce, AI voice workflows, Twilio, Stripe, dashboards, authentication, API performance, and scalable backend services.

Focus areas: routing, middleware, REST APIs, validation, authentication, error handling, webhooks, security, scaling, and production API design.

**Question count:** 100

**Categories:** Beginner (30), Intermediate (40), Advanced (30)

## Beginner

### 1. What is Express.js?

**Answer:** Express.js is a minimal Node.js web framework for building HTTP APIs and web applications. It provides routing, middleware, request handling, and response utilities.

### 2. Why use Express.js with Node.js?

**Answer:** Node.js gives the runtime, while Express adds a simple structure for routes, middleware, and APIs. It is productive for REST services, ecommerce integrations, auth, and dashboard backends.

### 3. What is an Express app?

**Answer:** An Express app is the main application instance created by calling express(). It registers middleware, routes, settings, and error handlers.

### 4. What is a route in Express?

**Answer:** A route maps an HTTP method and URL path to a handler function. For example, GET /drivers can return driver records, while POST /orders can create an order.

### 5. What are req and res in Express?

**Answer:** req represents the incoming request and contains params, query, body, headers, and user context. res is used to send status codes, JSON, files, or redirects back to the client.

### 6. What is middleware in Express?

**Answer:** Middleware is a function that runs during the request-response cycle. It can parse bodies, log requests, validate input, authenticate users, or handle errors.

### 7. What does next() do?

**Answer:** next() passes control to the next middleware or route handler. If called with an error, Express forwards the request to error-handling middleware.

### 8. What HTTP methods are commonly used in Express APIs?

**Answer:** GET reads data, POST creates data, PUT replaces data, PATCH updates part of data, and DELETE removes data. Good REST APIs use methods consistently.

### 9. What are route parameters?

**Answer:** Route parameters capture values from the URL path, such as /drivers/:id. They are useful for detail pages, updates, deletes, and resource-specific actions.

### 10. What are query parameters?

**Answer:** Query parameters appear after ? in the URL and are often used for filters, search, sort, and pagination. Example: page=1&limit=20.

### 11. How do you read request body data?

**Answer:** Use express.json() for JSON payloads and express.urlencoded() for form data. Request body parsing should be configured before routes that need body values.

### 12. What does res.json() do?

**Answer:** res.json() sends a JSON response with the proper content type. It is the common response method for REST APIs consumed by React or Next.js frontends.

### 13. How do you set HTTP status codes?

**Answer:** Use res.status(code) before sending the response. Clear status codes help clients handle success, validation errors, auth failures, and server errors properly.

### 14. What is express.Router?

**Answer:** express.Router creates modular route groups. It helps split APIs into files such as auth routes, user routes, product routes, driver routes, and report routes.

### 15. Why does middleware order matter?

**Answer:** Express runs middleware in the order registered. Body parsing, auth, and validation must run before handlers that depend on them, while error handlers usually come near the end.

### 16. How do you serve static files in Express?

**Answer:** Use express.static to serve assets from a folder. This can support uploaded files or public assets, though production apps often use a CDN or object storage.

### 17. How do you handle 404 routes?

**Answer:** Add a fallback middleware after all routes that returns a 404 response. This helps clients receive a clear message for unknown endpoints.

### 18. What is Express error-handling middleware?

**Answer:** Error middleware has four parameters: err, req, res, and next. It centralizes error responses and avoids repeating try/catch response logic everywhere.

### 19. How do you handle async route errors?

**Answer:** Wrap async handlers with try/catch or use an async error wrapper depending on the Express version and setup. The important part is that rejected promises reach centralized error handling.

### 20. What is CORS middleware used for?

**Answer:** CORS middleware controls which browser origins can call the API. It is important when a Next.js or React frontend runs on a different domain than the backend.

### 21. What is helmet used for?

**Answer:** helmet sets security-related HTTP headers. It helps harden Express apps against common web risks, though it does not replace validation and secure auth.

### 22. What is morgan used for?

**Answer:** morgan logs HTTP requests during development or simple deployments. Production systems often use structured logging instead.

### 23. What is a controller in Express?

**Answer:** A controller is a function that handles request and response logic for a route. Larger apps keep business logic in services so controllers stay small.

### 24. What is a service layer?

**Answer:** A service layer contains business logic independent of Express request/response objects. It improves testability and keeps APIs maintainable.

### 25. What is REST in Express APIs?

**Answer:** REST organizes APIs around resources and standard HTTP behavior. For example, users, products, vehicles, logs, and orders can each have clear endpoints.

### 26. How do you validate input in Express?

**Answer:** Use validation middleware or schemas before business logic runs. Validation should check required fields, types, formats, ranges, and ownership-sensitive values.

### 27. What is authentication middleware?

**Answer:** Authentication middleware identifies the caller, often by verifying a session or JWT. It can attach the user object to req for later authorization checks.

### 28. What is authorization in Express?

**Answer:** Authorization checks whether an authenticated user can perform an action. Examples include admin-only routes, carrier-specific data, or merchant-owned resources.

### 29. How can you test an Express endpoint?

**Answer:** Use tools like Postman, curl, or automated tests with Supertest. Automated tests should cover success, validation errors, unauthorized access, and failure paths.

### 30. What makes an Express API response format good?

**Answer:** A good response format is consistent, predictable, and includes data, status, errors, and pagination where needed. Consistency makes frontend integration much easier.

## Intermediate

### 31. How do you organize Express routes in a large project?

**Answer:** Group routes by feature, use express.Router, keep controllers thin, move business logic into services, and keep validation/auth middleware reusable.

### 32. How do nested routers work?

**Answer:** Nested routers mount one router under a path, such as /api/v1/products. This creates clean route prefixes and versioned API organization.

### 33. How do you validate route parameters?

**Answer:** Validate IDs, slugs, and enum-like params before querying the database. Invalid params should return clear 400 or 404 responses instead of causing database errors.

### 34. How do you implement pagination in Express?

**Answer:** Read page and limit from query params, validate boundaries, query with offset/cursor logic, and return data with pagination metadata such as total and current page.

### 35. How do you implement filtering and sorting?

**Answer:** Whitelist allowed filters and sort fields, validate values, and translate them into safe database queries. Never pass raw query values directly into SQL strings.

### 36. What is centralized response handling?

**Answer:** Centralized response helpers keep success, error, and pagination shapes consistent. This is useful across APIs for dashboards, mobile apps, and admin panels.

### 37. How should Express handle validation errors?

**Answer:** Return 400 with field-specific messages and a stable error shape. Good validation errors help frontend forms show precise feedback.

### 38. How should Express handle not-found database records?

**Answer:** Return 404 for missing resources and avoid revealing data that belongs to another tenant or user. Ownership checks are part of secure not-found behavior.

### 39. How do you implement JWT auth in Express?

**Answer:** Read the token, verify signature and expiration, load or trust minimal user claims, attach user context, and fail with 401 when invalid.

### 40. How do you implement role-based access control?

**Answer:** Create middleware that checks required roles or permissions after authentication. Use backend checks even if the frontend hides unauthorized buttons.

### 41. How do you implement request logging?

**Answer:** Log method, path, status, duration, request ID, and safe user context. Avoid logging passwords, tokens, or full sensitive payloads.

### 42. What is a request ID?

**Answer:** A request ID uniquely identifies a request across logs and services. It helps debug API issues reported from frontend dashboards or production monitoring.

### 43. How do you handle file uploads in Express?

**Answer:** Use streaming or middleware like multer for simple cases, validate file type and size, and prefer object storage for production-scale uploads.

### 44. How do you handle raw request bodies for webhooks?

**Answer:** Some providers require signature verification against the raw body. Configure raw parsing for those webhook routes before JSON parsing changes the payload.

### 45. How do you process Stripe or Shopify webhooks in Express?

**Answer:** Verify signatures, store event IDs, make handlers idempotent, enqueue heavy work, and return quickly. Duplicate events should not create duplicate business actions.

### 46. How do sessions work in Express?

**Answer:** Sessions store user identity between requests, often using cookies and a server-side store. In production, use secure cookies and a shared store rather than local memory.

### 47. What is cookie-parser used for?

**Answer:** cookie-parser reads cookies from incoming requests. It can support session handling, preferences, CSRF tokens, and auth flows.

### 48. How do you configure CORS with credentials?

**Answer:** Set a specific allowed origin, enable credentials, and align cookies with secure and same-site settings. Wildcard origins are not suitable for credentialed requests.

### 49. How do you add rate limiting to Express?

**Answer:** Use middleware that tracks requests by IP, user, or token. For multiple instances, store counters in Redis or another shared system.

### 50. How do you add compression?

**Answer:** Use compression middleware for text responses like JSON or HTML. Measure impact and avoid compressing already compressed assets unnecessarily.

### 51. How do you secure Express headers?

**Answer:** Use helmet, configure CORS carefully, disable unnecessary headers, and add CSP where appropriate. Headers reduce risk but do not replace secure coding.

### 52. What is trust proxy in Express?

**Answer:** trust proxy tells Express when to trust headers set by a reverse proxy. It affects client IP, secure cookies, and rate limiting behind load balancers.

### 53. How do you structure Express with a database layer?

**Answer:** Controllers call services, services call repositories or ORM clients, and database-specific logic stays out of route handlers. This keeps testing and maintenance easier.

### 54. How do transactions fit into Express handlers?

**Answer:** For related writes, start a transaction in the service layer, perform all changes, and commit or rollback together. This protects data consistency for orders, payments, and compliance records.

### 55. How do you handle external API calls in Express?

**Answer:** Use timeouts, safe retries, error mapping, and provider-specific adapters. Express handlers should not hang indefinitely while waiting for third-party APIs.

### 56. How do you document Express APIs?

**Answer:** Use OpenAPI/Swagger or similar documentation with request schemas, responses, auth rules, and examples. Good docs reduce frontend and integration mistakes.

### 57. How do you version Express APIs?

**Answer:** Use route prefixes like /api/v1 or another versioning strategy. Versioning allows clients to migrate without breaking existing integrations.

### 58. How do you implement health checks?

**Answer:** Expose lightweight liveness and readiness endpoints. Readiness can check database or Redis availability so deploy platforms know when the app can receive traffic.

### 59. What is graceful shutdown in Express?

**Answer:** Stop accepting new connections, finish in-flight requests, close the HTTP server, and disconnect databases. This prevents abrupt failures during deployments.

### 60. How do app.locals and res.locals differ?

**Answer:** app.locals stores application-wide values, while res.locals stores data for one response cycle. res.locals can pass request context between middleware safely.

### 61. Can Express render templates?

**Answer:** Yes, Express can render views with template engines. However, many modern stacks use Express as a JSON API behind React or Next.js frontends.

### 62. How do you handle API timeouts?

**Answer:** Set request timeouts, external-call timeouts, and clear client responses. Timeouts prevent stuck requests from consuming resources forever.

### 63. How do you prevent duplicate submissions?

**Answer:** Use idempotency keys, database constraints, and request-state checks. This is important for payments, orders, appointment booking, and retrying failed requests.

### 64. How can Express work with WebSockets?

**Answer:** Create an HTTP server from the Express app and attach a WebSocket server. Express handles HTTP routes while the socket layer handles realtime communication.

### 65. How do you handle API errors from Prisma or databases?

**Answer:** Map known database errors to safe API responses, such as unique constraint conflicts or not-found records. Do not expose raw database stack traces to users.

### 66. How do you sanitize input in Express?

**Answer:** Normalize strings, reject unexpected fields, validate types, and escape output where necessary. Sanitization reduces injection and stored-content risks.

### 67. How do you keep route handlers testable?

**Answer:** Move business logic into services, inject dependencies where possible, and test controllers separately from database-heavy integration tests.

### 68. How do you handle async context in Express?

**Answer:** Use request-scoped context carefully through middleware or AsyncLocalStorage. It can carry request IDs and user context into deeper service logs.

### 69. What is a clean Express folder structure?

**Answer:** A clean structure usually has routes, controllers, services, repositories, middleware, validators, config, utils, and tests. Feature-based grouping can work better as the app grows.

### 70. How do you deploy Express in production?

**Answer:** Run behind a reverse proxy or platform load balancer, set environment variables, use process management, enable logging, configure health checks, and handle shutdown signals.

## Advanced

### 71. How would you architect a production Express API?

**Answer:** Use modular routes, thin controllers, service layers, validation schemas, centralized errors, auth middleware, observability, and clear database boundaries. This keeps the API scalable and maintainable.

### 72. How would you design a standard error model?

**Answer:** Define stable error codes, HTTP status mapping, safe messages, optional field errors, and correlation IDs. This helps frontend apps display errors consistently.

### 73. How would you create a validation architecture?

**Answer:** Put schema validation at request boundaries, keep business-rule validation in services, and share DTO types when possible. This avoids mixing transport checks with domain logic.

### 74. How would you design authentication and authorization for Express?

**Answer:** Separate identity verification from permission checks, support role/resource ownership rules, log sensitive decisions, and enforce authorization in every data-access path.

### 75. How would you build multi-tenant APIs in Express?

**Answer:** Resolve tenant context early, attach it to request context, enforce it in queries, include it in cache keys, and test cross-tenant access attempts.

### 76. How would you make webhook endpoints reliable?

**Answer:** Verify signatures, save event IDs, make consumers idempotent, enqueue slow work, and expose monitoring for failed events. Webhook retries are normal, so duplicates must be safe.

### 77. How would you implement distributed rate limiting?

**Answer:** Use Redis-backed counters or token buckets keyed by route, user, tenant, or IP. Local memory rate limits are insufficient when multiple Express instances run.

### 78. How would you design cursor pagination?

**Answer:** Use stable sort fields, encode cursor values, and avoid offset for very large changing datasets. Cursor pagination is useful for logs, events, and high-volume records.

### 79. How would you version a public Express API?

**Answer:** Use a clear versioning scheme, keep backward compatibility, document deprecations, and track client usage. Public clients need predictable migration windows.

### 80. How would you enforce OpenAPI contracts?

**Answer:** Generate docs from schemas or validate requests/responses against specs in tests. Contract discipline prevents frontend and backend drift.

### 81. How would you add observability to Express?

**Answer:** Add request IDs, structured logs, metrics for latency/status codes, traces around database/external calls, and alerting for error rates. Observability turns incidents into diagnosable events.

### 82. How would you harden Express security?

**Answer:** Use secure headers, strict CORS, body limits, input validation, auth checks, rate limiting, dependency audits, safe cookies, and secret management. Security is layered.

### 83. How would you configure CORS for multiple frontends?

**Answer:** Use an allowlist, validate the Origin header, support credentials only for trusted origins, and test preflight behavior. Avoid permissive wildcard policies for authenticated APIs.

### 84. How would you process file uploads at scale?

**Answer:** Stream uploads directly to storage where possible, scan or transform asynchronously, validate ownership, and store metadata in the database. Avoid keeping large files on app servers.

### 85. How would you optimize Express performance?

**Answer:** Measure latency, reduce slow middleware, optimize database queries, add caching, compress responses appropriately, and avoid blocking the event loop. Do not guess before measuring.

### 86. How can Express stream large responses?

**Answer:** Use Node streams and proper headers to send chunks gradually. This is useful for exports, logs, reports, and large downloads without high memory usage.

### 87. How would you design caching in Express?

**Answer:** Cache safe read responses, use Redis for shared caches, define TTLs, and invalidate after writes. Be careful with user-specific or compliance-sensitive data.

### 88. How would you handle blue-green or rolling deploys?

**Answer:** Ensure backward-compatible APIs, graceful shutdown, health checks, and migration safety. Rolling deploys can run old and new code at the same time.

### 89. How would you migrate an Express app to NestJS or another framework?

**Answer:** Move by modules, keep external API contracts stable, write tests first, and migrate business services before route wrappers. Avoid rewriting everything at once.

### 90. How does Express fit into microservices?

**Answer:** Express can expose service APIs, but service boundaries, contracts, authentication, observability, and data ownership matter more than the framework itself.

### 91. How would you build a BFF with Express?

**Answer:** Use Express to adapt backend services for a frontend, aggregate data, hide provider credentials, normalize errors, and shape responses for React or Next.js clients.

### 92. How would you test critical Express APIs?

**Answer:** Use integration tests with Supertest, database test setup, auth scenarios, validation cases, and provider mocks. Critical flows should include unhappy paths.

### 93. How would you handle flaky external providers?

**Answer:** Set timeouts, classify errors, retry safe operations, use circuit breakers, and queue work when response time is not user-critical. Provider issues should not collapse the API.

### 94. How would you design graceful shutdown with active requests?

**Answer:** Track the HTTP server, stop accepting new connections, allow a drain period, close databases and queues, and force exit only after a timeout.

### 95. How would dependency injection help an Express app?

**Answer:** Inject services, repositories, and clients so tests can replace them and modules stay decoupled. It is useful even without a full DI framework.

### 96. How would you manage ownership of many route modules?

**Answer:** Create feature modules with their own routes, controllers, validators, services, and tests. Clear ownership reduces conflicts in larger teams.

### 97. How would you expose realtime data from an Express backend?

**Answer:** Use Express for REST endpoints and attach WebSocket/SSE for live updates. Persist important events first, then broadcast so reconnects can recover missed data.

### 98. How would you design an Express API for ELD fleet management?

**Answer:** Model drivers, vehicles, HOS logs, violations, reports, and auth roles; validate timestamps; paginate logs; and protect carrier-specific data. Compliance data needs strong correctness.

### 99. How would you explain Express experience from this resume?

**Answer:** Connect Express to scalable REST APIs, authentication, ecommerce integrations, Stripe/Twilio workflows, PostgreSQL services, and reliable dashboard backends.

### 100. What is the senior-level Express interview mindset?

**Answer:** Show that Express is simple, so production quality comes from architecture, validation, security, error handling, observability, tests, and database-aware design.
## Reference Docs

- [Express Guide](https://expressjs.com/en/guide/routing.html)
- [Express Middleware Guide](https://expressjs.com/en/guide/using-middleware.html)
- [Express Error Handling](https://expressjs.com/en/guide/error-handling.html)
