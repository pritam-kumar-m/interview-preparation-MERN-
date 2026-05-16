# TypeScript Interview Questions and Answers

Prepared for an experienced full-stack developer interview target, around a 6-year level. Resume context used: Node.js, Express.js, Next.js, React, PostgreSQL, MongoDB, Prisma, Redis, WebSocket, ELD and fleet management, Shopify and BigCommerce ecommerce, AI voice workflows, Twilio, Stripe, dashboards, authentication, API performance, and scalable backend services.

Focus areas: type system fundamentals, DTOs, generics, utility types, React/Node usage, runtime validation, API contracts, and production full-stack maintainability.

**Question count:** 100

**Categories:** Beginner (30), Intermediate (40), Advanced (30)

## Beginner

### 1. What is TypeScript?

**Answer:** TypeScript is a typed superset of JavaScript that compiles to JavaScript. It helps catch many mistakes during development before code runs in Node.js or the browser.

### 2. Why use TypeScript in full-stack development?

**Answer:** TypeScript improves confidence across frontend props, backend DTOs, API responses, services, and database models. For large projects, it reduces integration bugs and makes refactoring safer.

### 3. How is TypeScript different from JavaScript?

**Answer:** JavaScript is executed at runtime, while TypeScript adds compile-time type checking and then outputs JavaScript. TypeScript improves development safety but does not replace runtime validation.

### 4. What is type annotation?

**Answer:** A type annotation explicitly tells TypeScript the expected type, such as const age: number = 30. It documents intent and helps the compiler catch invalid assignments.

### 5. What is type inference?

**Answer:** Type inference means TypeScript can determine a type automatically from the assigned value or usage. Good inference reduces unnecessary annotations while keeping safety.

### 6. What are basic TypeScript types?

**Answer:** Common types include string, number, boolean, null, undefined, bigint, symbol, object, array types, tuple types, union types, and literal types.

### 7. What is the any type?

**Answer:** any disables type checking for a value. It can be useful during migration, but overusing any removes TypeScript benefits and can hide bugs.

### 8. What is the unknown type?

**Answer:** unknown represents a value whose type is not known yet. It is safer than any because you must narrow or validate it before using it.

### 9. What is void?

**Answer:** void usually means a function does not return a meaningful value. It is common for event handlers, logging functions, and functions that perform side effects.

### 10. What is never?

**Answer:** never represents values that never occur, such as functions that always throw or exhaustive checks that should be impossible. It is useful in advanced type safety.

### 11. What is a union type?

**Answer:** A union type allows a value to be one of several types, such as string | number. It is useful for status values, optional API fields, and flexible inputs.

### 12. What is an intersection type?

**Answer:** An intersection combines multiple types into one, such as User & Auditable. The resulting value must satisfy all combined type requirements.

### 13. What are literal types?

**Answer:** Literal types restrict values to exact literals, such as "active" | "inactive". They are useful for statuses, roles, modes, and event names.

### 14. What is a type alias?

**Answer:** A type alias gives a name to a type expression. It can describe primitives, unions, intersections, objects, tuples, and function signatures.

### 15. What is an interface?

**Answer:** An interface describes the shape of an object and is often used for contracts like User, Product, Driver, or ApiResponse. Interfaces can be extended and implemented by classes.

### 16. When should you use interface vs type?

**Answer:** Use either based on team convention. Interfaces are nice for object contracts and extension; type aliases are flexible for unions, intersections, and utility type composition.

### 17. What is an optional property?

**Answer:** An optional property uses ? to show that a field may be missing. Example: phone?: string. Optional fields are common in user profiles, filters, and partial updates.

### 18. What is a readonly property?

**Answer:** A readonly property cannot be reassigned after creation. It helps protect IDs, configuration, and immutable data structures.

### 19. How do arrays work in TypeScript?

**Answer:** Arrays can be typed as string[] or Array<string>. This ensures all elements match the expected type.

### 20. What is a tuple?

**Answer:** A tuple is an array with fixed positions and types, such as [number, string]. It is useful for small structured pairs, but object types are often clearer.

### 21. What is an enum?

**Answer:** An enum defines a named set of values. Many teams now prefer union literal types for simple statuses because they are lighter and often easier to type-check.

### 22. What is a function type?

**Answer:** A function type defines parameter and return types. It helps type callbacks, service methods, API handlers, and reusable utilities.

### 23. How do you type function parameters?

**Answer:** Add types beside parameters, such as function getUser(id: string). This prevents callers from passing invalid values.

