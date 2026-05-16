# React.js Interview Questions and Answers

Prepared for an experienced full-stack developer interview target, around a 6-year level. Resume context used: Node.js, Express.js, Next.js, React, PostgreSQL, MongoDB, Prisma, Redis, WebSocket, ELD and fleet management, Shopify and BigCommerce ecommerce, AI voice workflows, Twilio, Stripe, dashboards, authentication, API performance, and scalable backend services.

Focus areas: components, hooks, state management, dashboards, forms, performance, accessibility, and production React patterns.

**Question count:** 100

**Categories:** Beginner (30), Intermediate (40), Advanced (30)

## Beginner

### 1. What is React.js?

**Answer:** React.js is a JavaScript library for building user interfaces from reusable components. In your resume context, it fits fleet dashboards, ecommerce interfaces, admin panels, and analytics screens.

### 2. What is a React component?

**Answer:** A component is a reusable UI unit that returns JSX. Components help split dashboards, forms, tables, filters, modals, and navigation into maintainable pieces.

### 3. What is JSX?

**Answer:** JSX is syntax that lets you write HTML-like markup inside JavaScript. It is compiled to React function calls and makes component UI easier to read.

### 4. What are props in React?

**Answer:** Props are inputs passed from a parent component to a child component. They should be treated as read-only and are useful for reusable cards, table rows, buttons, and form fields.

### 5. What is state in React?

**Answer:** State is component-managed data that changes over time and triggers re-rendering. Examples include form values, selected filters, modal visibility, and loaded dashboard data.

### 6. What is the difference between props and state?

**Answer:** Props come from the parent and state is owned by the component. A strong interview answer says props configure a component, while state represents local interaction or fetched data.

### 7. What are functional components?

**Answer:** Functional components are JavaScript functions that return JSX. Modern React uses functional components with hooks for state, side effects, refs, and memoization.

### 8. What were class components used for?

**Answer:** Class components were the older way to manage state and lifecycle methods. You may still see them in legacy code, but new React apps generally use functional components and hooks.

### 9. What are hooks?

**Answer:** Hooks are functions that let functional components use React features such as state, effects, context, refs, and reducers. Common hooks include useState, useEffect, useMemo, and useRef.

### 10. How does useState work?

**Answer:** useState stores local component state and returns the current value plus an updater function. Use it for UI state such as search text, selected tab, or modal open state.

### 11. How does useEffect work?

**Answer:** useEffect runs side effects after rendering, such as fetching data, subscribing to events, or updating the document title. Dependencies control when the effect re-runs.

### 12. How do you handle events in React?

**Answer:** React uses camelCase event props like onClick and onChange. Handlers are functions that update state, submit forms, call APIs, or trigger UI behavior.

### 13. What is conditional rendering?

**Answer:** Conditional rendering displays different UI based on state or props. It is commonly used for loading states, permissions, empty tables, and validation messages.

### 14. How do you render lists in React?

**Answer:** Use array methods such as map to return components for each item. Always provide a stable key so React can reconcile list updates correctly.

### 15. Why are keys important in React lists?

**Answer:** Keys help React identify which list items changed, moved, or were removed. Stable IDs are better than array indexes for dynamic lists like drivers, orders, products, or logs.

### 16. What is a controlled component?

**Answer:** A controlled component has its value managed by React state. Controlled inputs make validation, formatting, and submit behavior predictable.

### 17. What is an uncontrolled component?

**Answer:** An uncontrolled component stores its value in the DOM and is accessed with refs. It can be useful for simple forms or file inputs, but controlled components are easier to validate.

### 18. What is lifting state up?

**Answer:** Lifting state up means moving shared state to the nearest common parent. It helps synchronize filters, forms, selected rows, and child components.

### 19. What is component composition?

**Answer:** Composition builds complex UI by combining smaller components. It is usually preferred over inheritance in React because it keeps behavior explicit and reusable.

### 20. What are React fragments?

