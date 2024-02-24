# REST API

- A REST API (**Representational State Transfer** Application Programming Interface) is a standardized way for systems to communicate over the internet.
- It allows you to perform operations (such as retrieving data, creating, updating, or deleting resources) on a server using standard HTTP methods like GET, POST, PUT, and DELETE.

### JavaScript Code Example:

```javascript
// Example of using a REST API to fetch data

// Fetch data from a REST API endpoint using GET method
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => {
    // Check if the response is successful (status code 200-299)
    if (!response.ok) {
      throw new Error("Network response was not ok");
    }
    // Parse the JSON response
    return response.json();
  })
  .then((data) => {
    // Handle the fetched data
    console.log("Fetched data:", data);
  })
  .catch((error) => {
    // Handle any errors that occur during the fetch operation
    console.error("Fetch error:", error);
  });
```

## RESTful

- REST (Representational State Transfer) is often referred to as RESTful because it embodies the principles and constraints outlined by its architectural style.
- When a system or service is designed and implemented following these principles, it is considered to be RESTful.

> The term "RESTful" is derived from "REST" and is used to describe systems, services, or APIs that adhere to the REST architectural style.

**A RESTful system exhibits characteristics such as:**

1. **Statelessness**:

- Each request from a client to the server contains all the information necessary to process the request.
- The server does not store any client state between requests.

2. **Client-Server Architecture**:

- The system is composed of clients and servers that interact through a uniform interface.
- Clients are responsible for presenting the user interface, while servers are responsible for storing and managing resources.

3. **Uniform Interface**:

- The system exposes a uniform interface, typically based on standard HTTP methods (GET, POST, PUT, DELETE), for interacting with resources.
- Resources are identified by URIs (Uniform Resource Identifiers), and representations of resources (e.g., JSON or XML) are exchanged between clients and servers.

4. **Cacheability**:

- Responses from the server can be cached by clients to improve performance and reduce the need for redundant requests.

5. **Layered System**:

- The system is composed of multiple layers, with each layer performing a specific function.
- This enables scalability, flexibility, and modifiability of the system architecture.

When a system or service follows these principles, it is considered to be RESTful because it embodies the characteristics and constraints of the REST architectural style. Therefore, the term "RESTful" is commonly used to describe systems, services, or APIs that adhere to these principles.

### Explanation with Analogy

Certainly! Let's use the analogy of a restaurant to explain and remember the principles of RESTful architecture:

1. **Statelessness**:

- Imagine you're dining at a restaurant. Each time you order a dish, you provide all the necessary information (your order) to the waiter.
- The waiter doesn't remember your previous orders; they only focus on serving your current request.
- Similarly, in a RESTful system, each client request contains all the information needed to process the request, and the server doesn't retain any client state between requests.

2. **Client-Server Architecture**:

- Think of the restaurant as having separate areas for customers (clients) and staff (servers).
- Customers (clients) sit at tables and place orders, while staff (servers) prepare and deliver food.
- This separation of concerns allows clients to focus on ordering and consuming, while servers handle the preparation and delivery of resources.

3. **Uniform Interface**:

- In the restaurant, the menu serves as a uniform interface for ordering food.
- It lists the available dishes (resources) and specifies how to order them (using standardized descriptions and prices).
- Similarly, in a RESTful system, clients interact with resources through a uniform interface, typically using standard HTTP methods (GET, POST, PUT, DELETE) and URIs (like menu items) to access and manipulate resources.

4. **Cacheability**:

- Imagine the restaurant provides a menu booklet to each customer.
- Customers can refer to the booklet to see the available dishes without asking the waiter repeatedly. - This caching mechanism saves time and reduces redundant requests to the kitchen.
- Similarly, in a RESTful system, clients can cache responses from the server to improve performance and reduce the need for redundant requests.

5. **Layered System**:

- Picture the restaurant as having multiple layers of staff, each responsible for different tasks such as cooking, serving, and cleaning.
- The tasks are organized hierarchically, with each layer performing a specific function and communicating with adjacent layers as needed.
- This layered approach enables scalability, flexibility, and modifiability of the restaurant's operations, similar to how a layered system architecture benefits a RESTful system.

By using this restaurant analogy, you can visualize and remember the principles of RESTful architecture more easily. Each aspect of dining at the restaurant corresponds to a principle of REST, making it simpler to understand and recall.

## Best Practices:

Here are some REST best practices to follow when designing and implementing RESTful APIs:

1. **Use Nouns for Resource URIs**:

- URIs should represent resources (nouns) rather than actions (verbs).
- Use meaningful and descriptive names for URIs that reflect the entities being manipulated.
- For example, `/users` for user-related operations instead of `/getUsers`.

2. **Use HTTP Methods Correctly**:

- Use HTTP methods (GET, POST, PUT, DELETE) according to their intended semantics:

  - GET: Retrieve resource representations.
  - POST: Create new resources or perform non-idempotent operations.
  - PUT: Update existing resources with a complete representation.
  - DELETE: Remove resources.
  - Use them consistently and appropriately for CRUD operations.

3. **Use Plural Nouns for Collection Resources**:

- Use plural nouns for URIs representing collections of resources.
- For example, `/users` for a collection of users rather than `/user`.

4. **Versioning**:

- Include versioning information in the URI or headers to ensure backward compatibility and smooth transitions between API versions.
- For example, `/v1/users` for version 1 of the users resource.

5. **Use HTTP Status Codes Correctly**:

- Use appropriate HTTP status codes to indicate the result of API operations:

  - 2xx: Success (200 for OK, 201 for Created, etc.).
  - 3xx: Redirection (301 for Moved Permanently, 304 for Not Modified, etc.).
  - 4xx: Client errors (400 for Bad Request, 404 for Not Found, etc.).
  - 5xx: Server errors (500 for Internal Server Error, 503 for Service Unavailable, etc.).
  - Choose the most suitable status code for each scenario to provide clear feedback to clients.

6. **Error Handling**:

- Provide meaningful error messages and use standard error formats (e.g., JSON) for consistency.
- Include error details in the response body and use appropriate HTTP status codes to indicate error conditions.

7. **Use HATEOAS (Hypermedia as the Engine of Application State)**:

- Include hypermedia links in API responses to enable clients to discover and navigate the API dynamically.
- Hypermedia links provide navigation paths to related resources, allowing clients to interact with the API without prior knowledge of URIs.

8. **Use Content Negotiation**:

- Support content negotiation to allow clients to specify their preferred representation format (e.g., JSON, XML) in the request headers.
- Servers should respond with the requested format if available, providing flexibility and interoperability.

9. **Security**:

- Implement appropriate security measures, such as authentication, authorization, and encryption, to protect the API from unauthorized access and ensure data integrity and confidentiality.

10. **Documentation**:

- Provide comprehensive documentation for the API, including resource URIs, supported operations, request and response formats, error handling, and usage examples.
- Clear documentation helps developers understand and use the API effectively.

Following these REST best practices helps ensure consistency, reliability, and usability of RESTful APIs, leading to better developer experience and interoperability with client applications.

## Resources:

1.[What Is REST API? Examples And How To Use It: Crash Course System Design #3](https://www.youtube.com/watch?v=-mN3VyJuCjM)
