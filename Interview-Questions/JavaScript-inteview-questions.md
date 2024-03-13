### Q1. What is JavaScript?

<details>
  <summary> <b>Click to view the answer.</b> </summary>
        
- JavaScript is a high-level, interpreted programming language primarily used for creating interactive and dynamic content on webpages.
- It was originally developed by Netscape as a client-side scripting language but has since evolved into a versatile language that can be used for both client-side and server-side development.
    
    **Key features of JavaScript include:**
    
    1. **Dynamic Typing**: Variables in JavaScript can hold values of any data type without explicit declaration.
    2. **Prototype-based Object-Oriented Programming**: JavaScript uses prototypes instead of classes for inheritance.
    3. **Functions as First-Class Citizens**: Functions can be assigned to variables, passed as arguments, and returned from other functions.
    4. **Event-Driven Programming**: JavaScript allows developers to define actions that occur in response to user interactions or other events.
    5. **Cross-platform Compatibility**: JavaScript is supported by all modern web browsers and can also be used on the server-side (e.g., with Node.js).

</details>

### Q2. What are datatypes in JavaScript?

<details>
  <summary> <b>Click to view the answer.</b> </summary>
        
In JavaScript, there are primitive data types and object data type.

1. **Primitive Data Types**: These include strings, numbers, boolean, undefined, null, and symbols (introduced in ES6). They hold single values and are immutable (cannot change).
2. **Object Data Type**: Objects are collections of key-value pairs and are used to store complex data structures. Examples include arrays, functions, and custom objects.

</details>

### Q3. Prototype Inheritance

<details>
  <summary> <b>Click to view the answer.</b> </summary>
        
Prototype inheritance in JavaScript _allows objects to inherit properties and methods from other objects_ through their prototype chains.

1.**Prototype Object:**

- Every object in JavaScript has a special property called prototype.
- This property refers to another object. When you create a new object, it automatically inherits properties and methods from its prototype.

2. **Constructor Functions:**

- You can create objects with a shared prototype using constructor functions.
- Constructor functions are functions used to create objects with a specific structure and behavior.

3. **prototype Property:**

- Constructor functions have a prototype property that is automatically assigned to any objects created using that constructor function.
- This prototype property becomes the prototype of the objects created by that constructor function.

4. **new Operator:**

- When you use the `new` operator with a constructor function, it creates a new object and sets its prototype to the constructor function's prototype property.

```js
// Constructor function
function Animal(name) {
  this.name = name;
}

// Adding a method to the prototype of Animal
Animal.prototype.sound = function () {
  return "Making a sound";
};

// Creating an instance of Animal
var dog = new Animal("Dog");

// Accessing properties and methods of the instance
console.log(dog.name); // Output: "Dog"
console.log(dog.sound()); // Output: "Making a sound"
```

`dog --> Animal.prototype --> Object.prototype`

</details>

### Q4. Call, Apply and Bind

<details>
  <summary> <b>Click to view the answer.</b> </summary>
        
In JavaScript, `call`, `apply`, and `bind` are methods that allow you to invoke functions with a specific context (`this` value) and arguments. Here's a brief explanation of each:

1. **`call`**:

   - The `call` method is used to invoke a function with a specified `this` value and individual arguments provided as separate parameters.
   - Syntax: `function.call(thisArg, arg1, arg2, ...)`
   - Example:

     ```javascript
     function greet() {
       return "Hello, " + this.name;
     }

     var person = { name: "Alice" };
     console.log(greet.call(person)); // Output: "Hello, Alice"
     ```

2. **`apply`**:

   - The `apply` method is similar to `call`, but it accepts arguments as an array.
   - Syntax: `function.apply(thisArg, [arg1, arg2, ...])`
   - Example:

     ```javascript
     function greet(greeting) {
       return greeting + ", " + this.name;
     }

     var person = { name: "Bob" };
     console.log(greet.apply(person, ["Hey"])); // Output: "Hey, Bob"
     ```

3. **`bind`**:

   - The `bind` method is used to create a new function with a specified `this` value, and optionally, pre-filled arguments.
   - Unlike `call` and `apply`, `bind` does not immediately execute the function. Instead, it returns a new function with the specified context and arguments bound to it.
   - Syntax: `function.bind(thisArg[, arg1[, arg2[, ...]]])`
   - Example:

     ```javascript
     function greet() {
       return "Hello, " + this.name;
     }

     var person = { name: "Charlie" };
     var greetPerson = greet.bind(person);
     console.log(greetPerson()); // Output: "Hello, Charlie"
     ```

In summary:

- `call` and `apply` are used for immediate invocation of a function with a specified context and arguments.
- `bind` is used to create a new function with a specified context and optionally pre-filled arguments, without immediately invoking it.

#### More Info:

Real-world scenario where `call`, `apply`, and `bind` can be useful:

**Use Case: Math Utility Functions**

Suppose you have a set of utility functions for performing mathematical operations, and you want to apply these functions to different objects representing numerical data. Here's how you can use `call`, `apply`, and `bind` in this scenario:

1. **Using `call`**:

   Suppose you have a `multiply` utility function, and you want to apply it to different objects:

   ```javascript
   function multiply(factor) {
     return this.value * factor;
   }

   var obj1 = { value: 5 };
   var obj2 = { value: 10 };

   // Using call to apply multiply function to obj1 and obj2
   console.log(multiply.call(obj1, 2)); // Output: 10
   console.log(multiply.call(obj2, 3)); // Output: 30
   ```

