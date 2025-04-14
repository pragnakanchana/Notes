# React Basics

## Introduction

- React is a JavaScript library for building user interfaces.
- JSX may remind you of a template language, but it comes with the full power of JavaScript.

## Components

- Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both.

## JSX Compilation

- Babel compiles JSX down to `React.createElement()` calls.
- Both the examples are same:
  ```js
  const element = (<h1 className="greeting">Hello, world!</h1>);
  const element = React.createElement('h1', { className: 'greeting' }, 'Hello, world!');
  ```
- `React.createElement()` performs a few checks to help you write bug-free code but essentially it creates an object like this:
  ```js
  const element = { type: 'h1', props: { className: 'greeting', children: 'Hello, world!' } };
  ```
- These objects are called **React elements**.
- React elements are immutable.
  - One of the ways to update the UI is to create a new element.
- React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

---

## Components & Props

- Components let you split the UI into independent, reusable pieces, and think about each piece in isolation.
- Components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.
- Functional Components are JS Functions. They accept a single `props` (which stands for properties) object argument with data and return a React element.
- Props are **Read Only**.
- All React components must act like pure functions with respect to their props. This ensures **Predictability** and **Reusability**.

---

## State

- State is similar to props, but it is private and fully controlled by the component.
- `this.props` is set up by React itself and `this.state` has a special meaning, but you are free to add additional fields to the class manually.

### Three important things to learn about State:

1. Do not update state directly with assign operator, which doesn't cause re-render.
2. State updates can be asynchronous; React may batch multiple state values into one update.
   - So, do not rely on state update with respect to previous state value.
3. State updates are merged.
   - If you update `this.state.x` at one line and `this.state.y` at another, both updated values persist.

---

## Lists & Keys

- https://www.linkedin.com/pulse/everything-you-need-know-key-prop-react-denis-bunchenko/

---

## Composition Over Inheritance

- React uses Composition methodology over Inheritance.
- Composition is about reusing components wherever needed.

---

## Context API

- Context provides a way to pass data through the component tree without having to pass props down manually at every level.
- Context is designed to share data that can be considered “global” for a tree of React components.

---

## Why Hooks?

- When a variable is used inside tags with `{}` -> it's called variable injection.
- State is a mechanism React has:
  - Any change in state is constantly monitored and leads to re-render of UI.
- React batches state updates using the concept of **reconciliation**.
- To avoid batching issues, use a callback within `setState`, which gives `prevState` as value.

### Useful Links:

- [React Source: ReactHooks.js](https://github.com/facebook/react/blob/main/packages/react/src/ReactHooks.js)
- [Video on Hooks](https://www.youtube.com/watch?v=4LI9sv8r6ss&list=PLRAV69dS1uWQos1M1xP6LWN6C-lZvpkmq&index=6)

---

## Virtual DOM, Fiber, and Reconciliation

- [React Fiber Architecture Readme](https://github.com/acdlite/react-fiber-architecture)

### Why batch updates?

- If a transition goes A -> B -> C -> A in milliseconds, updating DOM each time is wasteful. The user doesn't notice those in-between states.

### Reconciliation

- The algorithm React uses to diff one tree with another to determine which parts need to be changed.
- React maintains an in-memory virtual representation of the DOM and keeps it in sync using batch updates.

### DOM Overview

- **DOM**: Document Object Model
- HTML defines tags, but JavaScript and the DOM API give meaning and interactivity to those tags.
- DOM allows traversal and manipulation via JavaScript (e.g., `getElementById`).

### DOM Manipulation

- Comprises of:
  - Querying the DOM
  - DOM Update
  - Rendering/Re-rendering

- Frequent updates and re-renders degrade performance.
- React optimizes this by updating a virtual DOM, then syncing only the necessary changes to the real DOM.

### Virtual DOM

- An in-memory copy of the actual DOM.
- Faster for internal operations and syncing.
- Allows diffing before touching the real DOM.
- write to original DOM happens after batching a set of changes - happens at a certain frequency.

### Diffing Algorithm

1. If the root itself changes, clear the entire subtree.
2. If `className` changes, only updates the attribute and tear down of sub tree doesn't happen.
3. For lists:
   - Key prop helps avoid expensive line-by-line comparison.

- [Video on Virtual DOM and Reconciliation](https://www.youtube.com/watch?v=rysTbzKOEO0)

---

## useEffect, useRef, and useCallback

### useCallback

1. Caches a function definition between re-renders.
2. Returns the cached function.
3. Can only be used at component level (not inside loops or conditions).
4. On initial render, it returns the provided function.
5. On re-renders, if dependencies haven't changed, the cached function is reused.
6. Helps avoid unnecessary renders when functions are passed as props.
7. Similar to useMemo but for functions.
8. `useCallback` caches functions.

### useMemo

1. Caches a calculated value between re-renders.
2. Returns the memoized value, not the function.
