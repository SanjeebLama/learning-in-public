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
