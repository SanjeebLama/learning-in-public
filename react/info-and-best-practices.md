### Update state based on current state in react

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- In React, when you need to update state based on the current state, it's recommended to use the functional form of setState() rather than relying on the previous state directly.

- This ensures that you're working with the most up-to-date state value and avoids potential issues related to asynchronous state updates.

**Here's an example to illustrate the potential issue:**

```javascript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount(count + 1); // Incorrect: Using count directly
  };

  const decrementCount = () => {
    setCount(count - 1); // Incorrect: Using count directly
  };

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={incrementCount}>Increment</button>
      <button onClick={decrementCount}>Decrement</button>
    </div>
  );
}

export default Counter;
```

- In this example, if the "Decrement" button is clicked multiple times in quick succession, React might batch the state updates, and `count` might not reflect the latest state value.

- As a result, you might not get the expected behavior of decrementing the count by 1 each time.

- To ensure that you're working with the most up-to-date state value, _it's best practice to use the functional form of `setState()` and rely on the previous state value provided as an argument to the updater function_:

```javascript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount((prevCount) => prevCount + 1); // Correct: Using functional form of setState
  };

  const decrementCount = () => {
    setCount((prevCount) => prevCount - 1); // Correct: Using functional form of setState
  };

  return (
    <div>
      <h2>Count: {count}</h2>
      <button onClick={incrementCount}>Increment</button>
      <button onClick={decrementCount}>Decrement</button>
    </div>
  );
}

export default Counter;
```

- Using the functional form of `setState()` ensures that you're always working with the most up-to-date state value, avoiding potential issues related to stale state or race conditions.

- It's a recommended best practice when updating state based on the current state value in React components.

</details>

### For data that should not trigger rerender, don't use state. Use a regular variable instead.

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- When managing state in React, it's essential to differentiate between data that should trigger re-renders and data that should not.

- In React, changes to state or props typically trigger component re-renders, which can impact performance if unnecessary re-renders occur.

_Here's a breakdown of the concept:
_

1. **State vs. Regular Variables**:
   ![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/65edaaa6-ad20-48a0-9423-30cc07bd5db6)

   - State (managed via `useState` hook or `this.state` in class components) is used for data that influences the component's appearance or behavior and should trigger re-renders when updated.
   - Regular variables (declared using `let` or `const` outside the component function or class) are used for data that doesn't affect the component's rendering and doesn't need to trigger re-renders.

2. **Avoid Unnecessary Re-Renders**:

   - If data doesn't affect the component's rendering, there's no need to store it in state. Using state for such data can lead to unnecessary re-renders when that data changes, even if those changes don't impact the UI.
   - By using regular variables for non-rendering data, you can prevent unnecessary re-renders and optimize the performance of your React components.

3. **Example**:

   ```javascript
   import React from "react";

   function Counter() {
     // State for count, which affects the rendering
     const [count, setCount] = React.useState(0);

     // Regular variable for non-rendering data (does not trigger re-renders)
     const incrementAmount = 5;

     const incrementCount = () => {
       setCount((prevCount) => prevCount + incrementAmount);
     };

     return (
       <div>
         <h2>Count: {count}</h2>
         <button onClick={incrementCount}>Increment</button>
       </div>
     );
   }

   export default Counter;
   ```

- In this example, `count` is stored in state because it affects the rendering of the `Counter` component.
- However, `incrementAmount` is a regular variable because it doesn't influence the component's appearance or behavior and doesn't need to trigger re-renders.
- By using a regular variable for `incrementAmount`, we avoid unnecessary re-renders caused by changes to this value.

</details>

### Controlled Element

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Controlled components in React are form elements whose values are controlled by _React state_.

- This means that the value of the input element is controlled by React's state, and any changes to the input value are handled by updating the state.

- Controlled components offer a powerful way to manage form data and ensure that the state and UI remain synchronized.

**Here's an example of how to create a controlled component in React and some best practices to follow:**

```jsx
import React, { useState } from "react";

function ControlledForm() {
  // Initialize state for form input
  const [formData, setFormData] = useState({
    username: "",
    email: "",
  });

  // Event handler for input changes
  const handleChange = (event) => {
    // Update state with new input value
    setFormData({
      ...formData,
      [event.target.name]: event.target.value,
    });
  };

  // Event handler for form submission
  const handleSubmit = (event) => {
    event.preventDefault();
    // Handle form submission with current form data
    console.log("Form submitted:", formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Username:
        <input
          type="text"
          name="username"
          value={formData.username}
          onChange={handleChange}
        />
      </label>
      <br />
      <label>
        Email:
        <input
          type="email"
          name="email"
          value={formData.email}
          onChange={handleChange}
        />
      </label>
      <br />
      <button type="submit">Submit</button>
    </form>
  );
}

export default ControlledForm;
```

In this example:

- We use the `useState` hook to initialize state for the form input fields (`username` and `email`).
- Each input element has a `value` attribute that is set to the corresponding value from state (`formData.username` and `formData.email`).
- We define an `onChange` event handler (`handleChange`) that updates the state (`formData`) whenever the input value changes.
- The form has an `onSubmit` event handler (`handleSubmit`) that prevents the default form submission behavior and logs the current form data to the console.
- By following these best practices, we ensure that the form elements are controlled by React state, and any changes to the input values are handled and reflected in the state. This helps maintain a single source of truth for the form data and ensures that the UI remains synchronized with the state. Additionally, we handle form submission in a controlled manner, enabling validation, error handling, and other logic as needed.

