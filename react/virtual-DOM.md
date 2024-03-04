# Virtual DOM

The Virtual DOM in React is a lightweight copy of the real DOM (Document Object Model) that React keeps in memory. It's like a blueprint of your web page.

**Here's a simple explanation:**

1. **Real DOM**: Imagine your web page as a house built with Lego bricks. Every time you make a change, like adding a new brick or moving one, the entire house needs to be rebuilt.

2. **Virtual DOM**: Now, imagine you have a sketch of your house on paper. Instead of rebuilding the entire house every time you make a change, you make changes on the sketch first. Once you're happy with the changes, you compare the sketch with the actual house, and only the things that are different get updated.

- In React, the Virtual DOM works similarly to the sketch.
- When you make changes to your React components, React updates the Virtual DOM first, not the actual DOM.
- Then, it compares the Virtual DOM with the real DOM and only updates the parts of the page that have changed.
- This makes updating the UI faster and more efficient because React only touches what needs to be updated, like adding or removing Lego bricks from your house without rebuilding the entire structure from scratch.

### Reconcilication

- Reconciliation in React is the process of comparing the Virtual DOM (representing the current state of your UI) with the previous Virtual DOM (representing the previous state of your UI) and _determining the minimal set of changes needed to update the actual DOM_ (Document Object Model) to reflect the new state.

- This process ensures that React efficiently updates only the parts of the UI that have changed, rather than re-rendering the entire UI from scratch.

## Detail Explanation:

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/a82ee6f5-bd3c-4e53-8521-0bc935ca0c8f)


1. Render trigger

   - Initial render
   - State change in one or more component instances

**How are renders triggered?**

- The render process is triggered for the entire application.

  - This doesn't mean entire DOM is updated.
  - In react rendering is only about calling the component functions and figuring out how much DOM should be updated.

- In practice, it looks like React only renders the component where the state update happens, but that's not how it works behind the scene.

- Renders are not trigger immediately, but scheduled for when the JS engine has some free time. There's also batching of multiple setState calls in event handler.

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/ee003f6e-7101-478a-a293-216dc2ca01ab)


**Rendering Phase:**

2. Rendering:

   - React calls the component functions and figure out how much DOM should be updated

   > In react, rendering is NOT updating the DOM or displaying elements on the screen. _Rendering only happens internally inside React, it **doesnot produce visual change** ._
![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/74f15a38-a984-4b2a-8a8f-c16dae8c2fc4)

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/823eda87-fff7-40ce-be87-c23d5751a149)

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/c129fe68-2107-4800-a4b0-e6e4c6229bf9)

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/94239ca6-488b-45d7-a17f-68796d47dfd2)


3. Commit:

   - React actually writes to the DOM, updating, inserting, and deleting elements.

4. Browser Paint:
   - Here is exactly where the visual change takes place
