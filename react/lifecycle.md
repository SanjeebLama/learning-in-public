# Life cycle of REACT

- A React component goes through three main phases in its lifecycle: Mounting, Updating, and Unmounting.
- Each phase has specific methods that you can use to perform different actions at different points.
- Here's a breakdown:

![React-Lifecycle](https://media.geeksforgeeks.org/wp-content/uploads/20230804133715/gfg.png)

1. **Initialization:**

- This is the stage where the component is constructed with the given Props and default state.
- This is done in the constructor of a Component Class.

2. **Mounting:**

- Mounting is the stage of rendering the JSX returned by the render method itself.

3. **Updating:**

- Updating is the stage when the state of a component is updated and the application is repainted.

4. **Unmounting:**

- As the name suggests Unmounting is the final step of the component lifecycle where the component is removed from the page.

### **Detail Explanation**

1. **Mounting:**

- This is where the component is created and inserted into the DOM.
  - **Methods:**
  - **constructor (optional):** Used for initializing state and binding event handlers. (Class components only)
  - **static getDerivedStateFromProps (optional):** Updates state based on incoming props before rendering.
  - **render:** Returns the JSX that represents the component.
  - **componentDidMount:** Called after the component is inserted into the DOM. Ideal for side effects like fetching data or setting up subscriptions.

2. **Updating:**

- This happens when a component's state or props change.
  **Methods**:
  - **static getDerivedStateFromProps (optional):** Can also be used to update state based on new props during updates.
  - **shouldComponentUpdate (optional):** Allows controlling whether the component should re-render based on changes.
  - **render:** Re-renders the component with the updated state or props.
  - **getSnapshotBeforeUpdate (optional):** Captures DOM information before the update for later use.
  - **componentDidUpdate (optional):** Called after the component updates. Can be used for side effects like updating the DOM based on state changes.

3. **Unmounting:**

- This occurs when the component is removed from the DOM.
  **Method:**
  - **componentWillUnmount (optional):** Called before the component is removed. Useful for cleaning up resources like timers or subscriptions.

**Additional Notes:**

> _Functional components don't have lifecycle methods like constructor or componentDidMount, but they have hooks like useEffect that can achieve similar functionality._

- New lifecycle methods introduced in React 16.3+ like getDerivedStateFromProps and getSnapshotBeforeUpdate are optional and have specific use cases.

Remember: Understanding the React component lifecycle is crucial for building efficient and predictable applications. Choose the appropriate methods based on your needs and ensure proper cleanup for unmounted components.