2. **Using `apply`**:

   Now let's say you have a `sum` utility function that accepts multiple arguments, and you want to apply it to different objects:

   ```javascript
   function sum() {
     return this.values.reduce((total, current) => total + current, 0);
   }

   var obj1 = { values: [1, 2, 3] };
   var obj2 = { values: [4, 5, 6] };

   // Using apply to apply sum function to obj1 and obj2
   console.log(sum.apply(obj1)); // Output: 6
   console.log(sum.apply(obj2)); // Output: 15
   ```

3. **Using `bind`**:

   Suppose you want to create a reusable function that multiplies a value by a certain factor. You can use `bind` to create a new function with a preset factor:

   ```javascript
   function multiply(factor) {
     return this.value * factor;
   }

   var obj1 = { value: 5 };
   var obj2 = { value: 10 };

   // Using bind to create reusable functions
   var multiplyBy2 = multiply.bind(obj1, 2);
   var multiplyBy3 = multiply.bind(obj2, 3);

   console.log(multiplyBy2()); // Output: 10
   console.log(multiplyBy3()); // Output: 30
   ```

In this real-world scenario, `call`, `apply`, and `bind` help in applying utility functions to different objects with specific contexts or arguments, making the code more flexible and reusable.

</details>

### Q5. JSON (JavaScript Object Notation)

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- JSON is a lightweight data interchange format because it offers a simple and efficient way to represent and exchange structured data between different systems or applications.
- JSON is a way of representing data in a structured format.
- It consists of **key-value pairs**, where _keys are strings_ and _values can be strings, numbers, arrays, objects, boolean values, or null_.

```json
{
  "name": "John",
  "age": 30,
  "isStudent": false,
  "favoriteFruits": ["apple", "banana", "orange"],
  "address": {
    "city": "New York",
    "zipcode": "10001"
  },
  "spouse": null
}
```

### Common operations with JSON involve _creating, parsing, accessing, modifying, and serializing_ JSON data.

Here's a brief overview of each operation:

1. **Creating JSON**:

- You can create JSON data manually by defining key-value pairs, arrays, and objects in JavaScript or any other programming language that supports JSON syntax. For example:

  ```javascript
  var person = {
    name: "John",
    age: 30,
    city: "New York",
  };
  ```

2. **Parsing JSON**:

- Parsing JSON involves converting a _JSON string into a JavaScript object_.
- This is useful when you receive JSON data from an external source like a web API and need to work with it in your code.
- In JavaScript, you can use `JSON.parse()` function for parsing:

  ```javascript
  var jsonString = '{"name":"John","age":30,"city":"New York"}';
  var person = JSON.parse(jsonString);
  ```

3. **Accessing JSON Data**:

- Once you have a JavaScript object representing JSON data, you can access its properties using dot notation or bracket notation:

  ```javascript
  console.log(person.name); // Output: "John"
  console.log(person["age"]); // Output: 30
  ```

4. **Modifying JSON Data**:

- You can modify JSON data by updating its properties, adding new properties, or removing existing ones:

  ```javascript
  person.age = 31;
  person.city = "Los Angeles";
  person.country = "USA";
  delete person.city;
  ```

5. **Serializing JSON**:

- Serializing JSON involves _converting a JavaScript object into a JSON string_.
- This is useful when you need to send JSON data to an external server or save it to a file.
- In JavaScript, you can use `JSON.stringify()` function for serialization:

  ```javascript
  var jsonString = JSON.stringify(person);
  ```

These are some of the common operations you may perform when working with JSON data in your applications. JSON provides a simple and versatile way to represent and exchange structured data in various programming scenarios.

</details>

### Q6. Object and Maps

<details>
  <summary> <b>Click to view the answer.</b> </summary>

Here's a comparison of Objects and Maps presented in a table format:

| Feature     | Objects                                                            | Maps                                                                                   |
| ----------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| Key Types   | Strings or Symbols                                                 | Any data type (including objects, functions, primitives)                               |
| Order       | Not guaranteed                                                     | Guaranteed (based on insertion order)                                                  |
| Iteration   | `for...in`, `Object.keys()`, `Object.values()`, `Object.entries()` | `Map.prototype.keys()`, `Map.prototype.values()`, `Map.prototype.entries()`            |
| Size        | No direct method, `Object.keys(obj).length`                        | `size` property                                                                        |
| Performance | General-purpose, optimized for basic use cases                     | Optimized for frequent additions/removals, especially with non-string keys             |
| Use Cases   | Structured data, associative arrays, general-purpose use           | Keys of different types, order-sensitive operations, associating metadata with objects |

This table provides a concise comparison of key features and characteristics of Objects and Maps in JavaScript.

</details>

### Q7. `==` vs `===`

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- `==` performs loose equality comparison with type conversion, while `===` performs strict equality comparison without type conversion.
- It's generally recommended to use === for most comparisons to avoid unexpected behavior caused by type coercion.

```js
0 == false   // true
0 === false  // false
1 == "1"     // true
1 === "1"    // false
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
NaN == NaN or NaN === NaN // false
[]==[] or []===[] //false, refer different objects in memory
{}=={} or {}==={} //false, refer different objects in memory
```

</details>

### Q8. Arrow Functions (Lambda Expressions) vs Normal JavaScript Functions

<details>
  <summary> <b>Click to view the answer.</b> </summary>