</details>

### State vs Props

<details>
  <summary> <b>Click to view the answer.</b> </summary>

> Updating state causes component to re-render and Receiving new props causes the component to re-render, usually when the parent's state has been updated.

| Aspect             | Props                                                                                 | State                                                                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| **Definition**     | External data passed into a component.                                                | Internal data managed by a component.                                                                                                    |
| **Scope**          | Received from parent component.                                                       | Local to the component where it is declared.                                                                                             |
| **Mutability**     | Immutable. Cannot be modified by the component receiving them.                        | Mutable. Can be updated using setState() in functional components or this.setState() in class components.                                |
| **Initialization** | Provided by the parent component when the child component is rendered.                | Initialized internally within the component, typically using useState() hook in functional components or this.state in class components. |
| **Usage**          | Mainly used for passing data from parent to child components.                         | Used for managing dynamic data within a component, such as user input, UI state, or data fetched from APIs.                              |
| **Updating**       | Changes in props trigger re-renders in the component receiving them.                  | Changes in state trigger re-renders in the component where it is declared.                                                               |
| **Access**         | Accessed via props object in functional components or this.props in class components. | Accessed directly within the component using useState hook or this.state in class components.                                            |

This table summarizes the key differences between props and state in React, including their definitions, scope, mutability, initialization, usage, updating behavior, and access methods. Understanding these differences is essential for effective React component development.

</details>

### Passing Arugments to onClick Event Handlers in React.

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Using `onClick={() => handleCardClick(card.id)}` is a common pattern in React when you need to pass arguments to event handler functions.

- This approach ensures that the `handleCardClick` function is called with the correct `card.id` when the `onClick` event occurs.

- _However, directly passing `handleCardClick(card.id)` like `onClick={handleCardClick(card.id)}` will not work as expected._ Here's why:

1. **Function Invocation vs. Function Reference**:

   - In React, event handlers like `onClick` expect a function reference rather than the result of a function call.
   - When you use `onClick={handleCardClick(card.id)}`, you're actually invoking `handleCardClick` immediately during the rendering phase, rather than waiting for the click event.
   - This means that `handleCardClick(card.id)` will be executed when the component renders, not when the user clicks the card.

<details>
  <summary> <b>Function invocation and function reference meaning</b> </summary>

Function invocation and function reference are concepts in programming, particularly in JavaScript, that relate to _how functions are called or used_.

1. **Function Invocation**:

   - Function invocation refers to the act of calling or executing a function to perform a specific task.
   - When a function is invoked, its code block is executed, and any parameters passed to the function are evaluated.
   - In JavaScript, function invocation typically involves using parentheses `()` after the function name, along with any arguments passed inside the parentheses.
   - Example:

     ```javascript
     function sayHello(name) {
       console.log(`Hello, ${name}!`);
     }

     sayHello("John"); // Function invocation: Calling the sayHello function with the argument "John"
     ```

2. **Function Reference**:

   - Function reference refers to a value that points to the location in memory where a function is stored.
   - In JavaScript, functions are first-class citizens, which means they can be assigned to variables, passed as arguments to other functions, and returned from other functions.
   - A function reference is essentially a variable that holds a reference to a function, allowing you to call the function later by using the variable name followed by parentheses.
   - Example:

     ```javascript
     function sayHello(name) {
       console.log(`Hello, ${name}!`);
     }

     const helloFunction = sayHello; // Assigning the sayHello function to the helloFunction variable
     helloFunction("John"); // Function reference: Calling the function using the helloFunction variable
     ```

In summary, function invocation involves calling a function to execute its code, typically using parentheses, while function reference involves storing a reference to a function in a variable, which can then be used to call the function later. Understanding these concepts is essential for effectively working with functions in JavaScript and other programming languages.

</details>

2. **Closure Over Variables**:
   - Using an arrow function in the `onClick` attribute (`onClick={() => handleCardClick(card.id)}`) creates a closure over the `card.id` variable, ensuring that the correct `card.id` is captured and passed to the `handleCardClick` function when the click event occurs.
   - This approach delays the execution of `handleCardClick` until the click event happens, ensuring that the correct `card.id` is used.

In summary, using `onClick={() => handleCardClick(card.id)}` ensures that `handleCardClick` is called with the correct `card.id` when the card is clicked, while directly passing `handleCardClick(card.id)` would execute the function immediately and not wait for the click event.

</details>

### Thinking in `state transitions not element mutation`

<details>
  <summary> <b>Click to view the answer.</b> </summary>

> "Thinking in state transitions, not element mutation" emphasizes the importance of managing state changes in React by updating state variables rather than directly mutating the DOM elements.

In short:

- **State Transitions**: Focus on updating React component state to reflect changes in the application's data or UI state.
- **Element Mutation**: Avoid directly manipulating or mutating DOM elements, as this can lead to inconsistent UI states and unpredictable behavior.

> By following this principle, you ensure that your React components remain predictable, maintainable, and easier to debug, as state changes are managed through React's state management mechanisms rather than direct DOM manipulation.

- Let's consider a simple example where we have a counter component in React.
- We'll explore the difference between thinking in state transitions and directly mutating elements.

