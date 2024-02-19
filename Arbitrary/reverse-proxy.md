# Reverse Proxy

- A reverse proxy is a server that sits between clients and backend servers, intercepting requests from clients and directing them to the appropriate backend server.
- Unlike a traditional forward proxy, which handles requests on behalf of clients, a reverse proxy manages requests on behalf of servers.

### Key functions of a reverse proxy include:

1. **Load balancing:** Distributing incoming client requests across multiple backend servers to improve performance and ensure high availability.
2. **SSL termination:** Decrypting encrypted HTTPS traffic from clients before forwarding it to backend servers, which reduces the computational load on backend servers.
3. **Caching:** Storing copies of frequently accessed resources locally to reduce latency and improve responsiveness.
4. **Security:** Acting as a shield between clients and backend servers, hiding server details and protecting against direct attacks.
5. **Content optimization:** Compressing, modifying, or otherwise optimizing content before delivering it to clients to enhance performance and reduce bandwidth usage.

Overall, reverse proxies play a crucial role in optimizing and securing web applications by efficiently managing traffic between clients and servers.

### [Reverse Proxy with rewrites - Vercel](https://vercel.com/guides/vercel-reverse-proxy-rewrites-external#reverse-proxying-with-rewrites)
