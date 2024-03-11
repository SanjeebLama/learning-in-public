# One liner

### Promises

A promise in JavaScript represents the eventual completion or failure of an asynchronous operation and its resulting value.

### DOM

The Document Object Model (DOM) is a programming interface for web documents that represents the structure of a web page as a tree of nodes, allowing scripts to dynamically access and modify the content, structure, and style of web documents.

### Event Bubbling

Event bubbling is a mechanism in the Document Object Model (DOM) where events triggered on the innermost nested element are propagated upwards through its ancestor elements in the DOM hierarchy, allowing parent elements to also handle the same event.

<details> <summary> Use case </summary>

Simple use case of event bubbling is in form validation. Suppose you have a form with several input fields, and you want to validate each field when it loses focus (blur event). Instead of attaching a blur event listener to each input field individually, you can attach a single blur event listener to the form element itself.

When a user interacts with an input field and then moves to another field or clicks outside of the form, the blur event bubbles up from the input field through its parent elements, eventually reaching the form element. The blur event listener attached to the form can then handle the validation logic for all input fields.

This approach centralizes the validation logic, making it easier to manage and maintain. It also ensures consistent behavior across all input fields within the form.

</details>

### Event Capturing

Event capturing is a phase in the Document Object Model (DOM) event handling process where an event travels from the outermost ancestor element down to the target element. In this phase, event listeners attached to the ancestor elements have the opportunity to intercept the event before it reaches the target element.

<details>
<summary> Example </summary>

Let's consider a simple use case involving event capturing: a nested set of div elements where each div has its own click event listener attached.

```html
<div id="outer" style="border: 1px solid black; padding: 20px;">
  <div id="middle" style="border: 1px solid red; padding: 20px;">
    <div id="inner" style="border: 1px solid blue; padding: 20px;">
      Click me!
    </div>
  </div>
</div>
```

Now, let's attach click event listeners to each div element:

```javascript
document.getElementById("outer").addEventListener(
  "click",
  function (event) {
    console.log("Outer div clicked");
  },
  true
); // Set to true for event capturing

document.getElementById("middle").addEventListener(
  "click",
  function (event) {
    console.log("Middle div clicked");
  },
  true
); // Set to true for event capturing

document.getElementById("inner").addEventListener("click", function (event) {
  console.log("Inner div clicked");
});
```

With event capturing enabled (the third argument set to `true` in `addEventListener()`), the event will start from the outermost ancestor (`outer` div) and propagate down to the target element (`inner` div). This means that the click event listeners attached to the `outer` and `middle` divs will be triggered before the listener attached to the `inner` div, even though the click occurred on the `inner` div.

So, if you click on the "Click me!" text inside the `inner` div, the console will log:

```
Outer div clicked
Middle div clicked
Inner div clicked
```

This demonstrates event capturing, where events propagate from the outermost ancestor down to the target element before entering the bubbling phase.

</details>

### State

State in React is the internal mutable data storage mechanism used by components to manage dynamic content and UI state.

While you can use regular variables in React, state provides a more powerful and efficient way to manage dynamic data and UI state within components, leading to more predictable and maintainable code.

### Guess the outputs:

Q1:

```javascript
async function foo() {
  return "foo";
}

const res = foo();
console.log(res);
```

Q2:

```javascript
async function foo() {
  return "foo";
}

async function print() {
  const res = await foo();

  console.log(res);
}

print();
```

Q3: `[1,2] == [1,2]`

In JavaScript, [] == [] evaluates to false because arrays are reference types, and when you compare two arrays with the == operator, it checks for reference equality, not value equality.

### Fixed position property

The `position: fixed` CSS property positions an element relative to the viewport, meaning it stays fixed in its position even when the page is scrolled.

### How is fixed different from absolute?

`position: fixed` positions an element relative to the viewport and keeps it fixed in place during scrolling, while `position: absolute` positions an element relative to its closest positioned ancestor and scrolls with its containing block.

### Are there any cases when the position fixed will not be relative to the viewport?

In standard usage, the position: fixed property positions an element relative to the viewport, meaning it remains fixed in its position even when the page is scrolled. However, there are cases where the fixed positioning may not behave as expected and may not be strictly relative to the viewport. Here are some scenarios where this could occur:

<details>
<summary> Scenarios </summary>

1. **Containing Block:** If a parent element of the fixed-positioned element has a non-static position (e.g., position: relative, position: absolute, or position: fixed), the fixed-positioned element's position will be relative to its nearest positioned ancestor rather than the viewport.

