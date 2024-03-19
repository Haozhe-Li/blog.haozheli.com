### 1. REST

- **Definition**: REST stands for Representational State Transfer.
- **Properties**:
  1. **Client/Server**: Clients and servers interact through a defined interface or API.
  2. **Stateless**: Servers do not store per-client data.
  3. **Cache**: Responses indicate how long they can be cached.
  4. **Uniform Interface**: Requests and responses use similar formats.
  5. **Layered System**: Servers can be divided into multiple computers seamlessly.
  
### 2. RESTful Web API

- **Definition**: RESTful Web APIs adhere to the REST architectural style.
- **Properties**:
  - Clients send HTTP requests, and servers reply.
  - HTTP request methods:
    - **GET**: Retrieves data without changing server state.
    - **POST**: Changes existing server state.
    - Sometimes **PUT** (creates new server state) and **DELETE** (removes existing server state) are used, but occasionally handled using **POST**.
  - HTTP request path identifies the resource being accessed.
  - HTTP request body (not used by **GET**) describes specific changes to be implemented.
  - HTTP headers may specify the desired response format but should not alter the request's meaning.
  - Consistent request and response body formats (e.g., JSON or XML).
  - Other formats like application/x-www-form-urlencoded and multipart/form-data are used for specific cases.

This summary encapsulates the core principles and characteristics of REST and RESTful Web APIs as described in the provided text.