1. **Thinking in State Transitions**:

```jsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const incrementCount = () => {
    setCount((prevCount) => prevCount + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={incrementCount}>Increment</button>
    </div>
  );
}

export default Counter;
```

In this example:

- We use `useState` to manage the state of the counter.
- When the "Increment" button is clicked, the `incrementCount` function is called, which updates the state by incrementing the count value using the `setCount` function.
- React re-renders the component with the updated count value, reflecting the state transition.

2. **Directly Mutating Elements**:

```jsx
import React, { useState } from "react";

function Counter() {
  let count = 0; // Initial count value

  const incrementCount = () => {
    count++; // Directly mutating the count variable
    // This will NOT trigger a re-render in React
    document.getElementById("count").innerText = count; // Directly mutating the DOM element
  };

  return (
    <div>
      <p>
        Count: <span id="count">0</span>
      </p>
      <button onClick={incrementCount}>Increment</button>
    </div>
  );
}

export default Counter;
```

In this example:

- We're directly mutating the `count` variable when the "Increment" button is clicked.
- We're also directly mutating the DOM element with the id "count" to update its text content.
- This approach directly manipulates state and DOM elements, bypassing React's state management mechanism.
- Directly mutating state variables and DOM elements like this can lead to inconsistencies, unexpected behavior, and can make the code harder to reason about and maintain.

In summary, thinking in state transitions involves updating React component state using state management functions like `setState` or hooks like `useState`, while avoiding direct mutation of state variables or DOM elements. This approach ensures that your React components remain predictable and maintainable, with state changes properly managed by React's reconciliation mechanism.

</details>

### _Thinking in React_ process

<details>
  <summary> <b>Click to view the answer.</b> </summary>
"_Thinking in React_" is a process that emphasizes understanding and approaching UI development in React.js by breaking it down into several steps:

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/d7093037-d76b-463a-869b-6494b1a982d8)

1. **Start with a Mock**: Begin by visualizing the UI design or sketching it out to understand the components needed and their interactions.

2. **Identify Components**: Break down the UI into reusable components based on their responsibilities and functionalities.

3. **Build a Static Version**: Create a static version of the UI with React components but without any interactivity or state management. This helps establish the component hierarchy and structure.

4. **Identify the Minimal (but complete) Representation of UI State**: Determine the minimal set of state that your app needs to render the UI correctly. This includes identifying the data that should be stored in state and passed down as props.

5. **Define the Data Flow**: Understand how data flows through the components hierarchy and how state is managed. Decide which components should hold state and where it should be passed down via props.

6. **Add Interactivity**: Introduce interactivity by adding event handlers, state management, and data flow mechanisms to make the UI dynamic and responsive.

7. **Test Components Independently**: Test each component in isolation to ensure it behaves as expected and is reusable.

8. **Refactor and Optimize**: Refactor the code, optimize performance, and improve maintainability by removing duplicate code and optimizing rendering.

By following the "Thinking in React" process, developers can effectively design, develop, and maintain React applications, resulting in more scalable, modular, and maintainable codebases.

</details>

### State Management

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- State management in React refers to the management and manipulation of the state data within a React application. _deciding when to create pieces of state, what types of state are necessary, where to place each piece of state, and how data flows through app_

- State represents the current condition or data of a component and can be altered over time in response to user actions, server responses, or other events.

- Proper state management is crucial for building complex and interactive user interfaces while maintaining code organization, performance, and scalability.

**Let's use a simpler analogy:** managing a smart home with different rooms and appliances.\*\*\*\*

1. **Smart Home (React Application)**:

   - Imagine your React application as a smart home system that you control from a central hub.
   - The smart home system oversees the entire house, just like your React application manages all its components.

2. **Rooms and Appliances (Components)**:

   - Each room in your house represents a React component. For example, you might have a living room, kitchen, bedroom, and bathroom.
   - Within each room, you have different appliances such as lights, TVs, thermostats, and speakers. These appliances represent individual components within the React application.

3. **States of Appliances (State)**:

   - The state of an appliance represents its current condition or setting. For example, the state of a light bulb could be either on or off, and the state of a thermostat could be the desired temperature.
   - Just like in React, the state of an appliance (component) determines how it behaves and appears.

4. **Defining State and Passing Props**:

   - Each appliance (component) may have its own state. For example, the light bulb component would have state to track whether it's on or off.
   - State should be defined at the lowest level necessary. For instance, the light bulb component should manage its own state for its on/off status.
   - If information needs to be shared among multiple components (e.g., the current temperature set by the thermostat), it should be lifted up to a common ancestor component and passed down as props.
   - For example, the thermostat component might pass the current temperature setting down to the individual room components.

5. **Creating Subcomponents**:
   - If a room or appliance becomes too complex or contains multiple functionalities, consider breaking it down into smaller subcomponents.
   - For instance, the TV in the living room might have subcomponents for volume control, channel selection, and power.
   - Subcomponents help modularize your application, making it easier to manage and maintain.

- In summary, managing state in a React application can be compared to managing a smart home with different rooms and appliances.

- Each room and appliance represents a component, with its own state determining its behavior.

- State should be defined at the appropriate level and shared as needed using props, and subcomponents can be created to break down complex components into smaller, more manageable parts.

**Some best practices for state management in React:**