Here's a comparison of lambda expressions (arrow functions) and normal JavaScript functions presented in a table format:

| Feature              | Arrow Functions (Lambda Expressions)                                                                                  | Normal JavaScript Functions                                                                                                                |
| -------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Syntax               | Arrow function syntax `(parameters) => expression` or `(parameters) => { statements }`.                               | Function declaration syntax `function functionName(parameters) { statements }`.                                                            |
| `this` Binding       | Lexical `this` binding: `this` retains the value from the surrounding code where the arrow function is defined.       | Dynamic `this` binding: `this` value is determined by the function's execution context and can change based on how the function is called. |
| `arguments` Object   | Does not have its own `arguments` object. It inherits the `arguments` object from its surrounding non-arrow function. | Has its own `arguments` object, which is an array-like object containing all arguments passed to the function.                             |
| Context              | Cannot be used as constructors and cannot be invoked with `new`.                                                      | Can be used as constructors and invoked with `new` to create new objects.                                                                  |
| Implicit Return      | If the arrow function has a single expression, it's implicitly returned without needing the `return` keyword.         | Requires the `return` keyword to explicitly return a value.                                                                                |
| `prototype` Property | Does not have its own `prototype` property.                                                                           | Has its own `prototype` property, which can be used for inheritance and adding methods.                                                    |
| Binding `this`       | Does not bind its own `this` value, but inherits `this` from the surrounding lexical context.                         | Binds its own `this` value, which can be influenced by how the function is called (e.g., with `bind`, `call`, or `apply`).                 |
| Use Cases            | Often used for concise, inline functions, especially in functional programming paradigms.                             | Used for regular functions with more complex logic, object methods, and constructor functions.                                             |

In summary, arrow functions (lambda expressions) are a more concise and flexible way of writing functions in JavaScript, especially for short, simple functions where the surrounding `this` context is known and `arguments` object is not needed. However, traditional JavaScript functions are still widely used and necessary for more complex scenarios, object-oriented programming, and when a separate `this` context is required.

</details>

### Q9. First Class Function

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- In JavaScript, functions are considered first-class citizens, which means _they can be treated like any other data type._
- Here are the characteristics of first-class functions in JavaScript:

1. **Assigning to Variables**: You can assign functions to variables, just like any other value.

   ```javascript
   const myFunction = function () {
     console.log("Hello, world!");
   };
   ```

2. **Passing as Arguments**: Functions can be passed as arguments to other functions.

   ```javascript
   function greet(name, callback) {
     return callback(name);
   }

   greet("Alice", function (name) {
     console.log("Hello, " + name);
   });
   ```

3. **Returning from Functions**: Functions can be returned from other functions.

   ```javascript
   function createGreeter() {
     return function (name) {
       console.log("Hello, " + name);
     };
   }

   const greeter = createGreeter();
   greeter("Bob");
   ```

4. **Assigning as Properties**: Functions can be assigned as properties of objects.

   ```javascript
   const myObject = {
     greet: function () {
       console.log("Hello, world!");
     },
   };

   myObject.greet();
   ```

5. **Storing in Data Structures**: Functions can be stored in arrays, objects, or other data structures.

   ```javascript
   const functionArray = [
     function () {
       console.log("Function 1");
     },
     function () {
       console.log("Function 2");
     },
   ];

   functionArray[0]();
   ```

- The concept of first-class functions in JavaScript allows for powerful and flexible programming techniques, such as higher-order functions, callbacks, and functional programming patterns.
- It enables functions to be used as data, facilitating more expressive and concise code.

</details>

### Q10. All _first-order functions_ are first-class citizens, but not all first-class functions are first-order functions.

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Because A first-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

`const firstOrder = () => console.log("I am a first order function!");`

</details>

### Q11. Higher Order Function

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- A higher-order function is a function that accepts another function as an argument or returns a function as a return value or both.

```js
const firstOrderFunc = () => console.log("Hello, I am a First order function");
const higherOrder = (ReturnFirstOrderFunc) => ReturnFirstOrderFunc();
higherOrder(firstOrderFunc);
```

</details>

### Q12. TDZ Temporary Dead Zone

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Temporal Dead Zone (TDZ) is a specific period in the execution of code where variables declared with `let` and `const` exist but cannot be accessed or assigned a value.
- During this temporal dead zone, trying to access the variable results in a **ReferenceError**.

- Unlike variables declared with `var`, which are hoisted to the top of their scope and initialized with a value of undefined, variables declared with `let` and `const` are not initialized until the line of code where they are declared is reached during the program's execution.
- However, they are still hoisted to the top of their scope, but remain in an uninitialized state until their declaration is encountered.

```js
// ReferenceError: cannot access x before initialization
console.log(x); // TDZ for x starts here

let x = 10; // TDZ for x ends here

// ReferenceError: cannot access y before initialization
function myFunction() {
  console.log(y); // TDZ for y starts here
  const y = 20; // TDZ for y ends here
}

myFunction();
```

**Importance of TDZ:**

- **Prevents bugs:** Catches potential errors caused by using uninitialized variables.
- **Enhances code clarity:** Makes code more readable and predictable by ensuring variables are declared before use.
- **Safeguards modern JavaScript:** Enforces block-level scoping behavior, essential for features like arrow functions and template literals.

</details>

### Q13. IIFE (Immediately Invoked Function Expression)

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- It's a JavaScript design pattern where a **function is defined and immediately invoked within the same expression**.
- This pattern is commonly used to create a new lexical scope and encapsulate variables to avoid polluting the global namespace.

