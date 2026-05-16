# Node.js Interview Questions and Answers

Prepared for an experienced full-stack developer interview target, around a 6-year level. Resume context used: Node.js, Express.js, Next.js, React, PostgreSQL, MongoDB, Prisma, Redis, WebSocket, ELD and fleet management, Shopify and BigCommerce ecommerce, AI voice workflows, Twilio, Stripe, dashboards, authentication, API performance, and scalable backend services.

Focus areas: event loop, async I/O, APIs, backend architecture, streams, security, observability, scaling, and production service design.

**Question count:** 100

**Categories:** Beginner (30), Intermediate (40), Advanced (30)

## Beginner

### 1. What is Node.js?

**Answer:** Node.js is a JavaScript runtime built for running JavaScript outside the browser. It is commonly used to build REST APIs, backend services, scripts, realtime systems, and full-stack application backends.

### 2. Why is Node.js popular for backend development?

**Answer:** Node.js uses non-blocking I/O and a large npm ecosystem, making it productive for APIs and integrations. Your resume projects with ecommerce, ELD, Twilio, Stripe, and dashboards fit this use case well.

### 3. What is the V8 engine?

**Answer:** V8 is the JavaScript engine that compiles and executes JavaScript. Node.js uses V8 along with native APIs to provide server-side capabilities.

### 4. What does event-driven mean in Node.js?

**Answer:** Event-driven means code reacts to events such as requests, file completion, socket messages, or timers. This model is useful for APIs, WebSocket updates, and asynchronous workflows.

### 5. What does non-blocking I/O mean?

**Answer:** Non-blocking I/O means Node.js can start an operation and continue handling other work while waiting for the result. This helps APIs serve many concurrent users efficiently.

### 6. Is Node.js single-threaded?

**Answer:** JavaScript execution in Node.js runs mostly on a single main thread, but Node also uses libuv and worker resources for I/O and some background tasks. CPU-heavy work can still block the event loop.

### 7. What is npm?

**Answer:** npm is the package manager commonly used with Node.js. It installs dependencies, runs scripts, and manages package versions for backend and full-stack projects.

### 8. What is package.json?

**Answer:** package.json stores project metadata, dependencies, scripts, and configuration. It is central to starting, building, testing, and deploying Node.js applications.

### 9. What is package-lock.json?

**Answer:** package-lock.json records exact dependency versions. It improves reproducible installs across developer machines, CI, and production deployments.

### 10. What is the difference between dependencies and devDependencies?

**Answer:** dependencies are needed at runtime, while devDependencies are mainly for development tools such as testing, linting, and build utilities. Keeping this clear helps production builds stay lean.

### 11. What is CommonJS?

**Answer:** CommonJS is the module system using require and module.exports. Many Node.js projects and packages still use it, especially older Express applications.

### 12. What are ES modules in Node.js?

**Answer:** ES modules use import and export syntax. Modern Node.js supports them, but projects must configure module type and handle interop with CommonJS carefully.

### 13. What is the process object?

**Answer:** process provides information and control over the running Node.js process, such as environment variables, arguments, exit events, and memory usage.

### 14. How do environment variables work in Node.js?

**Answer:** Environment variables are read through process.env and used for configuration like database URLs, API keys, ports, and secrets. They should not be hardcoded in source code.

### 15. What is the fs module?

**Answer:** The fs module provides filesystem APIs for reading, writing, and managing files. Prefer async APIs for server code so file operations do not block request handling.

### 16. What is the path module?

**Answer:** The path module safely handles file paths across operating systems. It is useful for uploads, static files, generated reports, and config paths.

### 17. What is the http module?

**Answer:** The http module can create web servers directly. Frameworks like Express build on top of lower-level HTTP concepts to simplify routing and middleware.

### 18. What is a Buffer in Node.js?

**Answer:** A Buffer stores raw binary data. It is used for files, network packets, streams, uploads, and binary API payloads.

### 19. What is a stream in Node.js?

**Answer:** A stream processes data piece by piece instead of loading everything into memory. Streams are useful for large files, exports, uploads, logs, and HTTP responses.