**Answer:** Fragments let you return multiple elements without adding extra DOM nodes. They are useful when a component needs to return sibling elements cleanly.

### 21. What is the virtual DOM?

**Answer:** The virtual DOM is React representation of UI in memory. React compares changes and updates the real DOM efficiently, though developers should still avoid unnecessary rendering.

### 22. What is one-way data flow?

**Answer:** React data usually flows from parent to child through props. Child components communicate changes upward through callback props, which keeps UI behavior predictable.

### 23. What is React StrictMode?

**Answer:** StrictMode is a development helper that highlights potential problems and intentionally double-invokes some behavior to reveal unsafe side effects. It does not affect production output.

### 24. What are React DevTools used for?

**Answer:** React DevTools help inspect component trees, props, state, hooks, and render behavior. They are useful for debugging dashboard and form issues.

### 25. How do you pass children to a component?

**Answer:** React passes nested JSX through the children prop. This is useful for layout components, modals, cards, tabs, and reusable wrappers.

### 26. How can you style React components?

**Answer:** Common options include CSS files, CSS modules, utility classes, styled components, and UI libraries such as Material UI. Choose based on project conventions and maintainability.

### 27. How do you organize a React project?

**Answer:** A practical structure separates components, pages/routes, hooks, services, types, utilities, and styles. Feature-based folders work well for large dashboards.

### 28. What is useRef used for at a basic level?

**Answer:** useRef stores a mutable value that does not trigger re-rendering and can also reference DOM elements. It is useful for focusing inputs, timers, and keeping latest values.

### 29. How do you show loading and error states?

**Answer:** Store loading and error state near the data request or in a data-fetching library. Good UI should tell users when data is loading, failed, empty, or successfully available.

### 30. What makes a React component reusable?

**Answer:** Reusable components have clear props, minimal hidden assumptions, good naming, and flexible composition. Examples include buttons, input fields, data cards, and table controls.

## Intermediate

### 31. How do useEffect dependencies work?

**Answer:** The dependency array tells React when to re-run an effect. Missing dependencies can create stale data, while unnecessary dependencies can cause repeated fetches or loops.

### 32. Why is cleanup important in useEffect?

**Answer:** Cleanup removes subscriptions, timers, listeners, or pending work when dependencies change or the component unmounts. It prevents memory leaks in live dashboards and real-time screens.

### 33. What is a custom hook?

**Answer:** A custom hook extracts reusable stateful logic into a function whose name starts with use. It is useful for API calls, pagination, auth state, WebSocket subscriptions, or form logic.

### 34. When should you use React Context?

**Answer:** Context shares values across a component tree without prop drilling. It works well for themes, auth user, locale, and simple global settings, but frequent updates can cause re-renders.

### 35. What is useReducer?

**Answer:** useReducer manages complex state transitions with a reducer function. It is useful for multi-step forms, filter panels, and state that changes through named actions.

### 36. What is React.memo?

**Answer:** React.memo skips re-rendering a component when props are unchanged. It is useful for expensive child components, but should be applied after measuring or spotting real re-render issues.

### 37. What is useCallback?

**Answer:** useCallback memoizes a function reference between renders. It helps when passing callbacks to memoized children or when a stable function is needed in dependencies.

### 38. What is useMemo?

**Answer:** useMemo memoizes the result of an expensive calculation. It is useful for derived table data, filtered lists, chart data, or computed permissions when recalculation is costly.

### 39. How do you avoid stale closures in React?

**Answer:** Include correct dependencies, use functional state updates, or keep latest values in refs when needed. Stale closures often appear in intervals, subscriptions, and async callbacks.

### 40. How does React batching work?

**Answer:** React batches multiple state updates into one render for better performance. In modern React, batching works across more async contexts than older versions.

### 41. What is reconciliation?

**Answer:** Reconciliation is React process of comparing previous and next UI trees to decide what DOM updates are needed. Stable keys and predictable component structure help reconciliation.

