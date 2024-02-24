### Q0. How are REST APIs stateless?

<details>
  <summary> <b>Click to view the answer.</b> </summary>

> Stateful apps store client data on their own servers

- In REST architecture, statelessness means that each client request to the server contains all the information necessary for the server to fulfill the request.
- _The server does not maintain any client state between requests. This means that each request from a client to the server is independent and self-contained, and the server does not rely on any information from previous requests to process the current request._

You can further elaborate by mentioning:

- Each request from a client to the server includes all the required data and authentication information (if needed) in the request headers or body.
- The server processes each request based solely on the information provided in that request, without any reliance on previous interactions with the client.
- _Statelessness simplifies the architecture and makes it more scalable,_ as servers do not need to maintain session state for each client, allowing them to handle a larger number of concurrent requests efficiently.
- Clients can make requests to different servers or server instances in a load-balanced environment without affecting the overall statelessness of the system.

By explaining these points concisely, you demonstrate an understanding of the concept of statelessness in REST APIs and how it contributes to the scalability and simplicity of the architecture.

</details>

### Q1. Explain HTTP methods.

<details>
  <summary> <b>Click to view the answer.</b> </summary>

Certainly! Here's an explanation of HTTP methods in a table format:

| HTTP Method | Description                                                                                     |
| ----------- | ----------------------------------------------------------------------------------------------- |
| GET         | Retrieves data or resources from the server. It should only retrieve data and not modify it.    |
| POST        | Submits data to the server to create a new resource or perform a specific action on the server. |
| PUT         | Updates an existing resource on the server with the provided data.                              |
| DELETE      | Removes a resource from the server.                                                             |
| PATCH       | Partially updates an existing resource on the server with the provided data.                    |
| HEAD        | Retrieves metadata about a resource without retrieving the resource itself.                     |
| OPTIONS     | Requests information about the communication options available for a resource.                  |

These are the commonly used HTTP methods along with their descriptions. Understanding these methods is crucial for building RESTful APIs and interacting with web servers effectively.

</details>

### Q2. What is a URI?

<details>
  <summary> <b>Click to view the answer.</b> </summary>

- URI stands for Uniform Resource Identifier.
- It is a string of characters used to identify a resource on the internet.
- A URI can be used to uniquely identify various resources such as web pages, images, documents, and more.

**A URI typically consists of the following components:**

1. **Scheme**:

- Indicates the protocol used to access the resource (e.g., "http://" for Hypertext Transfer Protocol, "https://" for Hypertext Transfer Protocol Secure, "ftp://" for File Transfer Protocol).

2. **Authority**:

- Specifies the domain name or IP address of the server hosting the resource.

3. **Path**:

- Specifies the location of the resource on the server's file system or within its directory structure.

4. **Query**:

- Contains additional parameters or data used to access or manipulate the resource (e.g., search parameters in a web query).

5. **Fragment**:

- Identifies a specific portion or section of the resource (often used in web pages to link to specific sections of a document).

For example, in the URI "https://www.example.com/products?id=123", the scheme is "https://", the authority is "www.example.com", the path is "/products", and the query parameter is "id=123".

- URIs provide a standardized way to reference and access resources on the internet, enabling interoperability between different systems and applications.

</details>

### Q3. URI, URL and URN

<details>
  <summary> <b>Click to view the answer.</b> </summary>

URI, URL, and URN are all types of Uniform Resource Identifiers (URIs), but they serve slightly different purposes:

![Image](https://pbs.twimg.com/media/FQ4ZpiGaMAA4vD1.jpg)

1. **URI (Uniform Resource Identifier)**:

   - A URI is a string of characters used to identify a resource, which can be a web page, document, image, or any other resource accessible on the internet or within a computer network.
   - URIs provide a standard way to reference and access resources by uniquely identifying them.
   - URIs can be further classified into URLs and URNs.

2. **URL (Uniform Resource Locator)**:

   - A URL is a specific type of URI that specifies the location of a resource on the internet.
   - URLs typically consist of several components, including a scheme (such as "http" or "https"), an authority (such as a domain name or IP address), a path (the location of the resource on the server), and optional query parameters and fragments.
   - URLs are commonly used in web browsers and applications to access and retrieve web resources by providing their specific location.

3. **URN (Uniform Resource Name)**:
   - A URN is another type of URI that is used to uniquely identify resources without necessarily providing their location.
   - URNs are intended to be persistent and globally unique identifiers for resources, regardless of their location or access method.
   - Unlike URLs, which specify the location of a resource, URNs are primarily used for naming resources in a consistent and persistent manner.
   - While URNs have been defined in various specifications, they are less commonly used than URLs in practice.

In summary, URIs are used to uniquely identify resources, while URLs specify the location of resources on the internet, and URNs are used for naming resources in a persistent and globally unique manner. All URLs are URIs, but not all URIs are URLs, and URNs represent a specific subset of URIs focused on resource naming.

![Image](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2F1b143a39-0445-4906-baca-25633217e5c0_1539x1536.jpeg)

#### Resources:

- https://danielmiessler.com/p/difference-between-uri-url/

</details>

### More Resources:

- https://www.youtube.com/watch?v=faMdrSCVDzc
- https://www.youtube.com/watch?v=n2JQFFFEd0M
