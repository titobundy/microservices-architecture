
# Microservices Architecture

## Definition

Martin Fowlers

*"The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP or gRPC API."*

Sam Newman

*"Microservices are small, autonomous services that work together modelled around a business domain."*

## What is a service ?

According to the [OASIS definition], a service is a mechanism that enables access to one or more capabilities, where the access is provided using a prescribed interface and is exercised consistent with constraints and policies as specified by the service description. 

In our case, these capabilities might be executing commands, querying, or raising events. All of them make up a service’s public interface.

## Representation

Microservices is an architectural style that structures an application as a collection of small autonomous services, modeled around a business domain.

![Microservices Representation](img/fig-01.png?raw=true "Microservices Representation")

In the given Architecture, each service is self-contained and implements a single business capability (*).

A business capability is what a business does to generate value (for example, sales, customer service, or marketing).

(*) Los componentes y los servicios están organizados en función de las capacidades del negocio, aquello que contribuye o aporta valor al negocio para lograr sus objetivos.

## Why Microservices ?

The concept of Microservices came out of a need of solutions to the problems with monolithic architectures. We refer to an architecture as monolithic if the entire app is built into one executable/package, deployed all or nothing, using one or very few data stores. 


### Monolithic Architecture

A monolithic applications has most of its functionality within a single process that is commonly componentized with libraries.

- Single codebase
- Single process
- Single host
- Single database
- Consistent technology

These applications usually use tiered architectures (e.g. presentation, business logic, data layer) and internal modularization.

![Monolithic Architecture](img/fig-02.jpg?raw=true "Monolithic Architecture")


### Benefits of Monolithic Architecture

Simplicity
One codebase
- Simply to develop
- Easy to find things
- Easier debugging and testing: end-to-end testing much faster
Deployment
- One application to replace: Do not have to handle many deployments, just one file or directory.
- Less cross-cutting concerns: such as logging, handling, caching, and performance monitoring
Monoliths are not “wrong

### Limitations of Monolithic Architecture

- Inflexible: It is extremely problematic to apply a new technology in a monolithic application because then the entire application has to be rewritten.
- Unreliable: Even if one feature of the system does not work, then the entire system does not work (Resiliency).
- Unscalable: Scales (horizontal scaling) by cloning the app on multiple servers/VMs/Containers. Can not scale components independently, only the whole application (*).
- Blocks Continous Development: Many features of the applications cannot be built and deployed at the same time.
- Slow Development: Development in monolithic applications take lot of time to be built since each and every feature has to be built one after the other.
- Not Fit For Complex Applications: Features of complex applications have tightly coupled dependencies.


![Limitations of Monolithic Architecture](img/fig-03.png?raw=true "Limitations of Monolithic Architecture")

Horizontal scaling (X-axis) is a common way to scale a monolithic application. You run multiple instances of the application behind a load balancer. The load balancer distributes requests among the N identical instances of the application. This is a great way of improving the capacity and availability of an application.


## Monolithics vs Microservices

![Differences](img/fig-04.jpg?raw=true "Differences between Monolithics and Microservices Architectures")

## Microservices

### Why Microservices ?

Building Microservices allows us the opportunity to tackle software complexity and deliver faster; if (and it’s a big if) we build our services right: choosing the right tech, interfaces, and integration patterns.

Microservices are a way of breaking down applications into their parts so that businesses can deliver the components separately, experiment with distinct technology stacks, and create clear boundaries between business logic.

But building microservices isn’t easy an easy task. With microservices, you need to consider many things, such as how (and where) you split the services, how they talk to each other (integration), and what data they share.

### Microservices Architecture

Within a microservices architecture, the entire functionality is split up into independently deployable modules which communicate with each other through defined methods called APIs (Application Programming Interfaces). Each service covers its own scope and can be updated, deployed, and scaled independently.

The microservice architecture enables the rapid, frequent and reliable delivery of large, complex applications. It also enables an organization to evolve its technology stack.

![Architecture](img/fig-05.png?raw=true "Architecture")

- Different clients from different devices try to use different services like search, build, configure and other management capabilities.

- All the services are separated based on their domains and functionalities and  are further allotted to individual microservices.

- These microservices have their own load balancer and execution environment to execute their functionalities & at the same time captures data in their own databases.

- All the microservices communicate with each other through a stateless server which is either REST or Message Bus.

- Microservices know their path of communication with the help of Service Discovery and perform operational capabilities such as automation, monitoring.

- Then all the functionalities performed by microservices are communicated to clients via API Gateway.

- All the internal points are connected from the API Gateway. So, anybody who connects to the API Gateway automatically gets connected to the complete system.

### Principles by Sam Newman

![Principles Sam Newman](img/fig-06.png?raw=true "Principles Sam Newman")

- Modelled Around Business Domain: Provides more stables api. Services should represent a bounded context within the domain.

- Culture of Automatization: Allows scalability at speed.
- Hide Implementation Details: Evolution, allows one service evolve independently of another.
- Decentralise All the Things: Allows agility.
- Deploy Independently: Allows agility and availability.
- Consumer First: Provides useful services. Services exist to be called so they should be built outside in rather than inside out.
- Isolate Failure: Allows availability. Failure in one service should not have a cascading effect.
- Highly Observable: Provides maintainability.

### Features

![Features](img/fig-06-b.png?raw=true "Features")

