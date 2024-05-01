# Tutorial 9
Fikri Risyad Indratno</br>
2206031170</br>
Advanced Programming B

---

## Reflection

> What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

- Unary</br>
The client sends a single request to the server and waits for a response. Useful if you want to fetch a single item from a database, authenticate a user, or perform a calculation and obtain the result.
- Server streaming</br>
Allows the server to send a stream of responses to the client. Useful in scenarios where the server needs to push a large amount of data or a continuous stream of updates to the client.
- Bi-directional</br>
The client and server can send multiple messages to each other in a continuous stream. Useful in scenarios where there is a need for ongoing, interactive communication.

> What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?

- Authentication</br>
Utilize mutual transport layer security to authenticate both the client and the server.
- Authorization</br>
Implement access control mechanisms to determine which users or services can access the resources, such as Role-Based Access Control and Attribute-Based Access Control.
- Data encryption</br>
Encrypt sensitive data at rest and transit; use transport layer security
for data in transit.

> What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications?

Concurrency and resource management issues may arise when handling bidirectional streaming in Rust gRPC. We have to handle concurrent messages and shared states carefully to avoid race conditions and inconsistency issues. Bidirectional streaming can lead to long-lived connections, which require efficient resource management to handle a large number of concurrent connections.

> What are the advantages and disadvantages of using the `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC services?

- Advantages</br>
It integrates well with Tokio, which is one of the most widely used asynchronous runtime.
- Disadvantages</br>
It is a bit complex to understand for developers who are new to asynchronous programming and might require additional learning effort.

> In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?

I think we can adhere to the separation of concerns principle to make sure that the code is structured into logical modules based on functionality, similar to what we did in previous exercises.

> In the **MyPaymentService** implementation, what additional steps might be necessary to handle more complex payment processing logic?

Adding an input validation step can be useful to ensure safety and validate if the data that is received meets the expected criteria.

> What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?

gRPC promotes interoperability across programming languages as clients and servers that are written in different languages, can seamlessly communicate using generated code from the same Protobuf definition.

> What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?

- Advantages</br>
HTTP/2 supports multiplexing, allowing multiple requests and responses to be sent and received in parallel over a single connection. It also supports header compression and binary framing which improves its performance over HTTP/1.1.

- Disadvantages</br>
HTTP/2 is more complex, harder to implement, and not as widely supported as HTTP/1.1.

> How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?

The request-response model of REST APIs follows a one-way communication where the client sends a request to the server and waits for the server to respond. This type of communication is not ideal for real-time updates communication. Bidirectional streaming in gRPC allows both clients and servers to send and receive messages continuously making it more responsive.

> What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?

Protocol Buffers offer advantages like strong typing, efficient serialization, and versioning support, but demand upfront schema definition and code generation. On the other hand, JSON in REST APIs provides flexibility and compatibility, though it has potential drawbacks in possible runtime error, efficiency, and versioning.