1. **Use Local Component State**: For managing state that is local to a specific component and doesn't need to be shared with other components, use React's built-in state management with the `useState` hook or `setState` method in class components.

2. **Avoid Excessive State**: Keep the amount of state within your components minimal and focused. Avoid storing unnecessary data in state that doesn't directly affect the component's rendering or behavior.

3. **Lift State Up**: When multiple components need access to the same state or need to synchronize their state, consider lifting the state up to a common ancestor component. This promotes data sharing and avoids prop drilling.

4. **Use Context API**: React's Context API allows you to share state across multiple components without explicitly passing props through every level of the component tree. It's useful for managing global or application-level state.

5. **Consider State Management Libraries**: For complex state management needs, consider using external state management libraries like Redux, MobX, or Recoil. These libraries provide centralized state management solutions with features like time-travel debugging, middleware support, and more.

6. **Normalize State Shape**: Organize your state data in a normalized shape, especially when dealing with relational or nested data structures. This helps in avoiding redundant data and simplifies state updates.

7. **Immutable Updates**: When updating state, always use immutable techniques to ensure that the original state remains unchanged. This helps prevent bugs related to state mutations and makes it easier to track state changes.

8. **Separation of Concerns**: Maintain a clear separation between UI state (component-level state) and application state (global state). UI state should be managed within individual components, while application state should be managed at a higher level, possibly using state management libraries.

9. **Optimize Rendering**: Minimize unnecessary re-renders by optimizing state updates and using techniques like memoization (with `React.memo` or `useMemo`) and shouldComponentUpdate (in class components) to prevent unnecessary rendering.

10. **Testing**: Write tests to verify the behavior of components and state management logic. Test both the initial rendering and state changes to ensure that components behave as expected under different scenarios.

By following these best practices, you can effectively manage state in your React applications, leading to cleaner, more maintainable code and better user experiences.

</details>

### Lifting state up in React with best practices

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Lifting state up in React is a technique used to manage shared state among multiple components by moving the state to a common ancestor component.

- This allows different child components to access and update the shared state as needed.

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/cff06b00-f748-4199-8abf-596b53ee7bfe)

**Example**:

- Let's say we have a simple counter application with two buttons: one for incrementing the counter and one for decrementing it.

- We want both buttons to interact with the same counter value.

```tsx
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h2>Counter: {count}</h2>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
}

export default Counter;
```

- In this example, the `count` state is managed within the `Counter` component.

- _However, what if we want to use the counter value in another component as well? We can lift the `count` state up to a common ancestor component and pass it down to the `Counter` component as a prop_.

```tsx
import React, { useState } from "react";
import Counter from "./Counter";

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>Counter App</h1>
      <Counter count={count} setCount={setCount} />
      <p>Counter Value: {count}</p>
    </div>
  );
}

export default App;
```

- Now, the `App` component manages the `count` state, and it passes down both the `count` value and the `setCount` function as props to the `Counter` component.

- This way, both the `Counter` component and the `App` component can interact with the same counter value.

Here's how the `Counter` component would look like in TypeScript with JSX (`.tsx`):

```tsx
import React from "react";

interface CounterProps {
  count: number;
  setCount: React.Dispatch<React.SetStateAction<number>>;
}

const Counter: React.FC<CounterProps> = ({ count, setCount }) => {
  const increment = () => {
    setCount(count + 1);
  };

  const decrement = () => {
    setCount(count - 1);
  };

  return (
    <div>
      <h2>Counter: {count}</h2>
      <button onClick={increment}>Increment</button>
      <button onClick={decrement}>Decrement</button>
    </div>
  );
};

export default Counter;
```

- We define a TypeScript interface `CounterProps` to specify the props expected by the `Counter` component. It includes a `count` prop of type `number` and a `setCount` prop of type `React.Dispatch<React.SetStateAction<number>>`. This type is used to represent the function returned by `useState` that can update the `count` state.

- We declare the `Counter` component as a functional component (`React.FC`) that takes `CounterProps` as its props.

- Within the component, we use destructuring to access the `count` and `setCount` props.

- The `increment` and `decrement` functions update the `count` state using the `setCount` function.

**Importance and Best Practices**:

1. **Data Sharing**:

   - Lifting state up enables components to share data and communicate with each other.

   - This is especially useful when multiple components need access to the same data.

2. **Single Source of Truth**:

   - By lifting state up to a common ancestor component, you maintain a single source of truth for the shared state.

   - This helps prevent data inconsistencies and makes your application easier to understand and maintain.

3. **Flexibility**:

   - Lifting state up allows you to easily reorganize and refactor your components without having to rewrite state management logic.

   - It promotes a more flexible and scalable codebase.

4. **Performance**:

   - Lifting state up can also improve performance by reducing unnecessary re-renders of components lower in the component tree.

   - If a state value changes, only the components that depend on that state will re-render, rather than the entire subtree.

In summary, lifting state up is a powerful pattern in React that promotes data sharing, maintainability, flexibility, and performance in your applications. It's important to identify when to lift state up based on your application's requirements and to follow best practices to ensure clean and efficient code.

</details>

### Deriving State

<details>
  <summary> <b>Click to view the answer.</b> </summary>

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/11aa226e-ce4f-45f0-91bd-3f17c8c0040a)