### 42. How do you optimize rendering in a large table?

**Answer:** Use stable keys, memoized rows, pagination, filtering on the server when needed, and virtualization for very large datasets. Dashboards with logs or orders benefit from this.

### 43. What is list virtualization?

**Answer:** Virtualization renders only visible list rows instead of the entire list. It improves performance for large tables such as HOS logs, product catalogs, or transaction histories.

### 44. How do you handle form validation in React?

**Answer:** Use controlled inputs, validation schemas, touched state, clear error messages, and submit guards. Libraries can help, but the validation rules should match backend expectations.

### 45. How do you manage server state in React?

**Answer:** Server state should track loading, errors, cache, freshness, and refetching. Libraries like React Query are useful, but the concept is separate from local UI state.

### 46. How is local UI state different from server state?

**Answer:** Local UI state belongs only to the interface, such as modals or selected tabs. Server state comes from APIs and needs caching, synchronization, invalidation, and error handling.

### 47. How do you design pagination in React?

**Answer:** Keep page, limit, filters, sort, total, loading, and error state explicit. For APIs, use the backend pagination contract instead of guessing from array length.

### 48. How do you implement search filters in React?

**Answer:** Use controlled inputs, debouncing, URL query state when useful, and clear reset behavior. Server-side filtering is better for large datasets.

### 49. How do you handle optimistic UI?

**Answer:** Optimistic UI updates the interface before the server confirms success. It improves speed but requires rollback logic if the API fails.

### 50. How do you handle authentication state in React?

**Answer:** Store the authenticated user, loading state, and permissions in a central place. Protect routes, hide unauthorized actions, and keep token refresh logic outside random components.

### 51. What is role-based rendering?

**Answer:** Role-based rendering shows UI based on permissions, such as admin, carrier, driver, or merchant roles. It improves UX but must not replace backend authorization.

### 52. How do you handle file uploads in React?

**Answer:** Use file inputs, preview selected files, validate size/type, show progress, and send multipart data or signed upload requests. Cloudinary-style uploads need careful error handling.

### 53. How do you integrate payment flows in React?

**Answer:** Payment UI should use provider SDKs, validate amounts server-side, handle loading and failure states, and avoid storing sensitive card data directly. Stripe flows are a common example.

### 54. What are portals in React?

**Answer:** Portals render children into a DOM node outside the parent hierarchy. They are commonly used for modals, tooltips, dropdowns, and overlays.

### 55. What is lazy loading in React?

**Answer:** Lazy loading splits components into separate chunks and loads them when needed. It reduces initial bundle size for dashboards with many routes or heavy features.

### 56. What is Suspense?

**Answer:** Suspense lets components show a fallback while waiting for lazy components or supported async data. It helps coordinate loading UI, especially with modern React and Next.js patterns.

### 57. What are error boundaries?

**Answer:** Error boundaries catch rendering errors in child components and show fallback UI. They help prevent one broken widget from crashing the entire dashboard.

### 58. How do you test React components?

**Answer:** Use unit and integration tests with tools like React Testing Library. Test user behavior, visible output, API states, and important flows rather than internal implementation details.

### 59. How do you mock APIs in React tests?

**Answer:** Mock network calls at the fetch/client boundary or use a tool like MSW. Good mocks should match real API contracts for success, error, empty, and loading states.

### 60. How do TypeScript props improve React code?

**Answer:** Typed props document component requirements and catch invalid usage at compile time. This helps teams safely reuse components across dashboards and ecommerce pages.

### 61. How do you choose a state management approach?

**Answer:** Start with local state, lift state when shared, use Context for low-frequency global values, and use dedicated libraries when state complexity grows. The choice should match the problem size.

### 62. How do React components interact with REST APIs?

**Answer:** Components should call services or hooks rather than embedding fetch logic everywhere. This keeps authentication, error mapping, and response normalization consistent.

### 63. How do you handle WebSocket updates in React?

