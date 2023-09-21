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

Given the context, some criterias for choosing architectural styles are:


**Service-Based Architecture**

A Service-Based Architecture (SBA) is a type of architecture where services are the primary architectural components. The services are built on the concept of sharing as much as possible. For example, in a large retail company that has many applications associated with the processing of an order, SOA tries to address this problem through enterprise-level shared services (enterprise services). The Order service is smart enough to know which database to go to retrieve and update order data for each system, at the same time synchronizing the data among all three systems [<sup>1</sup>](https://www.oreilly.com/radar/microservices-vs-service-oriented-architecture/).

*Advantages*

- **Component Sharing**: SBA promotes the sharing of components across the enterprise, increasing scalability and efficiency [<sup>1</sup>](https://www.ibm.com/blog/soa-vs-microservices/).
- **Service Availability and Responsiveness**: SBA addresses service availability (the ability of a remote service to accept requests in a timely manner) and service responsiveness (the ability of the service consumer to receive a timely response from the service) [<sup>1</sup>](https://www.oreilly.com/radar/microservices-vs-service-oriented-architecture/).

*Disadvantages*

- **Complexity**: SBA can be complex and might not be needed for all types of applications. It might be a good choice for larger, more diverse environments but less so for smaller environments like web and mobile applications [<sup>1</sup>](https://www.ibm.com/blog/soa-vs-microservices/).
- **Coordination**: There might be a need for coordination among services to fulfill a single business request, which can increase development, testing, deployment, and maintenance time [<sup>1</sup>](https://www.oreilly.com/radar/microservices-vs-service-oriented-architecture/).

**Event-Driven Architecture**

Event-Driven Architecture (EDA) uses a publish-subscribe (pub-sub) model, where producers publish events, and consumers subscribe to them. The producers are independent of the consumers, and consumers are independent of each other. It is useful when different subsystems must perform different types of processing on the same event data [<sup>1</sup>](https://learn.microsoft.com/en-us/azure/architecture/guide/architecture-styles/).

*Advantages*

- Decoupling: In EDA, the producers and consumers are decoupled, which allows them to be scaled, updated, and deployed independently [<sup>1</sup>](https://aws.amazon.com/event-driven-architecture/).
- Fault Tolerance: Since services are decoupled from each other in EDA, faults are isolated to individual services. If a subscribing service fails, it doesn't impact the service that sent the event. Communications are queued in a broker until the subscriber is repaired or replaced [<sup>1</sup>](https://www.techtarget.com/searchapparchitecture/tip/Event-driven-architecture-pros-and-cons-Is-EDA-worth-it).
- Real-Time Processing and Responsiveness: EDA enables real-time processing and responsiveness by reacting to events as they occur. It ensures that the system can respond quickly to changes, enabling faster decision-making, real-time analytics, and immediate action [<sup>1</sup>](https://www.confluent.io/learn/event-driven-architecture/).

*Disadvantages*

- Difficulties with Monitoring: Since the services are independent of each other, you need a proper design to understand how they interact with each other and also a proper alerting mechanism to understand the knock-on effect should a service fail [<sup>1</sup>](https://solace.com/blog/event-driven-architecture-pros-and-cons/)
- Complexity: EDA can be complex to implement and manage. It requires a different programming model that may be unfamiliar to developers who are used to request-response models [<sup>1</sup>](https://dev.to/aws-builders/event-driven-vs-workflows-a-comprehensive-comparison-for-developers-and-architects-2j9k).

**Microservices Architecture**

A Microservices Architecture is an architectural method that relies on a series of independently deployable services. These services have their own business logic and database with a specific goal. Updating, testing, deployment, and scaling occur within each service. Microservices don't reduce complexity, but they make any complexity visible and more manageable by separating tasks into smaller processes that function independently of each other [<sup>1</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).

*Advantages*

- **Independent Deployment**: Microservices can be deployed independently, allowing developers to update or fix issues in one service without affecting the others [<sup>1</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).
- **Scalability**: Each microservice can be scaled independently based on its specific needs, which leads to better resource utilization [<sup>1</sup>](https://stackify.com/6-key-benefits-of-microservices-architecture/).
- **Technology Diversity**: In a microservices architecture, each service can be built using the technology stack that best suits its requirements. This allows developers to choose the most suitable technologies for each service [<sup>1</sup>](https://about.gitlab.com/blog/2022/09/29/what-are-the-benefits-of-a-microservices-architecture/).

*Disadvantages*

- **Increased Complexity**: Microservices can add increased complexity that leads to development sprawl, or rapid and unmanaged growth. It can be challenging to determine how different components relate to each other [<sup>1</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).
- **Debugging Challenges**: Each microservice has its own set of logs, which makes debugging more complicated. A single business process can run across multiple machines, further complicating debugging [<sup>1</sup>](https://www.atlassian.com/microservices/microservices-architecture/microservices-vs-monolith).


For a low-code platform that includes a web-based user interface for modeling applications, defining business logic, and deploying web applications. There are several prolems that need to be addressed:

- Performance: The platform should be able to handle a large number of users and applications.
- Scalability: The platform should be able to scale up and down based on demand since a common runtime environment is used for all applications.
- Many core functionalities:
	- Data Management
	- Business Logic Execution
	- Application Deployment

Using a **microservices architecture**, we can address these problems by breaking down the platform into smaller, more manageable services. Each service can be developed, tested, and deployed independently, allowing for better control of the resources used by the system. This also allows for easier handling of scalability and performance, as each service can be scaled separately.

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
