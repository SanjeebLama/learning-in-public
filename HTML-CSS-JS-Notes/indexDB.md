# IndexedDB

- IndexedDB is a _low-level JavaScript API for storing and retrieving large amounts of structured data in the browser_, providing a way for web applications to store data locally and work offline.
- It's designed to be a robust, scalable, and high-performance storage solution for web applications, allowing developers to build sophisticated offline-capable web applications.

### **Key features of IndexedDB include:**

1. **Structured Data Storage**: IndexedDB stores data in a structured manner, similar to a NoSQL database. It supports storing complex data types such as objects, arrays, and binary data.

2. **Asynchronous API**: IndexedDB operations are asynchronous, meaning that they don't block the main thread, which ensures that the user interface remains responsive even when performing database operations.

3. **Indexed Access**: IndexedDB allows you to create indexes on specific properties of stored objects, enabling efficient retrieval of data based on indexed properties.

4. **Transactions and Atomicity**: IndexedDB operations are grouped into transactions, ensuring data integrity and atomicity. Transactions provide a way to perform multiple database operations as a single unit of work, either committing all changes or rolling them back if an error occurs.

5. **Storage Quotas**: IndexedDB has built-in mechanisms for managing storage quotas, allowing browsers to limit the amount of data that web applications can store locally to prevent abuse of system resources.

6. **Browser Support**: IndexedDB is supported by most modern web browsers, including Chrome, Firefox, Edge, Safari, and Opera.

### **Using IndexedDB involves several steps:**

1. **Opening a Database**: You first need to open a connection to the IndexedDB database using the `indexedDB.open()` method.

2. **Creating Object Stores**: Once the database is open, you create object stores to store data. An object store is similar to a table in a relational database and defines the structure of the stored data.

3. **Performing Transactions**: Database operations are performed within transactions. You begin a transaction, perform database operations (such as adding, deleting, or updating data), and then commit or abort the transaction.

4. **Handling Events**: IndexedDB operations are asynchronous and rely on event handlers to handle success or error events.

Here's a basic example of using IndexedDB to store and retrieve data:

```js
// Open a connection to the IndexedDB database
const request = indexedDB.open("myDatabase", 1);

request.onerror = function (event) {
  console.error("Failed to open database:", event.target.error);
};

request.onsuccess = function (event) {
  const db = event.target.result;
  const transaction = db.transaction(["customers"], "readwrite");
  const objectStore = transaction.objectStore("customers");

  // Add data to the object store
  const customer = { id: 1, name: "John Doe", email: "john@example.com" };
  const request = objectStore.add(customer);

  request.onsuccess = function (event) {
    console.log("Data added successfully");
  };

  request.onerror = function (event) {
    console.error("Failed to add data:", event.target.error);
  };
};

request.onupgradeneeded = function (event) {
  const db = event.target.result;

  // Create an object store
  const objectStore = db.createObjectStore("customers", { keyPath: "id" });

  // Create indexes
  objectStore.createIndex("name", "name", { unique: false });
  objectStore.createIndex("email", "email", { unique: true });
};
```

- IndexedDB provides a powerful and flexible way to store and retrieve data in web applications, making it ideal for building offline-capable web applications or applications that require large-scale client-side data storage.
- However, it has a steep learning curve and can be complex to use compared to simpler storage options like Web Storage (localStorage/sessionStorage).
