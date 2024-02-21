# Event Loop

> JS is single threaded non blocking asynchronous concurrent language

- The event loop is a critical component of JavaScript's runtime environment, particularly in environments like web browsers and Node.js.
- It's responsible for managing asynchronous operations and ensuring that JavaScript remains single-threaded and non-blocking.

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/33b78efb-ba91-45dd-bcc1-111fe9511afc)

**Here's a breakdown of how the event loop works:**

1. **Call Stack**:

- JavaScript is single-threaded, meaning it can only execute one piece of code at a time.
- The call stack keeps track of the currently executing function and its execution context.

2. **Callback Queue**:

- Asynchronous operations, such as setTimeout, AJAX requests, and event listeners, are executed outside the normal flow of execution and placed in the callback queue _once they are completed_.

3. **Event Loop**:

- The event loop continuously checks if the call stack is empty.
- If the stack is empty, it looks into the callback queue for any tasks waiting to be executed.
- If there are tasks in the queue, it moves them to the call stack, allowing them to be executed.

4. **Non-blocking Nature**:

- While waiting for asynchronous tasks to complete, JavaScript doesn't halt the execution of other code.
- This non-blocking behavior is essential for building responsive and efficient applications, especially in web development.

In summary, the event loop ensures that JavaScript remains responsive by handling asynchronous operations in a non-blocking manner, allowing for efficient execution of code.

### Notes:

JS has

- call stack
- an event loop
- a callback queue
- some other apis and some stuffs

**V8 engine has**

- call stack
- and a heap

# blocking - What happens when things are slow??

- Synchronous
  - Line by line
  - If any request takes long to response or the request size is large - it's slow
  - Until that task is complete - you cannot do anything in the browser

**Solution?**

- Asynchronous Callbacks

![image](https://github.com/SanjeebLama/learning-in-public/assets/51410633/3640447a-31ed-4cf3-b9d6-dae1ae5089d7)

**Event loop:**

- Little peace in the whole equation
- It's job is to look at the stack and look at the callback queue
- if the stack is empty, it takes the first thing on the queue and pushes onto the stack

> AJAX request doesn't live in the JS runtime

**Callback function**

- any function that another functions call
- or asynchronous callback

### Resources

- [What the heck is the event loop anyway? | Philip Roberts](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

#### Visualization:

- [Loupe](http://latentflip.com/loupe/?code=JC5vbignYnV0dG9uJywgJ2NsaWNrJywgZnVuY3Rpb24gb25DbGljaygpIHsKICAgIHNldFRpbWVvdXQoZnVuY3Rpb24gdGltZXIoKSB7CiAgICAgICAgY29uc29sZS5sb2coJ1lvdSBjbGlja2VkIHRoZSBidXR0b24hJyk7ICAgIAogICAgfSwgMjAwMCk7Cn0pOwoKY29uc29sZS5sb2coIkhpISIpOwoKc2V0VGltZW91dChmdW5jdGlvbiB0aW1lb3V0KCkgewogICAgY29uc29sZS5sb2coIkNsaWNrIHRoZSBidXR0b24hIik7Cn0sIDUwMDApOwoKY29uc29sZS5sb2coIldlbGNvbWUgdG8gbG91cGUuIik7!!!PGJ1dHRvbj5DbGljayBtZSE8L2J1dHRvbj4%3D)

- [jsv9000](https://www.jsv9000.app/)

# Async - Promises

// TODO: Heyy

#### Questions:

- How does Javascript handle asynchronous operations?
- How does Javascript know when a Promise is fulfilled and executes the callback?
- What is the difference between Promises and Observable?
- What is the difference between Promise.all() and Promise.allSettled()? 10:02
- What are event emitters?
- Can we unsubscribe from an event?
- What optimizations are you familiar with?
  - memoization
  - use of continue | break | go to
  - Web Workers
  - Avoid memory leaks (global vars, etc)
  - Reusablility
- What is the difference between call() and apply()?
- What's the difference between creating an object using const and Object.freeze()?
- What's the difference between Map and WeakMap?
- Difference between "null" and "undefined"?
- Hoisting
- **JSONP vs AJAX?**
- What tools can be used to ensure consistent code style?
  - Husky,Eslint, Prettier
  - Sonar Qube
- Prototyping
- Constructors/Prototypes vs Module Pattern
- Reference vs Value? Is JS pass-by-reference or pass-by-value language?
- How to deep freeze an object?
- Why is "this" operator inconsistent?
- Arrow functions vs "regular" functions?
- Cons of using arrow functions?
- Async/await vs Generators? How can we achieve the same functionality?
- Shadow Clone Deep Clone
