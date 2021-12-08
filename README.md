
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