2. **Transforms:** If the fixed-positioned element or any of its ancestors have a CSS transform applied, the fixed positioning may become relative to the transformed ancestor rather than the viewport. This behavior occurs in some browsers, particularly when using CSS 3D transforms.

3. **Sticky Positioning:** In some cases, when combining position: fixed with position: sticky, the fixed positioning may behave differently, especially if the sticky element's containing block changes while scrolling.

4. **Browser Bugs or Quirks:** Different browsers may interpret the CSS specifications differently, leading to inconsistencies in fixed positioning behavior. Some browser bugs or quirks may cause fixed-positioned elements to behave unexpectedly in certain edge cases.

</details>

### Custom Tag in HTML

In HTML, unknown or custom tags like `<hello>World</hello>` do not produce errors because HTML is designed to be flexible and forgiving. When the browser encounters an unknown tag, it simply treats it as an inline element and renders its content accordingly.

### Inline vs Block level elements

Here's a comparison of inline elements and block-level elements presented in a table format:

| Feature            | Inline Elements                                                                                                                                                   | Block-Level Elements                                                                                                    |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Display Behavior   | Flows within the text content, side by side, without line breaks. Cannot have width or height specified.                                                          | Occupies the full width available and starts on a new line, causing line breaks before and after.                       |
| Examples           | `<span>`, `<a>`, `<strong>`, `<em>`, `<img>`, `<input>`                                                                                                           | `<div>`, `<p>`, `<h1>` - `<h6>`, `<ul>`, `<li>`, `<table>`, `<form>`                                                    |
| Default Width      | Takes up only as much width as necessary to contain its content.                                                                                                  | Expands to fill the entire width of its container by default, unless specified otherwise.                               |
| Default Height     | Takes up only as much height as necessary to contain its content.                                                                                                 | Height is determined by the content within, or can be specified using CSS.                                              |
| Margin and Padding | Left and right margin/padding can be applied, but top and bottom margin/padding have no effect (except for replaced elements like images).                        | All margin and padding values (top, right, bottom, left) can be applied.                                                |
| Common Use Cases   | Styling individual parts of text or inline elements within a block-level container. Useful for text formatting and inline elements within paragraphs or headings. | Structuring and organizing the layout of a web page, such as creating sections, headers, paragraphs, lists, forms, etc. |
| Nesting            | Can be nested within other inline or block-level elements.                                                                                                        | Can be nested within other block-level elements but not within inline elements.                                         |

### What happens when there are two span tags inside a div element. when we give heights and width to span tag will it work? Another question in the same scenerio what if we add display flex to the div element? What changes will it have?

### if else vs ternary operator

The "if...else" statement and the ternary operator (`? :`) are both conditional constructs used in JavaScript to execute different code based on a condition. Here's a comparison between the two:

| Feature      | If...Else Statement                                                                                           | Ternary Operator (`? :`)                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Syntax       | Requires the use of the `if`, `else if`, and `else` keywords.                                                 | Consists of a single expression with a conditional operator `? :`.                                            |
| Readability  | Generally more verbose, especially for complex conditions with multiple branches.                             | Often considered more concise and can lead to more compact code, especially for simple conditions.            |
| Side Effects | Can contain statements or blocks of code within each branch, allowing for multiple statements to be executed. | Must be an expression, meaning each branch must evaluate to a value or expression result.                     |
| Return Value | Does not have a return value, but can execute different blocks of code based on the condition.                | Returns a value based on the condition. Useful for conditional assignment or returning values in expressions. |

<details>

<summary> Side effects </summary>
Certainly! Let's delve deeper into the concepts of "statements" and "expressions," and then we'll discuss how they relate to side effects in the context of conditional constructs.

**Statements**:
In JavaScript, a statement is a piece of code that performs a specific action. Statements are executed sequentially and often have side effects. Examples of statements include variable declarations (`var`, `let`, `const`), loops (`for`, `while`), conditionals (`if`, `else`, `switch`), function declarations, and more. Statements don't necessarily return a value; their primary purpose is to carry out an operation or control flow.

**Expressions**:
An expression, on the other hand, is a piece of code that evaluates to a value. It can be as simple as a single variable or a complex combination of operators and operands that result in a value. Expressions can appear within statements, as part of larger expressions, or even stand alone. Examples of expressions include arithmetic expressions (`2 + 3`), function calls (`Math.sqrt(9)`), logical expressions (`true && false`), and variable assignments (`x = 10`).

**Side Effects**:
A side effect refers to any observable change that occurs as a result of executing a piece of code. In the context of conditional constructs like the "if...else" statement and the ternary operator, the side effects often relate to the actions taken within the branches of these conditionals.

