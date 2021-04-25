# Introduction to React and Components  
## React Tutorial through ‘Passing Data Through Props’  
###  What Is React?  
**React** is a declarative, efficient, and flexible JavaScript library for building user interfaces. It lets you compose complex UIs from small and isolated pieces of code called “_**components**_”.  

- We use **components** to tell React what we want to see on the screen. When our data changes, React will efficiently update and re-render our components.

- A component takes in parameters, called `props` (short for “**properties**”), and returns a hierarchy of views to display via the `render` method

- Passing `props` is how information flows in React apps, from **parents** to **children**.

- The React Devtools extension for `Chrome` and `Firefox` lets you inspect a React component tree with your browser’s developer tools.

## Hello World
- React example:  
```
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);

```

## Introducing JSX

- **JSX** is  a syntax extension to `JavaScript`, and it produces `React` “**elements**”

### Why JSX?

- Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both

- using JSX is optional, but it is helpful as a visual aid when working with UI inside the JavaScript code.

### Embedding Expressions in JSX

- You can put any valid JavaScript expression inside the curly braces in JSX
```
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;

ReactDOM.render(
  element,
  document.getElementById('root')
);

```

- You can embed `functions` results too

```
function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const user = {
  firstName: 'Harper',
  lastName: 'Perez'
};

const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);

ReactDOM.render(
  element,
  document.getElementById('root')
); 
```

### JSX is an Expression Too

- you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions:
```
function getGreeting(user) {
  if (user) {
    return <h1>Hello, {formatName(user)}!</h1>;
  }
  return <h1>Hello, Stranger.</h1>;
}
```

### Specifying Attributes with JSX

- You may use quotes to specify string literals as attributes, and curly braces to embed a JavaScript expression in an attribute:

`const element = <div tabIndex="0"></div>;`
`const element = <img src={user.avatarUrl}></img>;`

### Specifying Children with JSX

- If a tag is empty, you may close it immediately with />, like XML

- JSX tags may contain children

### JSX Prevents Injection Attacks 

- Everything is converted to a string before being rendered in **JSX**. This helps prevent XSS (cross-site-scripting) attacks.

### JSX Represents Objects

- Every JSX component can be viewed as an object.

- this:

```
const element = (
  <h1 className="greeting">
    Hello, world!
  </h1>
);

```
- can be viewed as this:

```
const element = {
  type: 'h1',
  props: {
    className: 'greeting',
    children: 'Hello, world!'
  }
};

```

## Rendering Elements

- Unlike browser `DOM elements`, `React elements` are plain objects, and are cheap to create. **React DOM** takes care of updating the **DOM** to match the **React** elements.

### Rendering an Element into the DOM

- Applications built with just React usually have a single root DOM node.

- You may have as many isolated root DOM nodes as you like.

- To render a **React element** e use the `render()` function.
```
const element = <h1>Hello, world</h1>;
ReactDOM.render(element, document.getElementById('root'));
```

### Updating the Rendered Element

- React elements are immutable. Once you create an element, you can’t change its children or attributes.

- A way to update the UI is to create a new element, and pass it to `ReactDOM.render()`.

### React Only Updates What’s Necessary

- React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

## Components and Props

- Conceptually, **components** are like **JavaScript** **functions**. They accept arbitrary inputs (called “`props`”) and return **React elements** describing what should appear on the screen.

### Function and Class Components

- he simplest way to define a component is to write a JavaScript function:
```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

- You can also use an **ES**6 class to define a component:
```
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

- **Elements** can also represent _**user-defined components**_:
`const element = <Welcome name="Sara" />;`

### Composing Components

- Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail

```
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

function App() {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

### Extracting Components

- Splitting components into smaller components is a good thing, because having a palette of reusable components pays off in larger apps.

### Props are Read-Only

- Whether you declare a component as a function or a class, it must never modify its own props.

- All React components must act like pure functions with respect to their props.

- A pure function, is a function that do not change the value/type of its components and return the same results for the same inputs always.