### 20. What is EventEmitter?

**Answer:** EventEmitter is a Node.js pattern where objects emit named events and listeners respond. It appears in streams, servers, sockets, and custom event-driven code.

### 21. What is an error-first callback?

**Answer:** An error-first callback receives error as the first argument and data after it. It is common in older Node.js APIs and helps standardize async error handling.

### 22. How do Promises help in Node.js?

**Answer:** Promises represent asynchronous results and avoid deeply nested callbacks. They work well with async/await for database calls, API requests, and service logic.

### 23. What is async/await in Node.js?

**Answer:** async/await lets you write promise-based code in a clear sequential style. It is common in route handlers, service functions, jobs, and integration code.

### 24. What is nodemon used for?

**Answer:** nodemon restarts a Node.js process when files change during development. It improves local developer speed but is not a production process manager.

### 25. What is dotenv used for?

**Answer:** dotenv loads environment variables from a local .env file during development. It helps keep credentials and config outside source code.

### 26. How does Node.js handle JSON?

**Answer:** Node.js can parse JSON request bodies through frameworks and can serialize JavaScript objects to JSON responses. API contracts should keep JSON shapes consistent and documented.

### 27. What is a REST API in Node.js?

**Answer:** A REST API exposes resources through HTTP methods such as GET, POST, PUT, PATCH, and DELETE. Node.js is commonly used to build these APIs with Express, NestJS, or similar frameworks.

### 28. What is a middleware-style backend?

**Answer:** Middleware-style backends process requests through a sequence of functions. This approach is used for logging, auth, validation, parsing, and error handling.

### 29. How do you start a Node.js application?

**Answer:** Usually a package script such as npm start or npm run dev starts the app. Production startup should use configured environment variables and a reliable process manager or platform.

### 30. What makes Node.js suitable for API integrations?

**Answer:** Node.js handles asynchronous network calls well and has many SDKs. This makes it practical for Shopify, BigCommerce, Twilio, Stripe, AI APIs, and internal microservices.

## Intermediate

### 31. What are the main parts of the Node.js event loop?

**Answer:** The event loop coordinates timers, pending callbacks, poll, check, close callbacks, and microtasks. Understanding it helps explain async execution order and performance problems.

### 32. What is libuv?

**Answer:** libuv is the library that provides Node.js with the event loop, async I/O, thread pool, and cross-platform system operations. It is a key reason Node.js can do non-blocking I/O.

### 33. What is the difference between process.nextTick and Promise microtasks?

**Answer:** Both run before many macrotasks, but process.nextTick has very high priority in Node.js. Overusing it can starve the event loop, so it should be used carefully.

### 34. How do streams handle backpressure?

**Answer:** Backpressure occurs when data is produced faster than it can be consumed. Streams signal when writers should pause and resume, preventing memory growth.

### 35. How would you handle large file uploads in Node.js?

**Answer:** Stream uploads, validate size and type, avoid buffering entire files in memory, and store files in object storage when possible. Large uploads need progress and failure handling.

### 36. What is child_process used for?

**Answer:** child_process runs external commands or separate processes. It is useful for isolated jobs, but inputs must be sanitized and process lifecycle handled safely.

### 37. What is the cluster module?

**Answer:** The cluster module allows multiple Node.js worker processes to share server load across CPU cores. Modern deployments often use process managers or containers for similar scaling.

### 38. What are worker_threads?

**Answer:** worker_threads run JavaScript in separate threads for CPU-heavy tasks. They are useful when computation would otherwise block the event loop.

### 39. How do you avoid blocking the event loop?

**Answer:** Avoid long synchronous loops, heavy JSON operations, sync filesystem calls in request paths, and CPU-heavy work. Move expensive work to workers, queues, or separate services.

### 40. What causes memory leaks in Node.js?

**Answer:** Leaks can come from global caches, retained closures, unremoved listeners, unresolved timers, large queues, or accidental references. Long-running services need memory monitoring.

### 41. How do you handle unhandled promise rejections?