When we say that an "if...else" statement can contain statements or blocks of code within each branch, it means that each branch can execute multiple statements. These statements may have side effects, such as modifying variables, changing the state of the program, or performing I/O operations. For example:

```javascript
if (condition) {
  // Statement 1
  // Statement 2
  // ...
} else {
  // Statement 3
  // Statement 4
  // ...
}
```

In contrast, the ternary operator (`? :`) must be an expression. This means that each branch of the ternary operator must evaluate to a value or an expression result. While you can still have side effects within each branch of the ternary operator, they must ultimately result in a value. For example:

```javascript
const result = condition
  ? // Expression 1
    // Expression 2
    // ...
    valueIfTrue
  : // Expression 3
    // Expression 4
    // ...
    valueIfFalse;
```

In summary, statements perform actions or control flow within your code and may have side effects, while expressions evaluate to values and are used to compute results. Both the "if...else" statement and the ternary operator can accommodate side effects, but the ternary operator requires that these side effects ultimately result in a value or expression.

</details>

### Closure

A closure in JavaScript is a function that retains access to variables from its outer scope even after the outer scope has finished executing.

<details>

<summary>Example </summary>

Here's a simple example of a closure in JavaScript:

```javascript
function outerFunction() {
  let outerVariable = "I am from outer scope";

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

const closure = outerFunction();
closure(); // Output: "I am from outer scope"
```

In this example:

- `outerFunction` defines a variable `outerVariable` and declares an inner function `innerFunction`.
- `innerFunction` has access to `outerVariable` due to closure, even though `outerFunction` has finished executing.
- When `outerFunction` is called and its return value is assigned to `closure`, it returns `innerFunction`.
- Later, when `closure` is invoked, it still has access to `outerVariable` through closure, and it logs the value of `outerVariable` to the console.
</details>

### What's the output?

```javascript
console.log(a); // undefined
console.log(b); // reference Error

var a = (b = 5);
```

```js
x = 4;

console.log(x++); // 4

console.log(x); // 5
```

```js
console.log(1 < 2 < 3); // true
console.log(3 > 2 > 1); // false
```

<details>

<summary>Explanation </summary>
The output of the given code will be:

```
true
false
```

Here's the explanation:

1. `console.log(1 < 2 < 3)`:

   - The comparison `1 < 2` evaluates to `true`, because `1` is indeed less than `2`.
   - Then, `true < 3` is evaluated. JavaScript converts `true` to the number `1`, so this becomes `1 < 3`, which is also `true`.
   - Therefore, the first `console.log()` outputs `true`.

2. `console.log(3 > 2 > 1)`:
   - The comparison `3 > 2` evaluates to `true`, because `3` is indeed greater than `2`.
   - Then, `true > 1` is evaluated. JavaScript converts `true` to the number `1`, so this becomes `1 > 1`, which is `false`.
   - Therefore, the second `console.log()` outputs `false`.

In JavaScript, comparison operators (`<`, `>`, `<=`, `>=`) are left-associative, meaning they are evaluated from left to right. So, `1 < 2 < 3` is essentially `(1 < 2) < 3`, and `3 > 2 > 1` is essentially `(3 > 2) > 1`.

</details>

```js
const foo = () => {
  console.log(this.name); // undefined
};

foo.call({ name: "John" });
```

In JavaScript, arrow functions (() => {}) do not have their own this contex

<details>

<summary> Explanation </summary>

In JavaScript, arrow functions (`() => {}`) do not have their own `this` context. Instead, they inherit the `this` value from the enclosing lexical context (i.e., the context in which they are defined). In your code snippet, the arrow function `foo` is defined in the global scope or some other outer scope where `this` refers to the global object (e.g., `window` in a browser or `global` in Node.js).

When you use the `call()` method to invoke `foo` with a specific `this` context (in this case, `{name: "John"}`), it doesn't affect the value of `this` inside the arrow function `foo`. So, `this.name` inside `foo` still refers to the property `name` of the global object, which is typically `undefined`.

To make `this` refer to the object passed to `call()`, you should use a regular function instead of an arrow function. Here's the corrected code:

```javascript
const foo = function () {
  console.log(this.name);
};

foo.call({ name: "John" }); // Output: "John"
```

In this code, `foo` is a regular function, so it has its own `this` context, which gets set to the object `{ name: "John" }` when `foo` is called with `call()`. As a result, `this.name` inside `foo` correctly refers to the `name` property of the object passed to `call()`, which is `"John"`.

</details>

### Output?

```js
console.log(a); // Outputs: undefined

a = 5;
```

```js
a = 5;
console.log(a); // Outputs: 5
```