```js
(function () {
  // Code here runs immediately when defined
  console.log("Hello from the IIFE!");
})();
```

</details>

### Q14. Encode and Decode URL

<details>
  <summary> <b>Click to view the answer.</b> </summary>

In JavaScript, you can encode and decode URLs using the following built-in functions:

1. **encodeURIComponent**:

   - This function encodes a Uniform Resource Identifier (URI) component by replacing certain characters with their UTF-8 encoding equivalents. It encodes all characters except the following: `A-Z`, `a-z`, `0-9`, `-`, `_`, `.`, and `~`.
   - It's typically used to encode query parameters or parts of a URL that are passed as data in a URL.
   - Example:

     ```javascript
     const originalURL =
       "https://www.example.com/search?q=JavaScript&category=Programming";
     const encodedURL = encodeURIComponent(originalURL);
     console.log(encodedURL);
     ```

2. **encodeURI**:

   - This function encodes a Uniform Resource Identifier (URI) by replacing certain characters with their UTF-8 encoding equivalents. However, it does not encode characters that have special meaning in the context of a URL (such as `:`, `/`, `?`, `&`, `=`, `#`, etc.).
   - It's typically used to encode entire URLs or URI components that are already part of a complete URL.
   - Example:

     ```javascript
     const originalURL =
       "https://www.example.com/search?q=JavaScript&category=Programming";
     const encodedURL = encodeURI(originalURL);
     console.log(encodedURL);
     ```

3. **decodeURIComponent**:

   - This function decodes a Uniform Resource Identifier (URI) component that has been encoded using `encodeURIComponent`.
   - It's used to decode URI components back to their original form.
   - Example:

     ```javascript
     const encodedQuery = "JavaScript%20%26%20Node.js";
     const decodedQuery = decodeURIComponent(encodedQuery);
     console.log(decodedQuery);
     ```

4. **decodeURI**:

   - This function decodes a Uniform Resource Identifier (URI) that has been encoded using `encodeURI`.
   - It's used to decode entire URIs back to their original form.
   - Example:

     ```javascript
     const encodedURL =
       "https://www.example.com/search?q=JavaScript&category=Programming";
     const decodedURL = decodeURI(encodedURL);
     console.log(decodedURL);
     ```

Here's a comparison of `encodeURIComponent`, `encodeURI`, `decodeURIComponent`, and `decodeURI` in a table format:

| Function             | Purpose                                                                  | Encoding Behavior                                                                                                | Decoding Behavior                                                        |
| -------------------- | ------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| `encodeURIComponent` | Encodes a URI component (e.g., query parameters)                         | Encodes all characters except: `A-Z`, `a-z`, `0-9`, `-`, `_`, `.`, and `~`                                       | Decodes a URI component that has been encoded using `encodeURIComponent` |
| `encodeURI`          | Encodes a complete URI                                                   | Encodes characters that have special meaning in a URL (e.g., `:`, `/`, `?`, `&`, `=`, `#`, etc.) are not encoded | Decodes a URI that has been encoded using `encodeURI`                    |
| `decodeURIComponent` | Decodes a URI component that has been encoded using `encodeURIComponent` | N/A                                                                                                              | Decodes a URI component back to its original form                        |
| `decodeURI`          | Decodes a URI that has been encoded using `encodeURI`                    | N/A                                                                                                              | Decodes a URI back to its original form                                  |

</details>

### Q15. Modules

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Modules in JavaScript are fundamental building blocks that allow you to break down your code into smaller, self-contained units. - This promotes code organization, reusability, and maintainability.

```js
// math.js
export function add(a, b) {
  return a + b;
}

// main.js
import { add } from "./math.js";

console.log(add(2, 3)); // Output: 5
```

</details>

### Q16. Service Workers in JavaScript: Enhancing Web App Performance and Reliability

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Service workers are powerful JavaScript scripts that run in the background of your web application, independent of the main page thread (operate on a separate thread, ensuring smooth perfromance for you main page).
- They have access to powerful APIs like Cache API and Fetch API for managing resources and network requests.
- Registration: They need to be registered with the browser for your chosen URL scope.
- Lifecycle: They go through various stages like install, activate, and fetch, allowing different tasks at each stage.
- They act as intermediaries between the browser and the network, offering several key benefits:

**Improved Performance:**

1. **Caching:**

- Service workers can store essential resources like HTML, CSS, JavaScript, and images locally, resulting in faster page loads, especially on slow or unreliable connections.

2. **Background synchronization:**

- They can download updates and data in the background, ensuring users have the latest content even when offline.

3. **Push notifications:**

- You can leverage service workers to send real-time updates and notifications to users, even when the app is not actively open.

**Enhanced Reliability:**

1. **Offline access:**

- With cached resources, service workers can enable basic functionality even when users are offline, providing a better user experience.

2. ** Background updates:**

- Updates can be downloaded and installed silently in the background, ensuring users always have the latest version without manual intervention.

**Use Cases:**

- **Progressive Web Apps (PWAs):** Build highly engaging and performant web apps that feel native-like.
- **Offline capabilities:** Offer basic functionality even when users are offline.
- **Background updates:** Ensure users have the latest content without manual updates.
- **Push notifications:** Keep users informed with real-time updates and alerts.

**Resources:**