Deriving state in React involves calculating new state values based on existing state or props. It's essential to approach state derivation with care to ensure your components remain efficient, maintainable, and bug-free. Let's discuss some common pitfalls, best practices, and examples:

### Bad Practices:

1. **Direct Mutation of State**:

   - **Bad Code**:

     ```tsx
     const [count, setCount] = useState(0);

     // Increment count by 1 directly
     const handleIncrement = () => {
       count++; // Directly mutating state
       setCount(count);
     };
     ```

   - **Explanation**: Directly mutating state without using the `setCount` function can lead to unexpected behavior, as React may not detect the change and trigger a re-render.

2. **State Derivation Based on Outdated State**:

   - **Bad Code**:

     ```tsx
     const [count, setCount] = useState(0);

     // Increment count by 1 based on outdated state
     const handleIncrement = () => {
       setCount(count + 1); // Based on outdated state
     };
     ```

   - **Explanation**: When deriving new state based on existing state, always use the updater function form of `setState` to ensure you're working with the latest state value.

### Best Practices:

1. **Using Updater Function with useState**:

   - **Good Code**:

     ```tsx
     const [count, setCount] = useState(0);

     // Increment count by 1 using updater function
     const handleIncrement = () => {
       setCount((prevCount) => prevCount + 1);
     };
     ```

   - **Explanation**: Use the updater function provided by `useState` to derive new state based on the previous state. This ensures that you're always working with the latest state value.

2. **Memoization for Complex Derivations**:

   - **Good Code**:

     ```tsx
     const [data, setData] = useState(initialData);

     // Derive filteredData based on data using useMemo
     const filteredData = useMemo(() => {
       return data.filter((item) => item.isActive);
     }, [data]);
     ```

   - **Explanation**: For complex state derivations, consider using `useMemo` hook to memoize the derived value. This prevents unnecessary recalculations and improves performance, especially in components with frequent re-renders.

3. **Separation of Concerns**:

   - **Good Code**:

     ```tsx
     const [inputValue, setInputValue] = useState("");
     const [filteredData, setFilteredData] = useState([]);

     // Update inputValue based on user input
     const handleInputChange = (e: React.ChangeEvent<HTMLInputElement>) => {
       setInputValue(e.target.value);
     };

     // Derive filteredData based on inputValue
     useEffect(() => {
       const filtered = originalData.filter((item) =>
         item.name.includes(inputValue)
       );
       setFilteredData(filtered);
     }, [inputValue]);
     ```

   - **Explanation**: Separate state management concerns and derived state calculations into separate variables and functions. This improves code readability, maintainability, and debugging.

### Conclusion:

- When deriving state in React components, always ensure that you're following best practices to maintain code quality, performance, and reliability.

- Avoid direct mutation of state, use updater functions provided by `useState`, consider memoization for complex state derivations, and separate concerns for better code organization.

- By adhering to these practices, you can create React components that are efficient, robust, and easy to maintain.

</details>

### Children Prop

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- In React, the `children` prop is a special prop that allows components to accept arbitrary JSX elements or components as children.

- _This allows for flexible and reusable component compositions._

- Here's an explanation, example code in TypeScript, and some best practices and use cases for using the `children` prop:

### Explanation:

- **Children Prop**: The `children` prop is a reserved prop in React that represents the content between the opening and closing tags of a component when it's used as a parent component.

- **Type**: The `children` prop can have various types, including JSX elements, React components, strings, numbers, arrays, or even functions.

- **Accessing Children**: Components can access and render the `children` prop just like any other prop.

- **Nested Components**: Components can have nested children, allowing for the creation of complex component hierarchies and layouts.

### Example Code in TypeScript:

```tsx
import React from "react";

interface CardProps {
  title: string;
  // Define children prop of type React.ReactNode
  children: React.ReactNode;
}

const Card: React.FC<CardProps> = ({ title, children }) => {
  return (
    <div className="card">
      <h2>{title}</h2>
      <div className="content">
        {/* Render the children prop */}
        {children}
      </div>
    </div>
  );
};

const App: React.FC = () => {
  return (
    <div className="app">
      {/* Using the Card component with children */}
      <Card title="Example Card">
        <p>This is some content inside the card.</p>
        <button>Click me</button>
      </Card>
    </div>
  );
};

export default App;
```

### Best Practices and Use Cases:

1. **Layout Components**:

   - Components like containers, panels, or wrappers often use the `children` prop to accept and render dynamic content. This allows for flexible layout compositions.

2. **Higher-Order Components (HOCs)**:

   - Higher-order components that enhance or modify their children components often use the `children` prop to wrap or inject additional functionality.

3. **Compound Components**:

   - Components that work together as a group or set (e.g., **tabs, accordions, modals**) often use the `children` prop to define their internal structure and behavior.

4. **Passing Content**:

   - The `children` prop is commonly used to pass content, such as text, buttons, or other components, into a parent component.

5. **Composition**:

   - Leveraging the `children` prop allows for component composition, enabling developers to create reusable building blocks for their UIs.

6. **Conditional Rendering**:

   - Components can conditionally render or manipulate their children based on props or internal state, providing dynamic behavior.

### Best Practices:

- **Type Safety**:

  -In TypeScript, it's a good practice to define the type of the `children` prop using `React.ReactNode` to ensure type safety and avoid unexpected errors.