**Answer:** Use try/catch around awaits, centralize async route error handling, and monitor unhandledRejection events. The best fix is to handle errors where they happen.

### 42. How do you design centralized error handling?

**Answer:** Normalize errors into application error types, log technical details, return safe messages, and preserve stack traces. Centralized error handling keeps API behavior consistent.

### 43. What should production logging include?

**Answer:** Logs should include timestamp, level, request ID, user or tenant context when safe, endpoint, and error details. Avoid logging secrets, tokens, or sensitive personal data.

### 44. How do you manage configuration in Node.js?

**Answer:** Use environment variables, validate required config at startup, separate environments, and document values. Missing config should fail early instead of causing runtime surprises.

### 45. How do you validate API input in Node.js?

**Answer:** Use schema validation, sanitize input, check authorization, and return field-level errors. Validation protects database integrity and third-party API calls.

### 46. How is JWT authentication commonly handled?

**Answer:** Verify token signature, expiration, issuer/audience when applicable, and map claims to user identity. Authorization should still check roles and resource ownership.

### 47. How do you implement rate limiting?

**Answer:** Track request counts by IP, user, tenant, or token using memory for simple cases or Redis for distributed systems. Rate limiting protects login, AI calls, webhooks, and public APIs.

### 48. What is CORS in a Node.js API?

**Answer:** CORS controls browser access to APIs from different origins. Configure allowed origins, methods, headers, and credentials carefully for frontend-backend deployments.

### 49. Why is database connection pooling important?

**Answer:** Pools reuse database connections instead of opening a new connection for every request. Good pool sizing improves performance and prevents exhausting PostgreSQL or MongoDB resources.

### 50. How does Prisma fit into Node.js projects?

**Answer:** Prisma provides a typed ORM and migration workflow. It can improve developer productivity, but you still need to understand SQL performance, transactions, and generated queries.

### 51. How do background jobs work in Node.js?

**Answer:** Background jobs run work outside the request-response path, often through queues. They are useful for emails, reports, AI processing, SEO scans, and webhook processing.

### 52. How does Redis help Node.js applications?

**Answer:** Redis can provide caching, distributed locks, rate limiting, queues, sessions, and pub/sub. It is useful when multiple Node.js instances need shared fast state.

### 53. How do you implement WebSockets in Node.js?

**Answer:** Use a WebSocket library, authenticate connections, handle reconnects, and broadcast only necessary updates. Fleet logs, chat, and live status dashboards are common cases.

### 54. What are cron jobs in Node.js?

**Answer:** Cron jobs run scheduled tasks such as cleanup, reports, reminders, or sync jobs. In distributed deployments, ensure only one instance runs a singleton job unless duplicates are safe.

### 55. What is graceful shutdown?

**Answer:** Graceful shutdown stops accepting new requests, finishes in-flight work, closes database connections, and exits cleanly. It helps prevent data loss during deploys or restarts.

### 56. What should a health check endpoint verify?

**Answer:** A basic health check confirms the service is alive, while readiness can check database, Redis, or dependency availability. Use lightweight checks to avoid adding load.

### 57. How do you test Node.js services?

**Answer:** Use unit tests for pure logic, integration tests for routes and databases, and end-to-end tests for critical flows. Mock external APIs where needed but keep contracts realistic.

### 58. How do you mock external services?

**Answer:** Mock SDK clients or HTTP boundaries and test success, failure, timeout, and retry behavior. This is important for Stripe, Twilio, Shopify, BigCommerce, and AI APIs.

### 59. Why use TypeScript with Node.js?

**Answer:** TypeScript catches type mismatches, documents contracts, and improves refactoring. It is useful for DTOs, service interfaces, database models, and API responses.

### 60. What issues happen when mixing ESM and CommonJS?

**Answer:** Default exports, named exports, file extensions, and package type settings can behave differently. Be consistent where possible and understand how each dependency exports modules.

### 61. How do you secure dependencies?

**Answer:** Run audits, update vulnerable packages, remove unused dependencies, pin versions appropriately, and review high-risk packages. Supply-chain risk is real in Node.js ecosystems.

