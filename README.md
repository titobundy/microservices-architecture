
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

### Principles

By Sam Newman

![Principles Sam Newman](img/fig-06-a.png?raw=true "Principles Sam Newman")

- Model around a business domain, provides stable APIs.
- Decentralize, allows agility.
- Embrace automation, allows scalability at speed.
- Hide implementation details, allows evolution.
- Deploy independently, allows agility and availability.
- Consumer first, provides useful services.
- Isolate failure, allows availability.
- Highly observable, provides maintainability.

![Principles](img/fig-06-b.png?raw=true "Principles")

- Decoupling – Services within a system are largely decoupled. So the application as a whole can be easily built, altered, and scaled.
- Componentization – Microservices are treated as independent components that can be easily replaced and upgraded.
- Business Capabilities – Microservices are very simple and focus on a single capability.
- Autonomy – Developers and teams can work independently of each other, thus increasing speed.
- Continous Delivery – Allows frequent releases of software, through systematic automation of software creation, testing, and approval.
- Responsibility – Microservices do not focus on applications as projects. Instead, they treat applications as products for which they are responsible.
- Decentralized Governance – The focus is on using the right tool for the right job. That means there is no standardized pattern or any technology pattern. Developers have the freedom to choose the best useful tools to solve their problems.
- Agility – Any new feature can be quickly developed and discarded again.



