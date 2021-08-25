# React Native

### Content

1. [Review, Research, and Discussion](#review-research-and-discussion)
1. [Terms](#terms)
1. [Preparation Materials](#preparation-materials)

---

## Review, Research, and Discussion

1. Compare and Contrast Redux Toolkit with Redux “Ducks”

   - The traditional folder-based approach (**“Ducks”**) requires you to separate actions, reducers, selectors, etc into multiple files that become cumbersome while developing and refactoring. While `Redux toolkit` provides an opinionated wrapper around redux and lets us do more with less code. But, the issue with the Redux toolkit is that the project structure becomes similar to ducks and is prone to a circular dependency.

2. What is the principle advantage of Redux Toolkit.
   - Redux Toolkit makes it easier to write good Redux applications and speeds up development, by baking in our recommended best practices, providing good default behaviors, catching mistakes, and allowing you to write simpler code. Redux Toolkit is beneficial to all Redux users regardless of skill level or experience

---

## Terms

- redux toolkit slices:
  > Redux slice is a collection of reducer logic and actions for a single feature of application . Redux state is typically organized into slices, defined by the reducers that are passed to combineReducers.
- namespace:
  > A group of related elements that each have a unique name or identifier. ... A file path, which uses syntax defined by the operating system, is considered a namespace. For example, C:\Program Files\Internet Explorer is the namespace that describes where Internet Explorer files on a Windows computer.

---

## Preparation Materials

### React Native

Many different kinds of people use React Native: from advanced iOS developers to React beginners, to people getting started programming for the first time in their career. These docs were written for all learners, no matter their experience level or background.

To work with React Native, you will need to have an understanding of JavaScript fundamentals. If you’re new to JavaScript or need a refresher, you can dive in or brush up at Mozilla Developer Network.

With React, you can make components using either classes or functions. Originally, class components were the only components that could have state. But since the introduction of React’s Hooks API, you can add state and more to function components.

React Native is like React, but it uses native components instead of web components as building blocks. So to understand the basic structure of a React Native app, you need to understand some of the basic React concepts, like JSX, components, state, and props. If you already know React, you still need to learn some React-Native-specific stuff, like 444the native components. This tutorial is aimed at all audiences, whether you have React experience or not.

### Expo

Expo is a framework and a platform for universal React applications. It is a set of tools and services built around React Native and native platforms that help you develop, build, deploy, and quickly iterate on iOS, Android, and web apps from the same JavaScript/TypeScript codebase.

### Ejecting to ExpoKit

If you created an Expo project and you want a way to add custom native modules, this guide will explain how to use ExpoKit for that purpose.

Normally, Expo apps are written in pure JS and never “drop down” to the native iOS or Android layer. This is core to the Expo philosophy and it’s part of what makes Expo fast and powerful to use.

However, there are some cases where advanced developers need native capabilities outside of what Expo offers out-of-the-box. The most common situation is when a project requires a specific Native Module which is not supported by React Native Core or the Expo SDK.

In this case, Expo allows you to eject your pure-JS project from the Expo iOS/Android clients, providing you with native projects that can be opened and built with Xcode and Android Studio. Those projects will have dependencies on ExpoKit, so everything you already built will keep working as it did before.

We call this “ejecting” because you still depend on the Expo SDK, but your project no longer lives inside Expo Go. You control the native projects, including configuring and building them yourself.

---

### Resources

- [Modular Ducks - A design pattern for scalable redux architecture](https://dev.to/code_ashish/modular-ducks-a-design-pattern-for-scalable-redux-architecture-4dna)
- [getting started with react native](https://reactnative.dev/docs/getting-started)
- [react native basics ](https://reactnative.dev/docs/tutorial)
- [react native](https://reactnative.dev/)
- [expo](https://expo.dev/)
- [expo snack](https://snack.expo.dev/)
- [ejecting](https://docs.expo.dev/versions/latest/expokit/eject)