### 62. What are common Node.js security concerns?

**Answer:** Input validation, injection, XSS through returned content, SSRF, insecure auth, exposed secrets, dependency vulnerabilities, and weak rate limiting are common concerns.

### 63. How do you profile Node.js performance?

**Answer:** Use CPU profiles, heap snapshots, event-loop delay metrics, APM tools, and endpoint timing. Determine whether the bottleneck is CPU, database, network, or external APIs.

### 64. How does Docker help Node.js deployment?

**Answer:** Docker packages the app with runtime dependencies and consistent startup behavior. Keep images small, avoid copying secrets, and use production install settings.

### 65. What is an API pagination contract?

**Answer:** A pagination contract defines page, limit, total, data, and sometimes summary fields. Consistent pagination makes frontend dashboard wiring easier and less error-prone.

### 66. What is idempotency in Node.js APIs?

**Answer:** Idempotency means repeated requests produce the same intended result. It is important for retries, payments, webhooks, and order creation.

### 67. How do you handle third-party API failures?

**Answer:** Use timeouts, retries for safe operations, circuit breakers for repeated failures, clear error mapping, and fallback states. Never let external APIs hang request threads indefinitely.

### 68. What is request context?

**Answer:** Request context stores metadata such as request ID, user, tenant, and trace information across async operations. It improves logging and debugging in production.

### 69. How do you structure a Node.js project?

**Answer:** Separate routes/controllers, services, repositories, validation, config, middleware, and tests. Clear layers keep business logic away from transport-specific code.

### 70. How do you handle API versioning?

**Answer:** Use URL versions, headers, or compatibility layers depending on client needs. Versioning helps mobile apps, third-party integrations, and frontend deployments evolve safely.

## Advanced

### 71. How would you design a scalable Node.js backend?

**Answer:** Separate domain services, keep route handlers thin, use database indexes, caching, queues, validation, observability, and horizontal scaling. Architecture should support both traffic and team maintenance.

### 72. How would you debug event loop lag?

**Answer:** Measure event-loop delay, inspect CPU profiles, check synchronous code, large JSON processing, and blocking libraries. Move heavy work to workers or queues after confirming the bottleneck.

### 73. When would you use worker threads versus a job queue?

**Answer:** Use worker threads for CPU-heavy work inside the service boundary, and queues for async workflows, retries, and distributed processing. Many production systems use both for different problems.

### 74. How would you scale Node.js across CPU cores?

**Answer:** Run multiple processes using cluster, a process manager, containers, or orchestration. Keep shared state outside process memory, typically in a database or Redis.

### 75. How would you design horizontal scaling for WebSockets?

**Answer:** Use a shared pub/sub layer, sticky sessions when needed, connection authentication, and presence tracking. One instance memory cannot be the source of truth in a scaled system.

### 76. What observability would you add to a Node.js service?

**Answer:** Add structured logs, metrics, traces, request IDs, dependency timing, error reporting, and health checks. Observability lets you debug API, database, and external provider issues quickly.

### 77. How would you implement circuit breakers?

**Answer:** Track repeated downstream failures, stop sending requests temporarily, return controlled errors or fallbacks, and recover gradually. Circuit breakers protect services from cascading failures.

### 78. How do you design retry and backoff safely?

**Answer:** Retry only safe operations, use exponential backoff with jitter, set max attempts, and include idempotency keys for mutations. Payment and webhook logic require extra caution.

### 79. How would you process a huge CSV export in Node.js?

**Answer:** Use streams, backpressure, chunked database reads, and incremental writes. Avoid loading the full dataset into memory and include progress/error handling.

### 80. How would you investigate high memory usage?

**Answer:** Compare heap snapshots, inspect retained objects, review caches and queues, monitor GC behavior, and reproduce with realistic traffic. Fix the reference keeping memory alive.

### 81. What garbage collection behavior matters in Node.js?

**Answer:** V8 automatically collects unreachable objects, but excessive allocation and retained references can cause pauses or memory growth. Reducing allocation pressure can improve latency.