### 24. How do you type function return values?

**Answer:** Add a return type after parameters, such as function count(): number. Explicit return types are useful for public functions and service contracts.

### 25. What is type narrowing?

**Answer:** Type narrowing refines a broad type to a more specific type using checks like typeof, instanceof, equality checks, or custom type guards.

### 26. What is a type guard?

**Answer:** A type guard is a check that tells TypeScript a value has a specific type. It is useful when handling unknown API data or union types.

### 27. What is tsconfig.json?

**Answer:** tsconfig.json configures the TypeScript compiler, including strictness, module behavior, target JavaScript version, path aliases, and included files.

### 28. What does strict mode do?

**Answer:** Strict mode enables stronger type checks, including stricter null handling and function type checks. It is recommended for long-term maintainable projects.

### 29. Does TypeScript run in the browser directly?

**Answer:** Browsers run JavaScript, not TypeScript. TypeScript must be compiled or transpiled to JavaScript before execution.

### 30. Why is TypeScript useful for React and Next.js?

**Answer:** It types props, hooks, route data, API responses, forms, and shared utilities. This prevents many UI and integration mistakes in larger applications.

## Intermediate

### 31. What are generics in TypeScript?

**Answer:** Generics let functions, types, and classes work with different types while preserving type information. They are useful for reusable API clients, repositories, and UI components.

### 32. How do generic constraints work?

**Answer:** Constraints limit generic types to values that satisfy a required shape, such as T extends { id: string }. This allows safe access to known properties.

### 33. What does keyof do?

**Answer:** keyof creates a union of property names from a type. It is useful for safe property access, reusable table columns, and generic utility functions.

### 34. What does typeof do in TypeScript types?

**Answer:** typeof can derive a type from an existing value. It helps keep config, constants, and derived types synchronized.

### 35. What is indexed access type?

**Answer:** Indexed access reads the type of a property, such as User["email"]. It avoids duplicating field types manually.

### 36. What are mapped types?

**Answer:** Mapped types create new object types by transforming properties of another type. Utility types like Partial and Readonly use this idea.

### 37. What are conditional types?

**Answer:** Conditional types choose one type or another based on a type relationship, such as T extends string ? A : B. They power many advanced utilities.

### 38. What is Partial<T>?

**Answer:** Partial<T> makes all properties of T optional. It is useful for update DTOs, patch operations, and form drafts.

### 39. What is Required<T>?

**Answer:** Required<T> makes all properties required. It can be useful after validation or when converting optional input into a complete domain object.

### 40. What is Pick<T, K>?

**Answer:** Pick creates a type with only selected keys from another type. It is useful for public DTOs or selecting a subset of model fields.

### 41. What is Omit<T, K>?

**Answer:** Omit creates a type by removing selected keys. It is useful for create DTOs where fields like id or createdAt should not be provided by users.

### 42. What is Record<K, V>?

**Answer:** Record creates an object type with keys K and values V. It is useful for lookup maps such as role-to-permissions or status-to-label mappings.

### 43. What is ReturnType<T>?

**Answer:** ReturnType extracts the return type of a function. It helps reuse derived function result types without manually duplicating them.

### 44. What is Awaited<T>?

**Answer:** Awaited unwraps the resolved type of a Promise-like value. It is useful when typing async function results.

### 45. What is NonNullable<T>?

**Answer:** NonNullable removes null and undefined from a type. It is useful after validation when a value is guaranteed to exist.

### 46. What are discriminated unions?

**Answer:** A discriminated union uses a common literal field, such as type or status, to safely narrow variants. It is excellent for events, API states, and workflow states.

### 47. How do you type API responses?

**Answer:** Define consistent response types with data, error, pagination, and status fields where needed. Keep backend responses and frontend expectations aligned.

### 48. How do you type Express request bodies?

**Answer:** Use generics or custom request types for params, response body, request body, and query. Still validate runtime data before trusting it.

### 49. How do you type React props?

**Answer:** Use interfaces or type aliases to define required and optional props. Clear prop types make components reusable and safer to refactor.

### 50. How do you type React events?

**Answer:** Use React event types such as React.ChangeEvent<HTMLInputElement> or React.FormEvent<HTMLFormElement>. This prevents incorrect event usage.

### 51. How do you type useState?

**Answer:** TypeScript often infers useState from the initial value. Add explicit generics when initial state is null, empty array, or a union state.

### 52. How do you type useRef?

**Answer:** Use generics like useRef<HTMLInputElement | null>(null) for DOM refs. For mutable refs, type the stored value explicitly.