**Answer:** Subscribe in an effect or custom hook, clean up on unmount, handle reconnects, and update normalized state efficiently. This is useful for live fleet or log monitoring.

### 64. How do you keep React forms user-friendly?

**Answer:** Show inline errors, disable duplicate submits, preserve entered data, support keyboard navigation, and provide clear success or failure feedback.

### 65. What accessibility basics matter in React?

**Answer:** Use semantic HTML, labels, focus management, keyboard support, ARIA only when needed, and sufficient contrast. Accessibility should be part of component design, not a last-minute patch.

### 66. How do you handle image-heavy React screens?

**Answer:** Use optimized image sizes, lazy loading, placeholders, and CDN transformations where available. This is relevant to ecommerce catalogs and Cloudinary-backed image workflows.

### 67. How do you prevent unnecessary API calls in React?

**Answer:** Debounce user input, cache server state, include correct effect dependencies, cancel stale requests, and trigger fetching from clear events instead of every render.

### 68. What is prop drilling, and how do you solve it?

**Answer:** Prop drilling is passing props through many layers that do not use them. Solve it with composition, colocated state, Context, or a state library when the shared data is truly global.

### 69. How do you handle empty states in React dashboards?

**Answer:** Show a clear empty state with relevant actions, such as adding a vehicle, changing filters, or refreshing data. Empty states should not look like broken loading screens.

### 70. How do you structure reusable table components?

**Answer:** Separate column definitions, row rendering, sorting, pagination, loading, empty, and action cells. Tables should remain flexible enough for drivers, orders, inventory, or logs.

## Advanced

### 71. How would you architect a large React dashboard?

**Answer:** Use feature-based modules, shared UI components, hooks for data access, route-level splitting, typed API contracts, and consistent error/loading states. This fits fleet, ecommerce, and analytics dashboards.

### 72. How would you design a reusable component library?

**Answer:** Define tokens, variants, accessibility rules, prop contracts, tests, and documentation. A good library makes common UI predictable without blocking domain-specific customization.

### 73. How do you separate server state and client state at scale?

**Answer:** Use server-state tools or clear hooks for API data, and keep UI-only state local. This avoids mixing cached backend records with temporary UI behavior.

### 74. How would you profile a slow React screen?

**Answer:** Use React Profiler, browser performance tools, network waterfall, and production metrics. Identify whether slowness comes from rendering, network, JavaScript execution, or backend latency.

### 75. How would you handle a real-time fleet dashboard in React?

**Answer:** Normalize entities by ID, batch WebSocket messages, throttle visual updates, show connection status, and refetch after reconnect. This keeps live data useful without excessive re-renders.

### 76. How would you design complex multi-step forms?

**Answer:** Use schema validation, step-level state, draft saving when needed, clear navigation, and backend-aligned validation. Complex forms should survive partial progress and show precise errors.

### 77. How would you prevent hydration issues in React/Next.js?

**Answer:** Avoid rendering browser-only values on the server, keep initial server and client markup consistent, and move client-only logic into effects or client components.

### 78. How do concurrent rendering concepts affect React code?

**Answer:** React may pause, resume, or restart rendering work. Components should be pure during render, avoid side effects outside effects, and keep state transitions predictable.

### 79. How would you design error handling for a React product?

**Answer:** Use route-level and widget-level error boundaries, API error normalization, user-friendly messages, and logging. The UI should fail gracefully instead of going blank.

### 80. How would you choose between Context and Redux/Zustand/Jotai?

**Answer:** Use Context for simple, low-frequency global values. Choose a dedicated store when updates are frequent, state has complex transitions, or debugging and middleware are important.

### 81. How would you secure a React application against XSS?

**Answer:** Avoid dangerouslySetInnerHTML, sanitize rich content, rely on safe framework rendering, apply CSP, and treat third-party scripts carefully. Ecommerce and admin content need special caution.

### 82. How would you design route protection?

