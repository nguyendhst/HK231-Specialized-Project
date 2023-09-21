# System Design

***

- [High-level architecture of the low-code platform](#high-level-architecture)
- [Explanation of the chosen architectural style](#architectural-style)
- [Description of the key components and their interactions](#key-components)
- [Detailed design of each microservice and its responsibilities](#container-diagram)

***

## High-Level Architecture

### Workflow
### Architectural Style

Arcchitecture style is the fundamental structural design of a software system. It consists of a set of patterns and principles used to define the system's components, their interactions, and the constraints that guide their design and evolution. [<sup>1</sup>](https://en.wikipedia.org/wiki/Software_architecture)

#### Choosing architectural styles

Given the context of developing a low-code platform, some criterias for choosing architectural styles are:

- **Modularity and Reusability:** The architecture should promote modular design priciples and enabling the development of reusable components/services. The low-code platform includes many core functionalities such as:
	- Data Management
	- Business Logic Execution
	- Application Deployment

- **Scalability:** The architecture should support the platform's ability to serve increasing workloads and user's application requirements. Additional infrastructure resource should be able to horizontally scale to accomodate growth without performance trade-off.

- **User Experience:** The architecture should enable the platform to prioritize providing intuitive user experience. It should promote separation of concerns between the user interface and the server-side logic. 

- **Performance and Efficiency:** The architecture should be designed to optimize performance and ensure efficient resource utilization. It should consider factors such as response times, system throughput, data storage, caching mechanisms, and efficient handling of concurrent user interactions.

- **Integration Capabilities:** The architecture should provide seamless integration capabilities with external systems, databases, and services. It should support various integration patterns such as API-based integrations, message queues, or event-driven architectures to enable smooth data exchange and interoperability.

#### Comparison of some candidates

**Layered Architecture**: Layered architecture, also known as multi-tier architecture, is a software architecture pattern that organizes code into layers where each layer has a specific role and responsibility. This architecture is often used in large-scale applications due to its ability to isolate concerns, enhance maintainability, and support scalability [<sup>2</sup>](https://www.outsystems.com/blog/posts/application-architecture/).

- **Modularity and Reusability:** Layered architecture promotes separation of concerns, which leads to more modular and reusable code. 
- **Scalability:** Layered architecture supports scalability, particularly vertical scalability. By separating concerns into different layers, we can scale each layer independently based on its specific resource needs. However, horizontal scalability can be challenging with layered architecture, as it requires careful design to ensure stateless behavior and handle distributed data.
- **User Experience:** The presentation layer can handles user interface concerns, while business logic and data access are separated into their own layers [<sup>3</sup>](https://www.outsystems.com/blog/posts/application-architecture/).
- **Performance and Efficiency:** Multiple layers can introduce latency due to the overhead of inter-layer communication. This can impact performance and efficiency, particularly for high-throughput or latency-sensitive applications.
- **Integration Capabilities:** Layered architecture can support integration with external systems through the use of APIs in the business layer or integration layer. However, development effort can be high for such integration capabilities.

**Event-Driven Architecture**

Event-Driven Architecture (EDA) uses a publish-subscribe (pub-sub) model, where producers publish events, and consumers subscribe to them. The producers are independent of the consumers, and consumers are independent of each other. It is useful when different subsystems must perform different types of processing on the same event data [<sup>4</sup>](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/).

- **Modularity and Reusability:** EDA supports modular design and reusability. Events can be consumed by multiple services, and each service can process the data separately and apply their individual business logic.
- **Scalability:** EDA can improve the scalability of a system. It allows components to communicate asynchronously—producers publish event messages, on their own schedule, without waiting for consumers to receive them [Source 10](https://aws.amazon.com/what-is/eda/).
- **User Experience:** EDA can enhance user experience as it allows users to complete a task in one component and move on to the next task without waiting[<sup>5</sup>](https://www.ibm.com/topics/event-driven-architecture).
- **Performance and Efficiency:** EDA can handle a large number of events with low latency. Moreover, with less polling, there is a reduction in network I/O, and decreased costs[<sup>6</sup>](https://cloud.google.com/eventarc/docs/event-driven-architectures).
- **Integration Capabilities**: EDA supports integration capabilities. Event producers are unaware of, unconcerned by, and unburdened by any activity of downstream consumers of the events that they produce [<sup>7</sup>](https://aws.amazon.com/what-is/eda/).


**Microservices Architecture**

A Microservices Architecture is an architectural method that relies on a series of independently deployable services. These services have their own business logic and database with a specific goal. Updating, testing, deployment, and scaling occur within each service. Microservices don't reduce complexity, but they make any complexity visible and more manageable by separating tasks into smaller processes that function independently of each other [<sup>8</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).

*Advantages*

- **Modularity and Reusability**: MSA supports modularity and reusability. Each microservice is a separate, independently deployable module. Microservices can be reused across different parts of an application or even across different applications [<sup>9</sup>](https://www.techtarget.com/searchapparchitecture/tip/The-ups-and-downs-of-low-code-microservices-development).
- **Scalability**: Each microservice can be scaled independently based on its specific needs, which leads to better resource utilization [<sup>10</sup>](https://stackify.com/6-key-benefits-of-microservices-architecture/).
- **User Experience**: MSA can improve user experience by allowing for faster updates and feature additions. Each microservice can be updated independently without impacting the entire application, enabling quicker adaptations to user feedback and needs [<sup>11</sup>](https://www.techtarget.com/searchapparchitecture/tip/The-ups-and-downs-of-low-code-microservices-development).
- **Performance and Efficiency**: MSA can boost performance and efficiency by allowing each microservice to run its own processes and manage its own database. However, inter-service communication can add latency and complexity, which can impact performance and efficiency [<sup>12</sup>](https://learn.microsoft.com/en-us/azure/architecture/microservices/).
- **Integration Capabilities**: MSA facilitates integration with external systems. Each microservice can expose its own API, allowing for easy integration with other services. However, managing these integrations can be complex [<sup>13</sup>](https://www.techtarget.com/searchapparchitecture/tip/The-ups-and-downs-of-low-code-microservices-development).


Using a **microservices architecture**, we can address these problems by breaking down the platform into smaller, more manageable services. Each service can be developed, tested, and deployed independently, allowing for better control of the resources used by the system. This also allows for easier handling of scalability and performance, as each service can be scaled separately.

However, there are some notable disadvantages:

- **Increased Complexity**: Microservices can add increased complexity that leads to development sprawl, or rapid and unmanaged growth. It can be challenging to determine how different components relate to each other [<sup>14</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).
- **Debugging Challenges**: Each microservice has its own set of logs, which makes debugging more complicated. A single business process can run across multiple machines, further complicating debugging [<sup>15</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).

**Event-Driven Architecture:**

- Implement an event-driven approach to handle interactions and communication between different components of the platform.
- Events can be triggered when a user models an application, defines business logic, or deploys an application.
- Event-driven architecture allows for decoupling and asynchronous processing of events, enhancing scalability and responsiveness.
- Benefits: Loose coupling, scalability, and flexibility in handling user interactions and system events.

**Stateless Client-Server Architecture:**

- Implement a stateless client-server architecture where the server does not store any client state.
- Utilize a client-server architectural pattern where the web-based user interface (web browser client) communicates with the server-side components.
- The client interface allows users to model applications, define business logic, and interact with the platform.
- The server-side components handle the storage, retrieval, and execution of user-defined models and application logic.
- Benefits: Separation of concerns, easier user interaction, and centralized management of data and logic.

## Architecture Diagrams

### Key Components

- **User Management Microservice:**

	- This microservice handles user authentication, registration, profile management, and access control.

	- It provides APIs for user-related operations, such as user creation, authentication, and updating user profiles.

- **Project Management Microservice:**

	- This microservice is responsible for managing user projects within the platform.
	- It handles operations like creating, updating, and deleting projects, as well as retrieving project information.
	- It provides APIs for project management, such as project creation, retrieval, and modification.

- **Application Deployment Microservice:**

	- This microservice focuses on deploying the web applications created by users within the platform.
	- It receives the application models, validates them, and handles the deployment process.
	- It may interact with other microservices to ensure the availability of necessary resources for the deployed applications.

- **Business Logic Execution Microservice:**

	- This microservice is responsible for executing the business logic defined by users within their applications.
	- It receives the user-defined logic, which can be in the form of scripts, rules, workflows, or other configurations.
	- It executes the logic based on the runtime context and provides the necessary data and services to support the execution.

These microservices can communicate with each other using well-defined APIs and protocols, such as RESTful APIs or message queues. The communication can be synchronous or asynchronous, depending on the requirements of the platform.

By adopting a microservices architecture, the low-code platform can benefit from modularity, scalability, independent development and deployment, and the ability to incorporate new functionalities or services without affecting the entire system.

### System Context Diagram
### Container Diagram
### Component Diagram
### Deployment Diagram

## References