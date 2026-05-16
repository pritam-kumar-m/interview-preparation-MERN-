# Redux Interview Questions & Answers

## Beginner

1. What is Redux?

- Redux is a predictable state container for JavaScript apps that centralizes application state in a single store and enforces unidirectional data flow.

2. What are the core concepts of Redux?

- Store: holds the state.
- Action: plain object describing "what happened".
- Reducer: pure function that returns next state given current state and action.
- Dispatch: method to send actions to the store.

3. What does a Redux action look like?

- A plain object with a `type` field and optional payload, e.g. `{ type: 'ADD_TODO', payload: { text: 'Buy milk' } }`.

4. What is a reducer?

- A pure function (state, action) => newState that does not mutate the input state and returns updated state based on action type.

5. How do you create a store?

- Use `createStore(rootReducer, preloadedState, enhancer)` or `configureStore` from Redux Toolkit.

6. Why should reducers be pure?

- Pure reducers are predictable, testable, and enable features like time-travel debugging.

## Intermediate

7. What is middleware in Redux?

- Middleware intercepts dispatched actions before they reach reducers, useful for logging, crash reporting, async handling (e.g., `redux-thunk`, `redux-saga`).

8. What is `redux-thunk` and how does it work?

- `redux-thunk` allows action creators to return functions (thunks) instead of plain objects. Thunks receive `dispatch` and `getState` to perform async work and dispatch actions.

9. How do you handle async actions in Redux?

- Common approaches: `redux-thunk` (simple functions), `redux-saga` (generator-based side effects), `redux-observable` (RxJS epics), or use async logic in RTK Query.

10. What is `combineReducers`?

- Utility to split reducer logic into multiple reducers keyed by state slice, producing a root reducer that delegates to child reducers.

11. How does `connect()` differ from `useSelector`/`useDispatch`?

- `connect()` (HOC) maps state/dispatch to props; hooks (`useSelector`, `useDispatch`) provide direct access inside functional components. Hooks are simpler for new code; `connect` can offer performance optimizations via `mapStateToProps` selectors.

12. How should you structure Redux state?

- Keep state normalized (no nested arrays of objects), store IDs and entities separately, avoid storing derived data, and keep UI-only state local when possible.

13. What is memoization in selectors and why use it?

- Memoized selectors (e.g., `reselect`) cache derived computations so expensive selectors only recompute when inputs change, improving performance.

14. How to update state immutably in reducers?

- Use object/array spread, `Array.prototype.map/filter`, or helper libraries like `immer` to produce new state without mutating originals.

## Advanced

15. What is Redux Toolkit (RTK) and why use it?

- RTK is the official, opinionated toolset for Redux that simplifies setup (`configureStore`), reduces boilerplate (`createSlice`, `createAsyncThunk`), and encourages best practices.

16. What is `createSlice`?

- RTK helper that combines action type definitions and reducers into a single slice; it auto-generates action creators and supports "mutating" syntax powered by `immer`.

17. How does `createAsyncThunk` simplify async logic?

- `createAsyncThunk` encapsulates async flows and generates pending/fulfilled/rejected action types; reducers can handle these lifecycle actions cleanly.

18. What are common Redux performance pitfalls?

- Large state objects causing frequent re-renders, non-memoized selectors, heavy computations in render, passing new object/array literals as props causing reference changes.

19. How to avoid unnecessary re-renders with Redux?

- Use memoized selectors, split connected components to smaller pieces, use `React.memo`, avoid inline functions/objects as props, and keep component-local state for ephemeral UI.

20. How do you test Redux logic?

- Test reducers as pure functions, test action creators for correct action objects (or thunks with mocked dispatch), and test connected components by mocking the store or using `Provider` with a test store.

21. What is time-travel debugging and how does Redux enable it?

- Time-travel debugging records actions and state history so you can revert or replay state; Redux's pure reducers and single store make replaying actions possible (Redux DevTools implements this).

22. How to handle optimistic updates in Redux?

- Update UI state immediately on action dispatch, then perform async request; on success keep state, on failure roll back using saved previous state or compensating actions.

23. Explain how to migrate a large app to Redux Toolkit.

- Introduce RTK gradually by replacing store setup with `configureStore`, convert feature reducers to `createSlice`, adopt `createAsyncThunk` for async flows, and keep interoperability with existing code during migration.

24. What is selector composition?

- Build small selectors that extract slices of state, then compose them to create higher-level derived data, improving reuse and testability.

25. When should you avoid Redux?

- For very small apps or simple state needs, local component state or Context + hooks may be simpler; avoid Redux if it adds unnecessary complexity.

---

*File created: concise Redux Q&A for interviews.*