- **Clarity**:

  - Provide clear documentation or examples of how the `children` prop should be used and what types of content are accepted.

- **Avoid Overuse**:

  - While the `children` prop offers flexibility, _avoid overusing it in favor of more explicit props when possible to maintain component clarity and readability._

- **Encapsulation**:
  - When passing children to components, consider encapsulating them within a dedicated component or element to maintain component encapsulation and separation of concerns.

By following these best practices and leveraging the `children` prop effectively, developers can create more flexible, reusable, and maintainable React components and applications.

</details>

### [Writing Resilient Components](https://overreacted.io/writing-resilient-components/?ref=jonas.io)

### [Things I think about when I write React code (GitHub repository)](https://github.com/mithi/react-philosophies?ref=jonas.io)

### [Things I think about when I write React code (GitHub repository)](https://github.com/mithi/react-philosophies?ref=jonas.io)

### [A Visual Guide to React Rendering - It Always Re-renders ⭐ ](https://alexsidorenko.com/blog/react-render-always-rerenders/?ref=jonas.io)

### [Render Game](https://alexsidorenko.com/render-game/)

### [Fix the slow render before you fix the re-render](https://kentcdodds.com/blog/fix-the-slow-render-before-you-fix-the-re-render)

### [Inside Fiber: in-depth overview of the new reconciliation algorithm in React](https://angularindepth.com/posts/1008/inside-fiber-in-depth-overview-of-the-new-reconciliation-algorithm-in-react)

### [Lin Clark - A Cartoon Intro to Fiber - React Conf 2017](https://www.youtube.com/watch?v=ZCuYPiUIONs)

### [What Is React Fiber? React.js Deep Dive #2](https://www.youtube.com/watch?v=0ympFIwQFJw)

### [So you think you know everything about React refs](https://thoughtspile.github.io/2021/05/17/everything-about-react-refs/)

### [React use](https://github.com/streamich/react-use)

### Component Size matters

<details>
  <summary> <b>Click to view the answer.</b> </summary>

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/404e7579-a606-466f-8035-62104a451619)

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/929e7f0e-a93c-46e7-bb0d-d00867acb04c)

- Be aware that creating a new component creates a new abstraction. Abstractions
  have a cost, because more abstractions require more mental energy to switch back
  and forth between components. So try not to create new components too early
- Name a component according to what it does or what it displays. Don’t be afraid of
  using long component names
- Never declare a new component inside another component!
- Co-locate related components inside the same file. Don’t separate components into
  different files too early
- It’s completely normal that an app has components of many different sizes, including
  very small and huge ones

</details>

### Component Categories

<details>
  <summary> <b>Click to view the answer.</b> </summary>

Here's a brief explanation of each category:

1. **Stateless / Presentational Components**:

   - **Description**:
     These components focus solely on presenting UI elements based on the data they receive via props. They don't manage any state internally.
   - **Use Cases**:
     Displaying static content, rendering UI elements based on props, creating reusable UI components without logic or state management.

2. **Stateful Components**:

   - **Description**:
     Stateful components manage their own state using hooks (`useState`, `useReducer`) or by extending the `React.Component` class. They handle dynamic data, user interactions, and side effects.
   - **Use Cases**:
     Managing and updating dynamic data and UI states, handling user input and interactions, performing data fetching operations and side effects.

3. **Structural Components**:
   - **Description**:
     These components are responsible for organizing the layout and managing the flow of data and state between other components. They often don't have a significant UI presence but focus on structuring the application.
   - **Use Cases**:
     Defining layout structures like headers, footers, or sidebars, providing context providers or higher-order components for data sharing, handling routing and navigation in single-page applications.

</details>

### Prop Drilling and Component composition

<details>
  <summary> <b>Click to view the answer.</b> </summary>

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/7606c3c4-6f9c-4740-a90b-d50ad66425a5)


**Prop drilling:**