- [MDN Web Docs:\*\* https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API
- [Google Workbox:\*\* https://developers.google.com/web/tools/workbox

</details>

### Q17. IndexedDB

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- IndexedDB is a _low-level JavaScript API for storing and retrieving large amounts of structured data in the browser including files/blobs_, providing a way for web applications to store data locally and work offline.
- It's designed to be a robust, scalable, and high-performance storage solution for web applications, allowing developers to build sophisticated offline-capable web applications.
- This API uses indexes to enable high-performance searches of this data.

</details>

### Q18. Web Storage

<details>
  <summary> <b>Click to view the answer.</b> </summary>

Web Storage is a simple key-value storage mechanism available in modern web browsers that allows web applications to store data locally within the user's browser. There are two main types of web storage:

1. **localStorage**:

   - `localStorage` allows web applications to store key-value pairs persistently across browser sessions.
   - Data stored in `localStorage` remains available even after the browser is closed and reopened.
   - The data stored in `localStorage` is scoped to the origin (protocol, domain, and port) of the web page, meaning that data is shared among all pages from the same origin.
   - The data in `localStorage` is stored as strings, so any non-string values need to be converted to strings before storage and parsed back into their original types upon retrieval.

2. **sessionStorage**:
   - `sessionStorage` is similar to `localStorage`, but the data stored in `sessionStorage` is available only for the duration of the browser session.
   - Data stored in `sessionStorage` is scoped to the origin (protocol, domain, and port) of the web page and is not shared between browser tabs or windows.
   - Like `localStorage`, the data in `sessionStorage` is stored as strings.

**Here's a basic example of using `localStorage`:**

```javascript
// Storing data in localStorage
localStorage.setItem("username", "john_doe");

// Retrieving data from localStorage
const username = localStorage.getItem("username");
console.log(username); // Output: john_doe

// Removing data from localStorage
localStorage.removeItem("username");
```

And here's an example using `sessionStorage`:

```javascript
// Storing data in sessionStorage
sessionStorage.setItem("theme", "dark");

// Retrieving data from sessionStorage
const theme = sessionStorage.getItem("theme");
console.log(theme); // Output: dark

// Removing data from sessionStorage
sessionStorage.removeItem("theme");
```

- Web Storage is commonly used for storing user preferences, session data, authentication tokens, and other small amounts of data needed by web applications.
- It's a convenient and lightweight storage option that's easy to use and well-supported across modern web browsers.
- However, it's important to note that web storage has limitations, such as the amount of data that can be stored (typically limited to a few megabytes per origin) and **its lack of support for complex data structures like objects or arrays (which need to be serialized/deserialized).**

</details>

### Q19. postMessage()

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- The `postMessage()` method is a feature of the HTML5 Web Messaging API that allows communication between different windows or tabs (iframes or pop-up windows) with different origins.
- It enables cross-origin communication in a secure manner by allowing one window to send messages to another window, even if they are from different origins.

**Here's how `postMessage()` works:**

1. **Sending Messages**:

   - To send a message from one window to another, you call the `postMessage()` method on the sending window's `Window` object.
   - The method takes two parameters: the message to send and the target origin (the origin of the receiving window).
   - Example:

     ```javascript
     // Sending a message from parent window to iframe
     const iframe = document.getElementById("myIframe");
     iframe.contentWindow.postMessage(
       "Hello from parent!",
       "https://example.com"
     );
     ```

2. **Receiving Messages**:

   - To receive messages, you need to add an event listener for the `message` event on the receiving window.
   - The event object contains the received message, the origin of the sending window, and other information.
   - Example:

     ```javascript
     // Receiving a message in the iframe
     window.addEventListener("message", function (event) {
       if (event.origin === "https://example.com") {
         console.log("Message received:", event.data);
       }
     });
     ```

3. **Security Considerations**:
   - It's important to validate the origin of received messages to prevent security vulnerabilities, such as cross-site scripting (XSS) attacks.
   - Always specify the target origin when sending messages to ensure they are delivered only to trusted destinations.

`postMessage()` is commonly used for cross-origin communication in various scenarios, such as embedding third-party content (like social media widgets or advertisements), implementing single sign-on (SSO) solutions, or building collaborative web applications.

It's worth noting that the use of `postMessage()` requires cooperation between the sender and receiver, as both parties need to agree on the messaging protocol and handle messages appropriately. Additionally, care should be taken to ensure that sensitive data is not leaked unintentionally through message passing.

</details>

### Q20. Cookie

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- Cookies are small pieces of data stored on the client-side (i.e., the user's browser) by websites.
- They are commonly used to store information about the user's browsing activity, preferences, session state, and other data relevant to the website's functionality.
- _Cookies are sent to the server with every subsequent request made to the same website, allowing the server to retrieve and utilize the stored information._

**Here are some key characteristics and uses of cookies:**

1. **Persistent Storage**: Cookies can be set with an expiration date, allowing them to persist beyond the current browsing session. This enables websites to remember users between sessions and personalize their experience accordingly.

2. **Limited Size**: Cookies have a limited storage capacity, typically restricted to a few kilobytes per cookie and a maximum number of cookies per domain (usually a few dozen).

3. **Security**: Cookies are associated with a specific domain and are only sent to the server that set them. They cannot be accessed by other websites, enhancing security and privacy. However, cookies can be vulnerable to attacks such as cross-site scripting (XSS) and cross-site request forgery (CSRF) if not properly managed.

4. **HTTP-Only and Secure Flags**: Cookies can be configured with the `HttpOnly` flag to prevent client-side scripts from accessing them, and the `Secure` flag to ensure they are only transmitted over HTTPS connections, enhancing security.

5. **First-Party vs. Third-Party Cookies**: First-party cookies are set by the website the user is currently visiting, while third-party cookies are set by external domains (e.g., for tracking or advertising purposes). Many web browsers provide options to block or limit third-party cookies for privacy reasons.

6. **Session Management**: Cookies are commonly used for session management, where a unique session identifier stored in a cookie allows the server to associate subsequent requests with the same user session.

Here's a basic example of setting and accessing a cookie using JavaScript:

```javascript
// Set a cookie
document.cookie =
  "username=john_doe; expires=Sun, 18 Feb 2024 23:59:59 GMT; path=/";

// Access a cookie
const cookies = document.cookie.split("; ");
for (let cookie of cookies) {
  const [name, value] = cookie.split("=");
  console.log(name, value);
}

// Update a cookie
document.cookie =
  "username=new_value; expires=Fri, 31 Dec 2022 23:59:59 GMT; path=/";

// Delete a cookie by setting its expiration date to a past value
document.cookie = "username=; expires=Thu, 01 Jan 1970 00:00:00 GMT; path=/";
```

Overall, cookies are a fundamental mechanism for maintaining state and personalizing user experiences on the web, but they also raise important considerations regarding privacy, security, and compliance with regulations such as the General Data Protection Regulation (GDPR).

</details>

### Q21. Cookie vs Web Storage

<details>
  <summary> <b>Click to view the answer.</b> </summary>

| Feature          | Cookies                                                                                        | Local Storage                                                                                      | Session Storage                                                                                                       |
| ---------------- | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Storage Location | Stored on the client-side, sent with every HTTP request to the same domain                     | Stored on the client-side, persists even after the browser is closed                               | Stored on the client-side, cleared when the browser session ends (i.e., when the browser is closed)                   |
| Capacity         | Limited (typically a few kilobytes per cookie and a maximum number of cookies per domain)      | Larger (usually several megabytes per origin)                                                      | Similar to local storage, larger than cookies                                                                         |
| Accessibility    | Can be accessed by both the client and the server                                              | Can be accessed only by client-side scripts (JavaScript), not sent to the server with each request | Similar to local storage, accessible only by client-side scripts                                                      |
| Expiry           | Can be set with an expiration date or cleared when the browser is closed (session cookies)     | Persists until explicitly cleared or until the user clears browser data                            | Persists until the end of the browser session                                                                         |
| Scope            | Domain-specific; accessible to all pages on the same domain                                    | Origin-specific; accessible to all pages from the same origin                                      | Origin-specific; accessible to all pages from the same origin                                                         |
| Usage            | Typically used for maintaining user sessions, authentication tokens, and small amounts of data | Used for storing larger amounts of data such as user preferences, settings, or cached data         | Similar to local storage, used for storing session-specific data that should be cleared when the browser session ends |

In summary, cookies, local storage, and session storage are all client-side storage mechanisms in web browsers, but they differ in terms of capacity, accessibility, expiry, scope, and usage. The choice between them depends on factors such as the size and persistence of data, accessibility requirements, and security considerations.

</details>

### Q22. Check web storage and web worker browser support

<details>
  <summary> <b>Click to view the answer.</b> </summary>

**Web Storage**

```js
if (typeof Storage !== "undefined") {
  // Code for localStorage/sessionStorage.
} else {
  // Sorry! No Web Storage support..
}
```

**Web Worker**

```js
if (typeof Worker !== "undefined") {
  // code for Web worker support.
} else {
  // Sorry! No Web Worker support..
}
```

</details>

### Q23. Is Javascript single-threaded or multi-threaded

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- JavaScript is primarily single-threaded. In web browsers, JavaScript runs on a single thread known as the "main thread". This means that JavaScript code is executed sequentially, one statement at a time, and can only perform one task at a time.

- However, JavaScript can also work with asynchronous programming patterns such as callbacks, promises, and async/await, which allow non-blocking execution of code. Asynchronous operations, such as fetching data from a server or waiting for user input, are handled by browser APIs, which run concurrently with the main thread. This allows JavaScript to handle I/O operations efficiently without blocking the main thread.

- While JavaScript itself is single-threaded, modern web browsers leverage multi-threading capabilities for tasks such as rendering, networking, and handling user interactions. For example, browsers use separate threads for rendering the UI, executing JavaScript, and handling network requests. This multi-threaded architecture ensures a responsive user experience while still maintaining the single-threaded nature of JavaScript execution.
</details>

### Q24. How does Javascript handle asynchronous operations?

<details>
  <summary> <b>Click to view the answer.</b> </summary>

JavaScript handles asynchronous operations using non-blocking I/O and an event-driven architecture.

- Asynchronous tasks are managed by the **event loop**, which continuously checks the call stack and task queue.
- **Callback functions** are commonly used to handle asynchronous tasks, allowing code to execute once an operation completes.
- **Browser APIs (in web environments)** provide functions for asynchronous tasks like fetching data or setting timers.
- **Promises and async/await** (ES6+) offer alternative approaches for working with asynchronous code, improving readability and maintainability.

</details>

### Q25. How does Javascript know when a Promise is fulfilled and executes the callback?

<details>
  <summary> <b>Click to view the answer.</b> </summary>

JavaScript knows when a Promise is fulfilled and executes the callback through the event loop and microtask queue mechanism. Here's how it works:

1. **Promise Resolution**:

- When a Promise is resolved (either with a value or another Promise), it schedules its `then` and `catch` callbacks to be executed.

2. **Microtask Queue**:

- Promises use microtasks, which are a type of task that has higher priority than regular tasks (macrotasks) such as setTimeout callbacks and DOM events.
- Microtasks are placed in the microtask queue.

3. **Event Loop**:

- The event loop continuously checks the call stack and microtask queue.
- When the call stack is empty, it picks the first microtask from the microtask queue and executes it.

4. **Executing Callbacks**:

- When a Promise is resolved, its `then` callback is queued as a microtask.
- When all synchronous code in the current execution context is completed, the event loop picks up the microtask from the microtask queue and executes the `then` callback.

In summary, JavaScript knows when a Promise is fulfilled and executes the callback by scheduling the callback as a microtask, which is then executed by the event loop when the call stack is empty. This ensures that Promise callbacks are executed in a predictable order and with higher priority than other asynchronous tasks.

</details>

### Q26. Promises vs Observables

<details>
  <summary> <b>Click to view the answer.</b> </summary>
  
Here's a comparison table highlighting the main differences between Promises and Observables:

| Feature         | Promises                                                      | Observables                                                             |
| --------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Lazy Evaluation | Not lazy. Promises start executing immediately upon creation. | Lazy. Observables do not start executing until they are subscribed to.  |
| Multiple Values | Not inherently capable of emitting multiple values.           | Can emit multiple values over time.                                     |
| Cancellation    | Not directly cancellable.                                     | Can be unsubscribed from, effectively cancelling the ongoing operation. |
| Error Handling  | Uses `catch()` for error handling.                            | Uses `error()` callback or `catch()` for error handling.                |
| Asynchronous    | Primarily used for handling asynchronous operations.          | Can handle both synchronous and asynchronous data streams.              |
| Composition     | Chains with `.then()` and `.catch()` methods for composition. | Can be composed using operators like `map`, `filter`, `mergeMap`, etc.  |
| Built-in        | Built into JavaScript since ECMAScript 2015 (ES6).            | Provided by libraries like RxJS, not built into JavaScript natively.    |

In summary, Promises are primarily used for handling asynchronous operations and represent a single value over time, while Observables are more versatile and can handle both synchronous and asynchronous data streams, emitting multiple values over time. Promises are built into JavaScript, whereas Observables require a library like RxJS for implementation.

</details>

### Q27. What is the difference between Promise.all() and Promise.allSettled() in table format?

<details>
  <summary> <b>Click to view the answer.</b> </summary>
  Here's a comparison table highlighting the main differences between `Promise.all()` and `Promise.allSettled()`:

| Feature         | `Promise.all()`                                                                                                                                 | `Promise.allSettled()`                                                                                                                                                      |
| --------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Resolves When   | Resolves when all promises in the array are resolved successfully.                                                                              | Resolves when all promises in the array have settled (either resolved or rejected), regardless of the outcome.                                                              |
| Result          | Returns a promise that resolves with an array of resolved values from each promise.                                                             | Returns a promise that resolves with an array of objects containing the outcome of each promise (whether fulfilled or rejected), along with the respective value or reason. |
| Handling Errors | If any promise in the array is rejected, the entire `Promise.all()` call is rejected immediately with the reason of the first rejected promise. | Does not fail fast. Even if some promises are rejected, `Promise.allSettled()` waits for all promises to settle before resolving.                                           |
| Use Case        | Suitable when you need all promises to succeed and want to work with their results collectively.                                                | Suitable when you want to know the outcome of all promises in the array, regardless of whether they succeed or fail, and handle each promise's result individually.         |

In summary, `Promise.all()` resolves when all promises in the array are successfully resolved and fails fast if any promise is rejected, while `Promise.allSettled()` resolves when all promises in the array have settled, allowing you to handle each promise's outcome individually, regardless of success or failure.

</details>

### Q28. AJAX request

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- AJAX (Asynchronous JavaScript and XML) is a technique used in web development to send and receive data from a server asynchronously **without requiring a full page refresh**.
- It allows web pages to update content dynamically, making them more interactive and responsive to user actions.

- With AJAX, you can make HTTP requests from a web page to a server in the background, fetch data from the server, and update parts of the page with the retrieved data without reloading the entire page.
- This enables the development of web applications that feel more like desktop applications, as they can update content seamlessly without interrupting the user's experience.

- The term "XML" in AJAX is historical and refers to the fact that XML was often used as the data format for communication between the client and server. However, nowadays, JSON (JavaScript Object Notation) is more commonly used due to its simplicity and ease of parsing in JavaScript.

> In summary, AJAX allows web pages to communicate with a server in the background, fetch data, and update content dynamically without requiring a full page reload, resulting in a smoother and more interactive user experience.

</details>

### Slice vs Splice

<details>
  <summary> <b>Click to view the answer.</b> </summary>

| Feature                        | slice                                                                                                                                                                                                                                                                                                          | splice                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Syntax                         | `array.slice(start, end)`                                                                                                                                                                                                                                                                                      | `array.splice(start, deleteCount, item1, item2, ...)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Description                    | Returns a shallow copy of a portion of an array into a new array without modifying the original array.                                                                                                                                                                                                         | Changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.                                                                                                                                                                                                                                                                                                                                                                                                          |
| Modification of Original Array | Does not modify the original array.                                                                                                                                                                                                                                                                            | Modifies the original array.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Parameters                     | - `start`: The beginning index (inclusive) of the portion to extract. If negative, it counts from the end of the array. <br> - `end` (optional): The ending index (exclusive) of the portion to extract. If negative, it counts from the end of the array. If omitted, slice extracts to the end of the array. | - `start`: The index at which to start changing the array. If negative, it indicates an offset from the end of the array. <br> - `deleteCount` (optional): The number of elements to remove. If omitted or larger than the remaining number of elements, deleteCount will remove all elements from start to the end of the array. <br> - `item1`, `item2`, ... (optional): The elements to add to the array, beginning at the start index. If no elements are specified, splice will only remove elements from the array. |
| Return Value                   | A new array containing the extracted elements.                                                                                                                                                                                                                                                                 | An array containing the deleted elements, if any.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Use Cases                      | - Copying parts of an array without altering the original array. <br> - Extracting a subset of an array for manipulation or display.                                                                                                                                                                           | - Removing elements from an array. <br> - Adding elements into an array at a specific position. <br> - Replacing elements within an array.                                                                                                                                                                                                                                                                                                                                                                                |

**Example:**

```javascript
const array = [1, 2, 3, 4, 5];

// Using slice
const slicedArray = array.slice(1, 4); // Returns [2, 3, 4]
console.log(slicedArray); // Output: [2, 3, 4]
console.log(array); // Output: [1, 2, 3, 4, 5] (Original array remains unchanged)

// Using splice
const deletedElements = array.splice(1, 2, 6, 7); // Removes elements [2, 3] and adds elements 6 and 7 at index 1
console.log(deletedElements); // Output: [2, 3] (Deleted elements)
console.log(array); // Output: [1, 6, 7, 4, 5] (Original array modified)
```

</details>

### Shallow Clone vs deep Clone

<details>
  <summary> <b>Click to view the answer.</b> </summary>

1. **Shallow Clone:**

   - A shallow clone creates a new object or array, but it only copies the top-level structure of the original object or array. In other words, it creates a new object with the same properties as the original object, but the properties themselves are not cloned. Similarly, for arrays, a shallow clone creates a new array with the same elements as the original array, but if those elements are objects or arrays, they are not cloned; rather, their references are copied.

   - Shallow clones are quick and easy to perform but may not be sufficient if the original object contains nested objects or arrays that need to be cloned separately.

   **Example:**

   ```javascript
   const originalObject = { a: 1, b: { c: 2 } };

   // Shallow clone using object spread syntax (for objects)
   const shallowCloneObject = { ...originalObject };

   // Shallow clone using slice method (for arrays)
   const originalArray = [1, { a: 2 }, 3];
   const shallowCloneArray = originalArray.slice();

   // Modifying the cloned objects to demonstrate shallow nature
   shallowCloneObject.a = 10;
   shallowCloneObject.b.c = 20; // This also modifies originalObject
   shallowCloneArray[1].a = 100; // This also modifies originalArray

   console.log(originalObject); // { a: 1, b: { c: 20 } }
   console.log(originalArray); // [1, { a: 100 }, 3]
   ```

2. **Deep Clone:**

   - A deep clone creates a new object or array and recursively copies all nested objects and arrays within the original object or array. In other words, it creates a completely independent copy where changes to the clone do not affect the original and vice versa.
   - Deep cloning ensures that all levels of nested objects or arrays are also cloned, making it more suitable for scenarios where you need a fully independent copy of the original data structure.

   **Example:**
   Deep cloning can be done using various libraries such as Lodash, or you can implement a custom deep clone function. Here's an example using Lodash:

   ```javascript
   const _ = require("lodash");

   const originalObject = { a: 1, b: { c: 2 } };

   // Deep clone using Lodash
   const deepCloneObject = _.cloneDeep(originalObject);

   // Modifying the cloned object to demonstrate deep nature
   deepCloneObject.a = 10;
   deepCloneObject.b.c = 20; // This does not modify originalObject

   console.log(originalObject); // { a: 1, b: { c: 2 } }
   console.log(deepCloneObject); // { a: 10, b: { c: 20 } }
   ```

   ```javascript
   function deepClone(obj) {
     // Handle non-object types and null
     if (typeof obj !== "object" || obj === null) {
       return obj;
     }

     // Create an empty object or array to store the cloned data
     const clone = Array.isArray(obj) ? [] : {};

     // Iterate over each key in the original object or array
     for (let key in obj) {
       // Check if the property belongs to the object itself, not inherited
       if (obj.hasOwnProperty(key)) {
         // Recursively clone nested objects or arrays
         clone[key] = deepClone(obj[key]);
       }
     }

     return clone;
   }
   ```

```javascript
// Deep clone using JSON.stringify and JSON.parse
const deepCloneObject = JSON.parse(JSON.stringify(originalObject));

// Modifying the cloned object to demonstrate deep nature
deepCloneObject.a = 10;
deepCloneObject.b.c = 20; // This does not modify originalObject

console.log(originalObject); // { a: 1, b: { c: 2 } }
console.log(deepCloneObject); // { a: 10, b: { c: 20 } }
```

In summary, shallow cloning creates a new object or array with copied top-level properties or elements, while deep cloning creates a new object or array with all nested properties or elements recursively cloned, ensuring complete independence from the original data structure.

</details>

# One liner

### Promises

A promise in JavaScript represents the eventual completion or failure of an asynchronous operation and its resulting value.
