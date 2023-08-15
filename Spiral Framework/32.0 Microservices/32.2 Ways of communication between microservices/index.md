## Ways of communication between microservices

When it comes to communication between microservices, there are several protocols that you can use, each with its own pros and cons.

1. **HTTP/REST**: This is a stateless protocol, which means each request from client to server must contain all the information needed to understand and process the request. It's simple and easy to use, but it may not be the most efficient for complex or high-volume microservices communication.

2. **gRPC**: This is a high-performance, open-source universal RPC framework developed by Google. It uses Protocol Buffers as its interface definition language, allowing you to define services and message types in .proto files. It's highly efficient and suitable for point-to-point real-time communication. However, it's more complex to set up and use compared to HTTP/REST.

3. **GraphQL**: This is a query language for APIs and a runtime for executing those queries with your existing data. It's highly flexible and allows clients to request exactly the data they need, reducing the amount of data that needs to be transferred. However, it can be more complex to set up and maintain compared to other options.

4. **Message Queues (RabbitMQ, Kafka, etc.)**: These are used for asynchronous communication between microservices. They allow you to decouple your microservices and provide fault tolerance. However, they can add complexity to your system and require careful management to ensure reliability.

5. **Event-Driven Architecture (EDA)**: This is a pattern that can be used to produce, detect, consume, and react to events. It's highly scalable and can provide real-time updates, but it can also add complexity to your system.

Choosing the right protocol depends on your specific use case and requirements. You might even use a combination of these protocols in a single application.

### Links and materials to read more:
1. [HTTP/REST](https://www.restapitutorial.com/)
2. [gRPC](https://grpc.io/)
3. [GraphQL](https://graphql.org/)
4. [RabbitMQ](https://www.rabbitmq.com/)
5. [Kafka](https://kafka.apache.org/)
6. [Event-Driven Architecture](https://martinfowler.com/articles/201701-event-driven.html)
