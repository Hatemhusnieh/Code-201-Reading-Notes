# Redux - Asynchronous Actions

### Content

1. [Review, Research, and Discussion](#review-research-and-discussion)
1. [Terms](#terms)
1. [Preparation Materials](#preparation-materials)

---

## Review, Research, and Discussion

1. How granular should your reducers be?
   - It is difficult to manage states that are deeply nested, so more reducers is better than only a few. Redux gives us combineReducers to let us define more precisely what our initial state will look like.
2. Pro or Con – multiple reducers can “fire” when a commonly named action is dispatched

   - It depends on the implementation, it can cause errors if written poorly, or can result in clean firm code if done with caution.

3. Name a strategy for preventing the above
   - Make a reducer for each component that will be affected by the dispatcher, only effecting a specific amount of the state it self.

---

## Terms

- store:
  > store is an immutable object tree in Redux. A store is a state container which holds the application’s state. Redux can have only a single store in your application. Whenever a store is created in Redux, you need to specify the reducer.
- combined reducers
  > helper function turns an object whose values are different reducing functions into a single reducing function you can pass to createStore.

---

## Preparation Materials

### Async Actions

Both of the middleware in that last section were very specific and only do one thing. It would be nice if we had a way to write any async logic ahead of time, separate from the middleware itself, and still have access to dispatch and getState so that we can interact with the store.

What if we wrote a middleware that let us pass a function to dispatch, instead of an action object? We could have our middleware check to see if the “action” is actually a function instead, and if it’s a function, call the function right away. That would let us write async logic in separate functions, outside of the middleware definition.

### Thunk middleware

With a plain basic Redux store, you can only do simple synchronous updates by dispatching an action. Middleware extends the store’s abilities, and lets you write async logic that interacts with the store.

Thunks are the recommended middleware for basic Redux side effects logic, including complex synchronous logic that needs access to the store, and simple async logic like AJAX requests.

### Redux Thunk

By default, Redux’s actions are dispatched synchronously, which is a problem for any non-trivial app that needs to communicate with an external API or perform side effects. Redux also allows for middleware that sits between an action being dispatched and the action reaching the reducers.

There are two very popular middleware libraries that allow for side effects and asynchronous actions: Redux Thunk and Redux Saga. In this post, you will explore Redux Thunk.

Thunk is a programming concept where a function is used to delay the evaluation/calculation of an operation.

## Redux Thunk

is a middleware that lets you call action creators that return a function instead of an action object. That function receives the store’s dispatch method, which is then used to dispatch regular synchronous actions inside the function’s body once the asynchronous operations have been completed.

### Resources

- [async actions](https://redux.js.org/tutorials/fundamentals/part-6-async-logic)
- [thunk middleware](https://github.com/reduxjs/redux-thunk)
- [redux thunk](https://www.digitalocean.com/community/tutorials/redux-redux-thunk)