### 53. How do you type custom hooks?

**Answer:** Define clear parameter and return types, especially when returning tuples or objects. For tuples, as const can preserve position-specific types.

### 54. What are declaration files?

**Answer:** Declaration files with .d.ts describe types for JavaScript code or packages. They let TypeScript understand libraries that do not ship types directly.

### 55. What are ambient declarations?

**Answer:** Ambient declarations tell TypeScript about values that exist at runtime elsewhere, such as globals or external modules. They should be used carefully.

### 56. What is module augmentation?

**Answer:** Module augmentation extends existing module types. It is useful when adding custom fields to library types, such as Express request user context.

### 57. How do you type environment variables?

**Answer:** Create a validated config layer and optionally augment NodeJS.ProcessEnv. Runtime validation is important because env values are strings or undefined.

### 58. What is structural typing?

**Answer:** TypeScript checks whether a value has the required shape, not whether it was explicitly declared as a certain type. This matches JavaScript object behavior.

### 59. What is excess property checking?

**Answer:** When assigning object literals, TypeScript checks for unexpected fields in certain contexts. This catches typos in DTOs, config, and props.

### 60. What is type assertion?

**Answer:** A type assertion tells TypeScript to treat a value as a type. It should be used sparingly because it can bypass safety if the assertion is wrong.

### 61. What is const assertion?

**Answer:** as const makes values deeply readonly and narrows literals. It is useful for status arrays, route constants, and configuration maps.

### 62. What does satisfies do?

**Answer:** satisfies checks that a value conforms to a type while preserving its specific inferred type. It is useful for config objects and constant maps.

### 63. How does TypeScript work with Prisma?

**Answer:** Prisma generates types from the schema, so queries and model fields are type-safe. You still need database constraints and runtime validation for external inputs.

### 64. How does TypeScript work with MongoDB or Mongoose?

**Answer:** You can type document interfaces, schemas, and query results. Be careful that database data can still differ from expected types without validation or migrations.

### 65. What is a DTO?

**Answer:** A DTO, or Data Transfer Object, defines the shape of data crossing boundaries such as API requests and responses. TypeScript makes DTOs explicit and reusable.

### 66. How do you type pagination?

**Answer:** Create types for query input and response metadata, such as page, limit, total, totalPages, and data. Consistent pagination types help frontend dashboards.

### 67. What is noImplicitAny?

**Answer:** noImplicitAny reports cases where TypeScript cannot infer a type and would use any. It improves code safety by forcing explicit typing.

### 68. What is strictNullChecks?

**Answer:** strictNullChecks makes null and undefined distinct from other types. It prevents many runtime crashes caused by assuming values always exist.

### 69. How do you type error handling?

**Answer:** Catch values are unknown in strict setups, so narrow them before reading properties. Application errors can use custom classes or typed error codes.

### 70. How do you avoid over-engineering types?

**Answer:** Prefer clear domain types, DTOs, and practical generics. Avoid deeply nested conditional types unless they solve a real team problem.

## Advanced

### 71. How would you design shared types between backend and frontend?

**Answer:** Use shared DTO packages or generated types from OpenAPI/tRPC/GraphQL where appropriate. Keep runtime validation aligned with compile-time types to avoid false confidence.

### 72. How would you migrate a large JavaScript codebase to TypeScript?

**Answer:** Start with tsconfig and allowJs, type critical boundaries first, add strictness gradually, convert files feature by feature, and use tests to protect behavior.

### 73. How do you handle unknown third-party API responses?

**Answer:** Treat external responses as unknown, validate with schemas, then convert into typed internal DTOs. Never trust TypeScript types alone for network data.

### 74. How do you type a reusable API client?

**Answer:** Use generics for response data, typed request options, normalized error types, and endpoint-specific DTOs. Keep authentication and retry behavior outside random components.

### 75. How do you type reusable table components?

**Answer:** Use generics over row type, column definitions constrained by keyof row, and explicit render functions. This supports dashboards with drivers, vehicles, orders, and logs.

### 76. How would you type role-based permissions?

**Answer:** Use literal unions for roles/actions, Record mappings for permissions, and helper functions with typed inputs. Runtime checks still enforce real authorization.

### 77. How do conditional types help library code?

**Answer:** They allow types to adapt based on inputs, such as extracting promise results or function returns. Use them in libraries, but keep application types readable.

### 78. What is infer in conditional types?

**Answer:** infer declares a type variable inside a conditional type to extract part of another type. ReturnType and Promise unwrapping patterns use this idea.

