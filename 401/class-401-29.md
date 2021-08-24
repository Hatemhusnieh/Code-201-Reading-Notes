# Advanced State with Reducers

### Content

1. [Review, Research, and Discussion](#review-research-and-discussion)
1. [terms](#terms)
1. [Preparation Materials](#preparation-materials)
1. [Resources](#resources)

---

## Review, Research, and Discussion

1. How can we ensure that an effect hook runs only once?
   - Automatically it only render once each mount, but we can pass an empty array [] to assure this behavior
2. Can `useState()` update more than one state variable at the same time?
   - Yes, if the variable was an object like `const [state, setSate] = useState({state1: value1, sate2: value2})`
3. Is `useState()` synchronous?
   - No, it is Asynchronous by nature

---

## Terms

- State Hook
  > The `useState()` is a Hook that allows you to have state variables in functional components , it takes the initial state as an argument and returns an array of two entries.
- Component Lifecycle
  > These methods are called the component's lifecycle methods and they are invoked in a predictable order. Basically all the React component's lifecycle methods can be split in four phases: initialization, mounting, updating and unmounting.

---

## Preparation Materials

useReducer: `const [state, dispatch] = useReducer(reducer, initialArg, init);` useReducer is one of the additional Hooks that shipped with React 16.8. An alternative to the useState Hook:

it helps you manage complex state logic in React applications. useReducer can be a good alternative to Redux or MobX — indeed, it can sometimes be an outright better option. useReducer is usually preferable to useState when you have complex state logic that involves multiple sub-values or when the next state depends on the previous one. useReducer also lets you optimize performance for components that trigger deep updates because you can pass dispatch down instead of callbacks.

Declaring state with useState `const [state, setState] = useState('default state');` useState returns an array that holds the current state value and a setState method for updating the state.

Declaring state with useReducer `const [state, dispatch] = useReducer(reducer, initialState)` useReducer returns an array that holds the current state value and a dispatch method that logically achieve the same goal of setState

---

### Resources

- [useReducer hook](https://reactjs.org/docs/hooks-reference.html#usereducer)
- [Ultimate Guide to useReducer](https://blog.logrocket.com/guide-to-react-usereducer-hook/)
