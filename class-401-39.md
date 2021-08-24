# Redux - Additional Topics

### Content

1. [Review, Research, and Discussion](#review-research-and-discussion)
1. [Terms](#terms)
1. [Preparation Materials](#preparation-materials)
   1. [Redux Toolkit](#redux-toolkit)
   1. [RTK Query](#rtk-query)

---

## Review, Research, and Discussion

1. What’s the best practice for “pre-loading” data into the store (on application start) in a Redux application?

   - I would say to load data using `redux-thunk` middleware, after all related component are mounted (componentDisMount) state, fire an action that utilize `redux-thunk`.

2. When using a thunk/async action that dispatches the actual action, which do you export from your reducer?
   - We export the action only, as `thunk` is a middleware that will fire before each firing of the reducer it's attached to.

---

## Terms

- middleware:
  > Middleware is software that enables one or more kinds of communication or connectivity between two or more applications or application components in a distributed network. Redux middleware provides a third-party extension point between dispatching an action, and the moment it reaches the reducer. This is to modify the behavior of the dispatch action
- thunk:
  > A Middleware for `redux`. `Thunks` are the recommended middleware for basic Redux side effects logic, including complex synchronous logic that needs access to the store, and simple async logic like AJAX requests.

---

## Preparation Materials

### Redux Toolkit

The Redux Toolkit package is intended to be the standard way to write Redux logic. It was originally created to help address three common concerns about Redux:

- "Configuring a Redux store is too complicated"
- "I have to add a lot of packages to get Redux to do anything useful"
- "Redux requires too much boilerplate code"

To install `Redux ToolKit` on the creation of a new App, from terminal:

- `npx create-react-app my-app --template redux`.

Or on an existing application:

- `npm install @reduxjs/toolkit`.

#### Packages:

The tool kit includes the following:

- **configureStore()**: wraps `createStore` to provide simplified configuration options and good defaults. It can automatically combine slice reducers, adds whatever Redux middleware you supply, includes `redux-thunk` by default, and enables use of the Redux DevTools Extension.

- **createReducer()**: that lets you supply a lookup table of action types to case reducer functions, rather than writing switch statements. In addition, it automatically uses the `immer` library to let you write simpler immutable updates with normal mutative code, like `state.todos[3].completed = true`.

- **createAction()**: generates an action creator function for the given action type string. The function itself has `toString()` defined, so that it can be used in place of the type constant.

- **createSlice()**: accepts an object of reducer functions, a slice name, and an initial state value, and automatically generates a slice reducer with corresponding action creators and action types.

- **createAsyncThunk**: accepts an action type string and a function that returns a promise, and generates a thunk that dispatches `pending/fulfilled/rejected` action types based on that promise.

- **createEntityAdapter**: generates a set of reusable reducers and selectors to manage normalized data in the store.

- The **createSelector** utility from the Reselect library, re-exported for ease of use.

### RTK Query

`RTK Query` purpose is to solve the use case of data fetching and caching, supplying a compact, but powerful toolset to define an API interface layer for your app.

`RTK Query` is built on top of the Redux Toolkit core for its implementation, using Redux internally for its architecture.

`RTK Query` is included within the installation of the core Redux Toolkit package. It is available via either of the two entry points below:

```
import { createApi } from '@reduxjs/toolkit/query'

/* React-specific entry point that automatically generates
   hooks corresponding to the defined endpoints */
import { createApi } from '@reduxjs/toolkit/query/react'

```

#### Packages:

- `createApi()`: The core of RTK Query's functionality. It allows you to define a set of endpoints describe how to retrieve data from a series of endpoints, including configuration of how to fetch and transform that data. In most cases, you should use this once per app, with "one API slice per base URL" as a rule of thumb.
- `fetchBaseQuery()`: A small wrapper around `fetch` that aims to simplify requests. Intended as the recommended `baseQuery` to be used in `createApi` for the majority of users.
- `<ApiProvider />`: Can be used as a `Provider` if you do not already have a Redux store.
- `setupListeners()`: A utility used to enable `refetchOnMount` and `refetchOnReconnect` behaviors.

---

### Resources

- [Middleware](https://www.ibm.com/cloud/learn/middleware)
- [Redux Fundamentals, Part 4: Store](https://redux.js.org/tutorials/fundamentals/part-4-store)
- [Redux Thunk](https://github.com/reduxjs/redux-thunk)
- [Redux Toolkit (RTK)](https://redux-toolkit.js.org/introduction/getting-started)
