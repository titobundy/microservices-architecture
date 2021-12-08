
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