### 79. What are variance concerns in TypeScript?

**Answer:** Variance describes how subtyping works for generics and function parameters. It matters in callbacks, event handlers, and library types where unsafe assignment can appear.

### 80. How does TypeScript handle private and protected class members?

**Answer:** TypeScript supports access modifiers at compile time. JavaScript private fields also exist at runtime using # syntax, which has different behavior from TypeScript private.

### 81. How do decorators relate to TypeScript?

**Answer:** Decorators attach metadata or behavior to classes and members, often used in NestJS. They require understanding framework runtime behavior, not just types.

### 82. How would you type NestJS DTOs and services?

**Answer:** Use DTO classes or schemas for validation, typed service methods, typed repository returns, and clear module contracts. Avoid leaking database entities directly as public responses.

### 83. How would you type Express request user context?

**Answer:** Use module augmentation to add user to Express Request or pass context explicitly. Ensure authentication middleware actually sets the value before handlers rely on it.

### 84. How would you model domain states in TypeScript?

**Answer:** Use discriminated unions for states like pending, active, failed, completed, or cancelled. Exhaustive switch checks prevent missing cases as workflows grow.

### 85. How do you enforce exhaustive checks?

**Answer:** Use a never assignment in the default branch of a switch over a discriminated union. If a new variant is added, TypeScript will report missing handling.

### 86. How do you keep TypeScript builds fast?

**Answer:** Use project references for monorepos, avoid huge type computation, skip unnecessary generated checks, and keep dependencies updated. Type complexity can hurt developer speed.

### 87. What are project references?

**Answer:** Project references split TypeScript projects into smaller build units. They help large monorepos build incrementally and keep package boundaries clearer.

### 88. How does TypeScript affect CI quality?

**Answer:** CI can run type checks to catch broken contracts before deployment. It should run alongside tests, linting, and build checks, not replace them.

### 89. How would you type database transactions?

**Answer:** Pass a transaction-scoped client type through service methods or define repository interfaces that accept a transaction context. This prevents accidentally mixing transaction and non-transaction queries.

### 90. How do you prevent type drift between database schema and app code?

**Answer:** Use generated ORM types, migrations, compile checks, and integration tests. TypeScript helps, but the database remains the source for actual stored data.

### 91. How do you type webhook handlers?

**Answer:** Define provider event types, validate signatures and payload shape, narrow event variants, and handle unknown event types safely. Idempotency should be represented in persistence, not only types.

### 92. How would you type a payment workflow?

**Answer:** Use discriminated unions for payment states, DTOs for provider responses, branded IDs where helpful, and runtime validation for all provider data.

### 93. What are branded types?

**Answer:** Branded types distinguish values with the same primitive type, such as UserId and OrderId both being strings. They reduce accidental ID mixups.

### 94. What are template literal types?

**Answer:** Template literal types create string patterns from type unions, such as event names or route keys. They are useful for strongly typed constants and event systems.

### 95. How do you use TypeScript with Redis keys?

**Answer:** Create typed key builder functions instead of hand-written strings. This reduces mistakes in tenant IDs, entity IDs, and cache namespaces.

### 96. How do you use TypeScript with PostgreSQL JSONB?

**Answer:** Define TypeScript types for expected JSONB shapes and validate before writes and after reads. JSONB flexibility should not become unchecked runtime risk.

### 97. How would you review TypeScript code as a senior developer?

**Answer:** Check meaningful types, boundaries, runtime validation, any usage, null safety, DTO clarity, generic readability, and whether types reflect real business rules.

### 98. How do you explain TypeScript experience in an interview?

**Answer:** Connect it to safer APIs, DTOs, React props, Next.js routes, NestJS services, Prisma models, and reduced bugs in complex full-stack projects.

### 99. What is the biggest TypeScript misconception?

**Answer:** The biggest misconception is that TypeScript guarantees runtime correctness. It only checks compile-time assumptions, so external data still needs validation and tests.

### 100. What is the senior-level TypeScript mindset?

**Answer:** Use TypeScript to make important contracts explicit and refactoring safer, while avoiding unnecessary type complexity. Types should help the team ship reliable code.


## Reference Docs

- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [TypeScript Handbook - Everyday Types](https://www.typescriptlang.org/docs/handbook/2/everyday-types.html)
- [TypeScript Handbook - Generics](https://www.typescriptlang.org/docs/handbook/2/generics.html)
- [TypeScript Utility Types](https://www.typescriptlang.org/docs/handbook/utility-types.html)