### 82. How would you design secure authentication services?

**Answer:** Use strong password hashing, secure sessions or JWT validation, refresh-token rotation when applicable, MFA where needed, audit logging, and strict authorization checks.

### 83. How would you support multi-tenant SaaS in Node.js?

**Answer:** Require tenant context at every data boundary, enforce tenant filters server-side, isolate secrets, and design caching keys with tenant IDs. Tenant isolation is a security requirement.

### 84. How would you process Stripe or Shopify webhooks?

**Answer:** Verify signatures, preserve raw payload when required, store event IDs, handle retries idempotently, and move heavy work to a queue. Return quickly after validation.

### 85. How would you implement distributed rate limiting?

**Answer:** Use Redis or another shared store with atomic counters or token buckets. Local memory rate limits fail when the API runs on multiple instances.

### 86. How would you tune database pool size?

**Answer:** Consider app instance count, database max connections, query duration, traffic, and serverless behavior. Too many connections can hurt the database more than help the app.

### 87. How do you maintain consistency across Node.js and PostgreSQL?

**Answer:** Use transactions for related writes, enforce constraints in the database, and make retries idempotent. Application logic alone should not be the only consistency layer.

### 88. How would you design Node.js microservices?

**Answer:** Define service ownership, API contracts, auth between services, observability, failure handling, and data boundaries. Avoid splitting services before domain boundaries are clear.

### 89. What message queue patterns are useful in Node.js?

**Answer:** Use queues for retryable jobs, delayed tasks, fan-out, and workload smoothing. Include dead-letter handling and idempotent consumers.

### 90. How would you build a real-time ELD log pipeline?

**Answer:** Receive events, validate and persist them, publish updates through WebSocket or pub/sub, detect violations asynchronously, and store auditable timestamps. Reliability is more important than flashy UI.

### 91. How would you design API contracts for frontend teams?

**Answer:** Define stable response shapes, error formats, pagination, filtering, sorting, and versioning. Clear contracts reduce frontend-backend integration churn.

### 92. How do you perform zero-downtime deploys for Node.js?

**Answer:** Use health checks, graceful shutdown, rolling deploys, backward-compatible migrations, and connection draining. Avoid deploys that kill in-flight requests or background jobs abruptly.

### 93. How would you manage secrets in production?

**Answer:** Use a secret manager or platform-provided environment store, rotate credentials, avoid logging secrets, and limit access by service. Never commit secrets into source control.

### 94. How would you run load tests for a Node.js API?

**Answer:** Define realistic traffic, test critical endpoints, monitor latency percentiles, CPU, memory, event-loop delay, and database metrics. Load tests should reveal bottlenecks, not just peak numbers.

### 95. How do serverless constraints affect Node.js?

**Answer:** Cold starts, connection reuse, execution time limits, and filesystem constraints affect design. Serverless can scale well but needs careful database and background job planning.

### 96. How would you design a Node.js backend for AI voice workflows?

**Answer:** Handle Twilio/webhook events, manage conversation state, call AI APIs with timeouts, store transcripts, enqueue summaries, and expose dashboards. Latency and reliability are both important.

### 97. How would you protect a Node.js API from abuse?

**Answer:** Use authentication, authorization, rate limiting, input validation, body-size limits, logging, dependency security, and monitoring. Public endpoints and AI APIs need special protection.

### 98. How would you review Node.js code as a senior developer?

**Answer:** Check error paths, async handling, validation, transaction boundaries, logs, security, performance, and tests. Good review catches production risks before they become incidents.

### 99. How would you explain Node.js experience from this resume?

**Answer:** Talk about building scalable REST APIs, auth systems, ecommerce integrations, ELD services, Redis/WebSocket realtime flows, PostgreSQL-backed services, and reliable backend workflows.

### 100. What is the most senior-level Node.js interview mindset?

**Answer:** Show that you think beyond syntax: reliability, data correctness, security, observability, scaling, and maintainability. Use real project examples instead of only textbook definitions.


## Reference Docs

- [Node.js API Docs](https://nodejs.org/api/)
