
## Message Queues

A message queue is a form of asynchronous service-to-service communication used in serverless and microservices architectures.
Messages are stored on the queue until they are processed and deleted. Each message is processed only once, by a single consumer. Message queues can be used to decouple heavyweight processing and to buffer or batch work.

### Basic architecture

The basic architecture of a message queue is simple. there are client applications called producers that create messages and deliver them to the message queue. Another application, called a consumer, connects to the queue and gets the messages to be processed. Messages placed onto the queue are stored until the consumer retrieves them.

### Asynchronous Communication

A message queue provides an asynchronous communications protocol, which is a system that puts a message onto a message queue and does not require an immediate response to continuing processing.
Email is probably the best example of asynchronous communication

## Decoupling

Decoupling describes how much one piece of a system relies on another piece of the system. Decoupling is the process of separating functions so that they are more self contained.

A Decoupled system is achieved when two or more systems are able to communicate without being connected.
The systems can remain completely autonomous and unaware of other functions. Decoupling is often a sign of a computer system that is well structured because it is easier to maintain.

Insted of bulding one large application, it is beneficial to decouple different parts of your application and communicate between them asynchronously using message ueues. This allows for different parts of the application to evolve independently, be written in different languages, and/or be maintained by separated development teams. In other words, message queue helps the system to scale.
