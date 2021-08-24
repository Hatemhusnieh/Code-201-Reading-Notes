# Component Lifecycle / useEffect() Hook

### Content

1. [Review, Research, and Discussion](#review-research-and-discussion)
1. [terms](#terms)
1. [Preparation Materials](#preparation-materials)
1. [Resources](#resources)

---

## Review, Research, and Discussion

1. Why do we not need more .html pages in a multi-page React app?

   - In the Multipage apps , we split up our components but a lot of pages are going to be normal HTML pages, and widgets we dump in like an Image gallery that is managed by React, so the entire page is not under React control.

2. If we wanted a component to show up on every page, where would we put it and why?

- Outside the `<BrowserRouter/>`
- Inside the `<BrowserRouter />`, outside a `<Route />`
- Inside a `<Route />`
  - The second option. To use routes, everything needs to be inside a BrowserRouter. For content to be seen by all pages, it can’t be inside a route component. The route component is meant for content that needs to be switched out if a user goes from page to page.

3. What does routing do with the components that were rendered when a new route is requested?

   - it goes to the new component and remove the old one _cleans up _

4. What does props.children contain?

   - children is a special property of React components which contains any child elements defined within the component, e.g. the `div`s inside Example above. {this.props.children} includes those children in the rendered result.

5. How do useState() and this.setState() differ?
   - setState is merging the previous state with the new one, it means that you don't have to pass the full state object every time you want to change some part of the state. React will update given properties and won’t touch the rest. The useState’s updater rewrites a previous state with a new one and it does not perform any merging. Its just replacement instead of merging.

---

## Terms

- State Hook:

  > The state is an instance of React Component can be defined as an object of a set of observable properties that control the behavior of the component. In other words, the State of a component is an object that holds some information that may change over the lifetime of the component.

- Mounting and Un-Mounting:

  > Mounting: is the process of outputting the virtual representation of a component into the final UI representation (e.g. DOM or Native Components).

  > Un-Mounting: This method is called just before the component gets destroyed. Any clean up statements should be executed inside this method.

---

## Preparation Materials

### Using the Effect Hook

- A Hook is a special function that lets you “hook into” React features. For example, useState is a Hook that lets you add React state to function components. (Links to an external site.) Hooks apply the React philosophy (explicit data flow and composition) inside a component, rather than just between the components
- The Effect Hook, useEffect, adds the ability to perform side effects from a function component. (Links to an external site.)
- It serves the same purpose as componentDidMount, componentDidUpdate, and componentWillUnmount in React classes.

```
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });
```

---

### Resources

-[effects hook](https://reactjs.org/docs/hooks-effect.html)