**Answer:** Check auth during routing, show loading while session is verified, redirect unauthorized users, and enforce permissions server-side. UI route protection is not enough by itself.

### 83. How would you optimize React bundle size?

**Answer:** Use code splitting, remove unused libraries, prefer lightweight imports, analyze bundles, and lazy-load heavy routes. This improves first load for dashboards and storefront pages.

### 84. How would you test a critical React workflow end to end?

**Answer:** Cover the user path with realistic API responses, authentication state, validation errors, success states, and navigation. Critical workflows include checkout, driver log review, or appointment booking.

### 85. How do you design custom hooks for team reuse?

**Answer:** Keep input and return contracts clear, handle cleanup internally, expose loading/error states, and avoid surprising side effects. A hook should feel like a small API.

### 86. How would you migrate class components to hooks?

**Answer:** Start with tests, convert one component at a time, map lifecycle logic to effects, and preserve behavior. Avoid changing architecture and business logic in the same step.

### 87. How would you handle high-frequency updates from WebSocket?

**Answer:** Buffer messages, update only changed entities, virtualize long lists, and avoid recalculating everything on each event. This keeps dashboards responsive.

### 88. How do you handle permissions in reusable components?

**Answer:** Keep authorization decisions close to domain logic and pass explicit allowed actions to generic components. A table should not secretly know business roles unless it is a domain table.

### 89. How would you build an accessible modal system?

**Answer:** Trap focus, restore focus on close, support Escape, label the dialog, prevent background interaction, and test keyboard behavior. Portals are commonly used for modal rendering.

### 90. How would you design React analytics instrumentation?

**Answer:** Centralize tracking events, avoid leaking personal data, include meaningful business context, and make tracking resilient to route changes. Dashboards need both product and operational visibility.

### 91. How would you handle internationalization in React?

**Answer:** Externalize strings, support locale formatting for dates and numbers, avoid hardcoded text in reusable components, and test layout expansion. Timezone-sensitive apps need extra care.

### 92. How would you design a React data grid for production?

**Answer:** Support server-side pagination, sorting, filtering, loading, empty states, row actions, accessibility, and virtualization. Keep domain-specific cells separate from generic table mechanics.

### 93. How would you decide where state should live?

**Answer:** Place state as close as possible to where it is used, then lift or centralize only when sharing is real. This keeps components simpler and reduces accidental coupling.

### 94. How would you debug a React memory leak?

**Answer:** Check effects that subscribe to events, timers, WebSocket connections, or pending promises. Use cleanup functions and profiling to confirm components are released after unmount.

### 95. How do you handle design-system consistency?

**Answer:** Use shared tokens, components, spacing rules, and reviewed variants. Consistency matters in admin dashboards because users scan repetitive screens all day.

### 96. How would you integrate React with a backend error model?

**Answer:** Map backend error codes to user-friendly messages, field errors, retry actions, and logging. Keep raw internal errors out of the UI.

### 97. How would you structure React code for ecommerce integrations?

**Answer:** Separate product display, cart state, checkout actions, third-party API client logic, and payment status. This keeps Shopify/BigCommerce-specific details from spreading everywhere.

### 98. How would you handle progressive loading in a dashboard?

**Answer:** Load critical summary data first, defer heavy widgets, show skeletons carefully, and let each widget fail independently. Users should get useful data quickly.

### 99. How would you review React code as a senior developer?

**Answer:** Check state ownership, effect dependencies, accessibility, error/loading states, unnecessary renders, API contracts, and component boundaries. The review should protect maintainability and user experience.

### 100. How would you explain React experience from this resume in an interview?

**Answer:** Connect React to concrete outcomes: fleet dashboards for drivers and vehicles, ecommerce storefront/admin pages, real-time status screens, and analytics interfaces backed by Node.js and databases.


## Reference Docs

- [React Docs](https://react.dev/)
- [React Hooks Reference](https://react.dev/reference/react/hooks)
