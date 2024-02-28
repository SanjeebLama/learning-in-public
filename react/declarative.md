# React is declarative

> React is declarative because it _focuses on describing "what" you want the UI to look like_, rather than explicitly detailing "how" to achieve that look.

- instead of writing code to directly manipulate HTML elements when data changes,
- in React you describe how components should render based on the data they receive.
- React then intelligently figures out the most efficient way to update the UI to match the new data, without you needing to worry about the low-level DOM manipulation details.

This declarative approach makes React code easier to read, write, and maintain, as it abstracts away the implementation details and allows developers to focus on the desired UI outcomes rather than the specific steps to achieve them.

## Imperative Approach and Declarative Approach

Let's compare an imperative approach (traditional JavaScript DOM manipulation) with a declarative approach (React) to updating a simple counter based on a button click.

### Imperative Approach (Traditional JavaScript):

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Imperative Counter</title>
  </head>
  <body>
    <div id="counter">0</div>
    <button id="incrementBtn">Increment</button>

    <script>
      // Get references to DOM elements
      const counterElement = document.getElementById("counter");
      const incrementBtn = document.getElementById("incrementBtn");

      // Initialize counter value
      let count = 0;

      // Update counter when button is clicked
      incrementBtn.addEventListener("click", () => {
        count++;
        counterElement.textContent = count; // Update DOM manually
      });
    </script>
  </body>
</html>
```

- In this imperative approach, we manually manipulate the DOM to update the counter text whenever the button is clicked.
- We directly specify how the DOM should be modified in response to user actions.

### Declarative Approach (React):

- `JXS` is a declarative syntax to describe what components look like and how they work.
- `JXS` is an extension of JavaScript that allows us to embed JavaScript, CSS, and React components into HTML.
- Each `JSX` element is converted to a `React.createElement` function call by **Babel**.

```jsx
import React, { useState } from "react";

function Counter() {
  // Declare state variable using useState hook
  const [count, setCount] = useState(0);

  // Function to update count state
  const incrementCount = () => {
    setCount(count + 1); // Update count state
  };

  return (
    <div>
      <div>{count}</div> {/* Display count from state */}
      <button onClick={incrementCount}>Increment</button> {/* Handle click event */}
    </div>
  );
}

export default Counter;
```

- In the React declarative approach, we declare the desired UI structure and behavior using JSX.
- We define a `count` state variable using the `useState` hook, and we specify how the UI should look based on this state.
- When the button is clicked, we simply update the `count` state using `setCount`, and React automatically re-renders the component with the updated count value.
- We don't directly manipulate the DOM; instead, we describe how the UI should appear based on the current state.
