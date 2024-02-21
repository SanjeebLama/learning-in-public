# Event Loop

> JS is single threaded non blocking asynchronous concurrent language

has

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