- Decoupling: Services within a system are largely decoupled. So the application as a whole can be easily built, altered, and scaled.
- Componentization: Microservices are treated as independent components that can be easily replaced and upgraded.
- Business Capabilities: Microservices are very simple and focus on a single capability.
- Autonomy: Developers and teams can work independently of each other, thus increasing speed.
- Continous Delivery: Allows frequent releases of software, through systematic automation of software creation, testing, and approval.
- Responsibility: Microservices do not focus on applications as projects. Instead, they treat applications as products for which they are responsible.
- Decentralized Governance: The focus is on using the right tool for the right job. That means there is no standardized pattern or any technology pattern. Developers have the freedom to choose the best useful tools to solve their problems.
- Agility: Any new feature can be quickly developed and discarded again.

### Advantages Of Microservices

![Benefits](img/fig-07.png?raw=true "Benefits")

- Independent Development: All microservices can be easily developed based on their individual functionality.
- Independent Deployment: Based on their services, they can be individually deployed in any application.
- Fault Isolation: Even if one service of the application does not work, the system still continues to - function.
- Mixed Technology Stack: Different languages and technologies can be used to build different services of the same application.
- Granular Scaling:  Individual components can scale as per need, there is no need to scale all components together.

Other Benefits:
- Better development scaling.
- Higher development velocity.
- Supports iterative or incremental modernization.
- Take advantage of the modern Software - Development Ecosystem (Cloud, Containers, - DevOps, Serverless).
- Supports horizontal scaling and granular scaling.
- It puts low cognitive complexity on the - developer’s head thanks to its smaller size.

### Challenges of Microservices Architecture

![Challenges](img/fig-08.png?raw=true "Challenges")

- Difficult integration testing: Independent services within a microservices-based application may be tested in different environments.
- Operational Complexity: Management of multiple databases and transactions can be really cumbersome. The problem of operational complexity may be partially solved by the implementation of new configuration management tools (e.g. Docker, Ansible).
- Network problems and latency: So since microservice are small and communicate with inter-service communication, we should manage network problems. If we call chain of services for particular request, this will increate latency problems and need correct design to APIs for proper communication.
- Data Integrity: Maintaining strong consistency is extremely difficult for a distributed system, which means everyone has to manage eventual consistency.


## Design Patterns for Microservices

Applying all these principles brings several challenges and issues. Those can overcome with using correct and matching design patterns. Let's discuss those problems and their solutions.

There are design patterns for microservices and those can divide into five Patterns

![categories](img/fig-09.png?raw=true "categories")

### Decomposition Patterns

How to decompose the application into services?

Another challenge is deciding how to partition the system into microservices. This is very much an art, but there are a number of strategies that can help:

- Decompose by business capability and define services corresponding to business capabilities.
- Decompose by domain-driven design subdomain.
- Decompose by verb or use case and define services that are responsible for particular actions. e.g. a Shipping Service that’s responsible for shipping complete orders.
- Decompose by by nouns or resources by defining a service that is responsible for all operations on entities/resources of a given type. e.g. an Account Service that is responsible for managing user accounts.

Ideally, each service should have only a small set of responsibilities. (Uncle) Bob Martin talks about designing classes using the Single Responsibility Principle (SRP). The SRP defines a responsibility of a class as a reason to change, and states that a class should only have one reason to change. It make sense to apply the SRP to service design as well.

Another analogy that helps with service design is the design of Unix utilities. Unix provides a large number of utilities such as grep, cat and find. Each utility does exactly one thing, often exceptionally well, and is intended to be combined with other utilities using a shell script to perform complex tasks.

---

- **By Business Capability**

    - Define services corresponding to business capabilities.
    - A business capability is a concept from business architecture modeling.
    - A business service should generate value.
    - A business capability often corresponds to a business object, e.g.

![decomposition-by-bussiness](img/fig-10.png?raw=true "decomposition-by-bussiness")

---

- **By Subdomain**

    - This pattern uses a domain-driven design (DDD) subdomain to decompose monoliths.
    - DDD refers to the application’s problem space - the business - as the domain. 
    - Define services corresponding to Domain-Driven Design (DDD) subdomains.
    - A domain is consists of multiple subdomains. Each subdomain corresponds to a different part of the business.
    - Each subdomain has a model and the scope of that model is called a bounded context; microservices are developed around this bounded context.
    
![decomposition-by-subdomain](img/fig-11.png?raw=true "decomposition-by-subdomain")    

Decomposition Microservices Architecture Path

![decomposition-by-subdomain-steps](img/fig-12.png?raw=true "decomposition-by-subdomain-steps")   

---

- **Strangler Fig Pattern**

Incrementally migrate a legacy system by gradually replacing specific pieces of functionality with new applications and services. As features from the legacy system are replaced, the new system eventually replaces all of the old system's features, strangling the old system and allowing you to decommission it.

![decomposition-by-strangler-analogy](img/fig-13-b.jpg?raw=true "decomposition-by-strangler-analogy")

The strangler application consists of two types of services: 

    - First, there are services that implement functionality that previously resided in the monolith.
    - Second, there are services that implement new features. The latter are particularly useful since they demonstrate to the business the value of using microservices.

![decomposition-by-strangler](img/fig-13.jpeg?raw=true "decomposition-by-strangler") 

---

- BranchByAbstraction

### Microservices Communications

- Sync/Async Communication
- Api Gateway Pattern

### Database Managment

- Database per Service
- Saga Pattern

### Best Practices

- Design
- Hardcoded values
- Logging
- Versioning
- Authorization and authentication mechanism
- Dependency
- Make executable contracts
- Fault tolerance
- Documentation