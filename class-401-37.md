# Redux - Combined Reducers

### Content

1. [Review, Research, and Discussion](#review-research-and-discussion)
1. [Terms](#terms)
1. [Preparation Materials](#preparation-materials)

---

## Review, Research, and Discussion

1. Why choose Redux instead of the Context API for global state?

   - The ability to add in middleware and because, the `Context API` (currently) is not built for high-frequency updates.

2. What is the purpose of a reducer?

   - To define case to dispatch action to and make a default case whenever a something bad happens.

3. What does an action contain?

   - I contains the logic used to change the value of states.

4. Why do we need to copy the state in a reducer?
   - To keep the reducers as pure functions that does not change variables (states) directly.

---

## Terms

- immutable state
  > A state that can not be modified after initialization.
- time travel in redux
  > The ability step forward and backward through the state of you application, empowering the developer understand exactly what is happening at any point in the app’s lifecycle.
- action creator
  > a function that returns an action object. Redux includes a utility function called bindActionCreators for binding one or more action creators to the store’s dispatch() function.
- reducer
  > a pure function that takes an action and the previous state of the application and returns the new state
- dispatch
  > a function of the Redux store. You call store. dispatch to dispatch an action. This is the only way to trigger a state change.

---

## Preparation Materials

`Multiple Reducers` Reducers are a great concept in Redux, because they allow your react application to have specific pieces of data that all update synchronously. All reducers run against your Redux store, and then the store triggers a change event and your entire React.js application re-renders.

The most common state shape for a Redux app is a plain Javascript object containing “slices” of domain-specific data at each top-level key. Similarly, the most common approach to writing reducer logic for that state shape is to have “slice reducer” functions, each with the same (state, action) signature, and each responsible for managing all updates to that specific slice of state. Multiple slice reducers can respond to the same action, independently update their own slice as needed, and the updated slices are combined into the new state object.

There are two ways to define the initial shape and contents of your store’s state. First, the createStore function can take preloadedState as its second argument. This is primarily intended for initializing the store with state that was previously persisted elsewhere, such as the browser’s localStorage. The other way is for the root reducer to return the initial state value when the state argument is undefined. These two approaches are described in more detail in Initializing State, but there are some additional concerns to be aware of when using combineReducers.

combineReducers takes an object full of slice reducer functions, and creates a function that outputs a corresponding state object with the same keys. This means that if no preloaded state is provided to createStore, the naming of the keys in the input slice reducer object will define the naming of the keys in the output state object. The correlation between these names is not always apparent, especially when using ES6 features such as default module exports and object literal shorthands.

---

### Resources

- [Redux vs React's Context API](https://academind.com/tutorials/reactjs-redux-vs-context-api/)
- [Multiple Reducers Example](https://www.youtube.com/watch?v=gBER4Or86hE)
- [Redux Docs: Using Combined Reducers](https://redux.js.org/usage/structuring-reducers/using-combinereducers/)
- [Redux Docs: Combined Reducer Syntax](https://redux.js.org/api/combinereducers/)