```tsx
import { useState } from "react";

const tempMovieData = [
  {
    imdbID: "tt1375666",
    Title: "Inception",
    Year: "2010",
    Poster:
      "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
  },
];

const tempWatchedData = [
  {
    imdbID: "tt1375666",
    Title: "Inception",
    Year: "2010",
    Poster:
      "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
    runtime: 148,
    imdbRating: 8.8,
    userRating: 10,
  },
];

const average = (arr) =>
  arr.reduce((acc, cur, i, arr) => acc + cur / arr.length, 0);

export default function App() {
  const [query, setQuery] = useState("");
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);
  const [isOpen1, setIsOpen1] = useState(true);
  const [isOpen2, setIsOpen2] = useState(true);

  const avgImdbRating = average(watched.map((movie) => movie.imdbRating));
  const avgUserRating = average(watched.map((movie) => movie.userRating));
  const avgRuntime = average(watched.map((movie) => movie.runtime));

  return (
    <>
      <nav className="nav-bar">
        <div className="logo">
          <span role="img">🍿</span>
          <h1>usePopcorn</h1>
        </div>
        <input
          className="search"
          type="text"
          placeholder="Search movies..."
          value={query}
          onChange={(e) => setQuery(e.target.value)}
        />
        <p className="num-results">
          Found <strong>{movies.length}</strong> results
        </p>
      </nav>

      <main className="main">
        <div className="box">
          <button
            className="btn-toggle"
            onClick={() => setIsOpen1((open) => !open)}
          >
            {isOpen1 ? "–" : "+"}
          </button>
          {isOpen1 && (
            <ul className="list">
              {movies?.map((movie) => (
                <li key={movie.imdbID}>
                  <img src={movie.Poster} alt={`${movie.Title} poster`} />
                  <h3>{movie.Title}</h3>
                  <div>
                    <p>
                      <span>🗓</span>
                      <span>{movie.Year}</span>
                    </p>
                  </div>
                </li>
              ))}
            </ul>
          )}
        </div>

        <div className="box">
          <button
            className="btn-toggle"
            onClick={() => setIsOpen2((open) => !open)}
          >
            {isOpen2 ? "–" : "+"}
          </button>
          {isOpen2 && (
            <>
              <div className="summary">
                <h2>Movies you watched</h2>
                <div>
                  <p>
                    <span>#️⃣</span>
                    <span>{watched.length} movies</span>
                  </p>
                  <p>
                    <span>⭐️</span>
                    <span>{avgImdbRating}</span>
                  </p>
                  <p>
                    <span>🌟</span>
                    <span>{avgUserRating}</span>
                  </p>
                  <p>
                    <span>⏳</span>
                    <span>{avgRuntime} min</span>
                  </p>
                </div>
              </div>

              <ul className="list">
                {watched.map((movie) => (
                  <li key={movie.imdbID}>
                    <img src={movie.Poster} alt={`${movie.Title} poster`} />
                    <h3>{movie.Title}</h3>
                    <div>
                      <p>
                        <span>⭐️</span>
                        <span>{movie.imdbRating}</span>
                      </p>
                      <p>
                        <span>🌟</span>
                        <span>{movie.userRating}</span>
                      </p>
                      <p>
                        <span>⏳</span>
                        <span>{movie.runtime} min</span>
                      </p>
                    </div>
                  </li>
                ))}
              </ul>
            </>
          )}
        </div>
      </main>
    </>
  );
}
```

### Component Composition

```tsx
import { useState } from "react";

const tempMovieData = [
  {
    imdbID: "tt1375666",
    Title: "Inception",
    Year: "2010",
    Poster:
      "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
  },
];

const tempWatchedData = [
  {
    imdbID: "tt1375666",
    Title: "Inception",
    Year: "2010",
    Poster:
      "https://m.media-amazon.com/images/M/MV5BMjAxMzY3NjcxNF5BMl5BanBnXkFtZTcwNTI5OTM0Mw@@._V1_SX300.jpg",
    runtime: 148,
    imdbRating: 8.8,
    userRating: 10,
  },
];

const average = (arr) =>
  arr.reduce((acc, cur, i, arr) => acc + cur / arr.length, 0);

export default function App() {
  const [movies, setMovies] = useState(tempMovieData);
  const [watched, setWatched] = useState(tempWatchedData);

  return (
    <>
      <NavBar>
        <Search />
        <NumResults movies={movies} />
      </NavBar>

      <Main>
        <Box>
          <MovieList movies={movies} />
        </Box>

        <Box>
          <WatchedSummary watched={watched} />
          <WatchedMoviesList watched={watched} />
        </Box>
      </Main>
    </>
  );
}

function NavBar({ children }) {
  return (
    <nav className="nav-bar">
      <Logo />
      {children}
    </nav>
  );
}

function Logo() {
  return (
    <div className="logo">
      <span role="img">🍿</span>
      <h1>usePopcorn</h1>
    </div>
  );
}

function Search() {
  const [query, setQuery] = useState("");

  return (
    <input
      className="search"
      type="text"
      placeholder="Search movies..."
      value={query}
      onChange={(e) => setQuery(e.target.value)}
    />
  );
}

function NumResults({ movies }) {
  return (
    <p className="num-results">
      Found <strong>{movies.length}</strong> results
    </p>
  );
}

function Main({ children }) {
  return <main className="main">{children}</main>;
}

function Box({ children }) {
  const [isOpen, setIsOpen] = useState(true);

  return (
    <div className="box">
      <button className="btn-toggle" onClick={() => setIsOpen((open) => !open)}>
        {isOpen ? "–" : "+"}
      </button>

      {isOpen && children}
    </div>
  );
}

function MovieList({ movies }) {
  return (
    <ul className="list">
      {movies?.map((movie) => (
        <Movie movie={movie} key={movie.imdbID} />
      ))}
    </ul>
  );
}

function Movie({ movie }) {
  return (
    <li>
      <img src={movie.Poster} alt={`${movie.Title} poster`} />
      <h3>{movie.Title}</h3>
      <div>
        <p>
          <span>🗓</span>
          <span>{movie.Year}</span>
        </p>
      </div>
    </li>
  );
}

function WatchedSummary({ watched }) {
  const avgImdbRating = average(watched.map((movie) => movie.imdbRating));
  const avgUserRating = average(watched.map((movie) => movie.userRating));
  const avgRuntime = average(watched.map((movie) => movie.runtime));

  return (
    <div className="summary">
      <h2>Movies you watched</h2>
      <div>
        <p>
          <span>#️⃣</span>
          <span>{watched.length} movies</span>
        </p>
        <p>
          <span>⭐️</span>
          <span>{avgImdbRating}</span>
        </p>
        <p>
          <span>🌟</span>
          <span>{avgUserRating}</span>
        </p>
        <p>
          <span>⏳</span>
          <span>{avgRuntime} min</span>
        </p>
      </div>
    </div>
  );
}

function WatchedMoviesList({ watched }) {
  return (
    <ul className="list">
      {watched.map((movie) => (
        <WatchedMovie movie={movie} key={movie.imdbID} />
      ))}
    </ul>
  );
}

function WatchedMovie({ movie }) {
  return (
    <li>
      <img src={movie.Poster} alt={`${movie.Title} poster`} />
      <h3>{movie.Title}</h3>
      <div>
        <p>
          <span>⭐️</span>
          <span>{movie.imdbRating}</span>
        </p>
        <p>
          <span>🌟</span>
          <span>{movie.userRating}</span>
        </p>
        <p>
          <span>⏳</span>
          <span>{movie.runtime} min</span>
        </p>
      </div>
    </li>
  );
}
```

