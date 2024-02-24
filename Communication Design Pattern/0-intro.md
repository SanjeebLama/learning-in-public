# Communication design patterns:

- Communication design patterns are established templates for organizing and managing communication between different components or systems in software architecture.
- These patterns help developers structure the flow of information, data exchange, and interactions within a distributed or networked application.
- By following these patterns, developers can improve scalability, maintainability, and flexibility in their systems.

### Examples of Communication Design Patterns:

1. **Client-Server**:

- In the client-server pattern, clients request services or resources from a centralized server.
- The server processes these requests and responds to the clients accordingly.
- This pattern is widely used in web applications, where clients (browsers) communicate with servers over HTTP to retrieve data or perform operations.

2. **Publish-Subscribe (Pub/Sub)**:

- In the publish-subscribe pattern, publishers produce messages (events) and send them to a central message broker. Subscribers register interest in specific types of messages and receive them from the broker.
- This pattern decouples producers from consumers and enables asynchronous, event-driven communication. Examples include message queues like RabbitMQ or Apache Kafka.

3. **Remote Procedure Call (RPC)**:

- RPC is a communication pattern where a client calls procedures or functions that execute on a remote server as if they were local.
- This pattern abstracts network communication and enables distributed computing. Examples include gRPC, XML-RPC, and JSON-RPC.

4. **Message Queue**:

- In the message queue pattern, messages are stored in a queue and processed asynchronously by consumers.
- This pattern facilitates loose coupling between components, improves fault tolerance, and supports load balancing. Examples include RabbitMQ, ActiveMQ, and Amazon SQS.

5. **RESTful API**:

- Representational State Transfer (REST) is an architectural style for designing networked applications based on a set of constraints.
- RESTful APIs use standard HTTP methods (GET, POST, PUT, DELETE) to perform operations on resources, making them accessible via uniform resource identifiers (URIs). This pattern is commonly used in web services and APIs.

6. **SOAP (Simple Object Access Protocol)**:

- SOAP is a protocol for exchanging structured information in the implementation of web services.
- It uses XML for message formatting and relies heavily on XML-based schemas for defining message structure and service interfaces.

7. **GraphQL**:

- GraphQL is a query language and runtime for executing queries against a server-side API.
- Unlike REST, which exposes a set of fixed endpoints for different resources, GraphQL allows clients to specify the shape and structure of the data they need in a single request.
- This enables more efficient data fetching and reduces over-fetching or under-fetching of data.

8. **gRPC (gRPC Remote Procedure Calls)**:

- gRPC is a high-performance RPC (Remote Procedure Call) framework developed by Google.
- It uses Protocol Buffers (protobuf) as the interface definition language and HTTP/2 as the transport protocol.
- gRPC enables efficient communication between services in a microservices architecture, with features such as streaming, authentication, and bidirectional communication.

9. **WebSocket**:

- WebSocket is a protocol for providing full-duplex communication channels over a single TCP connection.
- Unlike HTTP, which follows a request-response model, WebSocket enables real-time, bi-directional communication between clients and servers.
- It is commonly used in applications that require low-latency, real-time updates, such as chat applications, online gaming, and live data streaming.

10. **Event-Driven Architecture (EDA)**:

- EDA is an architectural pattern where systems communicate by producing and consuming events.
- Events represent significant state changes or occurrences within a system, and they are typically published to a message broker or event bus. Consumers subscribe to specific types of events and react to them asynchronously.
- EDA is commonly used in distributed systems, event sourcing, and reactive applications.

These are just a few examples of alternative architectural styles for designing networked applications. Each approach has its own strengths, trade-offs, and use cases, and the choice of architecture depends on factors such as performance requirements, scalability, complexity, and developer preferences.

## More info:

1. [Communication Design patterns for backend developemt](https://www.freecodecamp.org/news/communication-design-patterns-for-backend-development/#:~:text=In%20this%20tutorial%2C%20we%20explored,suitable%20for%20various%20use%20cases.)

2. [REST vs GraphQL](https://www.freecodecamp.org/news/rest-vs-graphql-apis/)