</details>

### Passing elements as prop alternative to `children`

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- In React, instead of using the `children` prop to pass JSX elements as children, you can explicitly define and pass elements as props to achieve more clarity and control over component composition.

- This approach is particularly useful when you want to pass specific elements to a component rather than relying on the `children` prop.

- Here's an explanation, example code in TypeScript (`.tsx`), and some best practices:

### Explanation:

- **Explicit Props**: Instead of relying on the `children` prop, you define explicit props in your component's interface or type definition to accept specific JSX elements.

- **Enhanced Clarity**: This approach provides enhanced clarity and readability, as it clearly indicates which elements are expected to be passed to the component.

- **Improved Type Safety**: By explicitly defining props for elements, you can ensure type safety and catch potential errors at compile time, especially when using TypeScript.

- **Flexibility**: It offers more flexibility and control over component composition, allowing you to pass different elements to achieve specific layouts or functionality.

### Example Code in TypeScript (`.tsx`):

```tsx
import React from "react";

interface CardProps {
  title: string;
  // Define explicit props for header and content
  header: React.ReactElement;
  content: React.ReactElement;
}

const Card: React.FC<CardProps> = ({ title, header, content }) => {
  return (
    <div className="card">
      {/* Render the header element */}
      <div className="header">{header}</div>
      <div className="content">
        {/* Render the content element */}
        {content}
      </div>
    </div>
  );
};

const App: React.FC = () => {
  return (
    <div className="app">
      {/* Pass specific elements as props to the Card component */}
      <Card
        title="Example Card"
        header={<h2>This is the header</h2>}
        content={<p>This is some content inside the card.</p>}
      />
    </div>
  );
};

export default App;
```

### Best Practices:

- **Explicit Props Naming**: Choose descriptive names for props that represent specific elements to enhance readability and maintainability.
- **Type Safety**: Utilize TypeScript or PropTypes to define the types of props for elements, ensuring type safety and catching potential errors early.
- **Encapsulation**: Consider encapsulating elements within dedicated components or variables before passing them as props to maintain component encapsulation and separation of concerns.
- **Component Composition**: Use this approach strategically for component composition, especially when you need to pass different elements to achieve specific layouts or functionality.

By following these best practices and utilizing explicit props for passing elements, you can enhance the clarity, type safety, and flexibility of your React components, leading to more maintainable and readable codebases.

`implicitly vs explicitly`

Here's a short comparison between passing the `children` prop implicitly and defining elements explicitly as props:

1. **Passing `children` Prop Implicitly**:

   - **Pros**:
     - Simplicity: It's straightforward to use and requires minimal setup. You can pass any JSX elements between the component's opening and closing tags without specifying additional props.
     - Conciseness: It reduces the need for defining explicit props, making the component usage more concise.
   - **Cons**:
     - Lack of Clarity: It can make the component usage less clear, as it's not immediately obvious what type of content should be passed as children.
     - Reduced Control: It provides less control over component composition and may lead to ambiguity regarding the structure of the component's content.

2. **Defining Elements Explicitly as Props**:
   - **Pros**:
     - Clarity: It offers enhanced clarity by explicitly defining props for specific elements, making it clear what type of content is expected.
     - Control: It provides more control over component composition, allowing you to specify exactly which elements should be passed as props.
     - Type Safety: It improves type safety, especially when using TypeScript, as you can define the types of props for elements, catching potential errors at compile time.
   - **Cons**:
     - Increased Boilerplate: It requires additional setup to define and pass explicit props, potentially leading to increased boilerplate code.
     - Slightly More Complex: It may be slightly more complex than using the `children` prop implicitly, especially for simple cases where the content structure is straightforward.

**Which One is Better?**:

- The choice between passing the `children` prop implicitly and defining elements explicitly as props depends on factors such as the complexity of the component, the desired level of clarity and control, and personal preference.
- For simple components or cases where flexibility and conciseness are more important, passing the `children` prop implicitly may be suitable.
- For more complex components or cases where clarity, control, and type safety are priorities, defining elements explicitly as props is generally better.

In summary, both approaches have their pros and cons, and the choice between them should be based on the specific requirements and preferences of your project.

</details>

### BTS of React

<details>
  <summary> <b>Click to view the answer.</b> </summary>
![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/20578731-5e45-40e3-a50c-a024f973ba38)

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/9d3203a3-70e6-4cf1-bfa3-3da6a2eb3f34)

</details>
