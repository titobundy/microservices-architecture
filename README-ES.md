# Microservices Architecture

## Definition

### Service

Según OASIS (Organization for the Advancement of Structured Information Standards), se entiende por servicio “un mecanismo para habilitar acceso a una o más capacidades, donde el acceso es provisto utilizando una interfaz prescripta y es ejecutado de manera consistente con restricciones y políticas especificadas por la descripción del servicio.”

Un servicio es una funcionalidad o un conjunto de funcionalidades de software con el objetivo de que pueda ser reutilizado por distintos clientes con distintos propósitos, junto con las políticas que deben controlar su uso.

https://en.wikipedia.org/wiki/Service_(systems_architecture)

---

### Microservices

From Martin Fowlers Microservices article;
The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP or gRPC API.

Sam Newman
Microservices are small, autonomous services that work together modelled around a business domain. Let’s break that definition down a bit and consider the characteristics that make microservices different.

---

### Representation

Cada servicio es autónomo e implementa una única capacidad empresarial.

Los componentes y los servicios están organizados en función de las capacidades del negocio, aquello que contribuye o aporta valor al negocio para lograr sus objetivos.

---

## Why Microservices ?

El concepto de Microservicios surgió de una necesidad de soluciones a los problemas con las arquitecturas monolíticas.

Nos referimos a una arquitectura como monolítica si toda la aplicación está integrada en un ejecutable/paquete, implementada todo o nada, usando uno o muy pocos almacenes de datos.

---

### Monolithic Architecture

Una aplicación monolítica tiene la mayor parte de su funcionalidad dentro de un solo proceso que comúnmente se compone de librerías.

- Single codebase (Codigo fuente unico)
- Single process
- Single host
- Single database
- Consistent technology

Estas aplicaciones suelen utilizar arquitecturas escalonadas (por ejemplo, presentación, lógica empresarial, capa de datos) y modularización interna.

---

**Benefits**

- Fácil de desarrollar.
- Fácil encontrar cosas debido a un unico codigo
- Fácil de depurar y realizar pruebas.
- Despliegue de solo una aplicación.
- Menos responsabilidades transversales, tales como logging, manejo de caché, monitoreo de desempeño.

---

**Limitations**

- **Inflexible**: Es extremadamente problemático aplicar una nueva tecnología en una aplicación monolítica porque entonces toda la aplicación tiene que ser reescrita.

- **No confiable**: Un error en algún punto del sistema significa que todo el sistema puede fallar en un segundo (Resiliency).

- **No escalable**: Escala (escalamiento horizontal) clonando la aplicación en varios servidores/máquinas virtuales/contenedores. No se pueden escalar componentes de forma independiente, solo toda la aplicación. El escalamiento vertical tiene limitaciones y es más costoso.

- **Bloquea el desarrollo continuo**: Limita la agilidad en el sentido de que muchas características de las aplicaciones no se pueden construir e implementar al mismo tiempo. Por otro lado cualquier cambio por pequeño que sea requiere el re-despliegue de toda la aplicación.

- **Desarrollo lento**: El desarrollo en aplicaciones monolíticas requiere mucho tiempo para construirse, ya que todas y cada una de las funciones deben construirse una tras otra, las reparaciones son lentas y costosas . Por otro lado tenemos un solo gran código fuente, lo que sobrecarga los IDES y ralentiza los tiempos de inicio de la aplicación.

- **No apto para aplicaciones complejas**: Son un reto de crecimiento y el cambio. Si la aplicación crece en complejidad, en líneas de código y en el número de características, es más riesgoso y costoso efectuar cambios, las características de las aplicaciones complejas tienen dependencias estrechamente acopladas.

---

**Why Microservices?**

La creación de microservicios nos brinda la oportunidad de abordar la complejidad del software y entregar más rápido; si (y es un gran si) construimos nuestros servicios correctamente: eligiendo la tecnología, las interfaces y los patrones de integración adecuados.

Los microservicios son una forma de dividir las aplicaciones, para que podamos entregar los componentes por separado, experimentar con distintos stacks tecnologicos y crear límites claros entre la lógica de negocio.

Pero crear microservicios no es una tarea sencilla. Se debe considerar muchas cosas, tales como ¿cómo (y dónde)  dividir los servicios?, ¿cómo se comunican entre sí (integración) y qué datos compartirán?.

---

### Microservices Architecture

Dentro de una arquitectura de microservicios, toda la funcionalidad se divide en módulos implementables de forma independiente que se comunican entre sí a través de métodos definidos llamados API (interfaces de programación de aplicaciones). 

Cada servicio cubre su propio alcance y se puede actualizar, implementar y escalar de forma independiente.

La arquitectura de microservicio permite la entrega rápida, frecuente y confiable de aplicaciones grandes y complejas. También permite que una organización evolucione su stack de tecnología.

En la figura:

- Diferentes clientes desde diferentes dispositivos intentan utilizar diferentes servicios.
- Todos los servicios se separan en función de sus dominios y funcionalidades y se asignan a microservicios individuales.
- Todos los microservicios se comunican entre sí a través de un servidor sin estado como pueden ser APIS REST o un un Bus de mensajes.
- Las funcionalidades expuestas por los microservicios son accedidas por los clientes son a través de un API Gateway.

---

### Advantages

- **Desarrollo independiente:** todos los microservicios se pueden desarrollar fácilmente en función de su funcionalidad individual.

- **Despliegue independiente:** según sus servicios, se pueden implementar individualmente en cualquier aplicación.

- **Tolerancia a fallas/Resiliencia:** Un error solo afectará a al servicio en el que ocurre, pero no afectará toda la aplicación.

- **Stack de tecnología mixta:** Permiten adaptarse fácilmente y aprovechar las últimas tecnologías emergentes. Se pueden usar diferentes lenguajes, bases de datos para construir diferentes servicios de la misma aplicación.

- **Escalado granular:** Los componentes individuales se pueden escalar según sus necesidades, no es necesario escalar todos los componentes juntos.


Otros Beneficios:

- Mayor velocidad de desarrollo
- Soporte al desarrollo iterativo/incremental.
- Aprovecha las ventajas del software moderno - Ecosistema de desarrollo (Cloud, Containers, DevOps, Serverless).
- Equipos flexibles, los diferentes microservicios requieren diferentes equipos de desarrolladores, tanto en tamaño como en estructura.

---

### Challenges

Aunque los microservicios se distinguen por su eficiencia, flexibilidad, agilidad y potencial de crecimiento, implican retos importantes para su implementación.

Al tener mayor número de componentes, su operación es más compleja, por lo que crear y desarrollar la infraestructura requiere más tiempo y más recursos. Esta es una razón para que una cultura DevOps le ofrezca agilidad al proceso de desarrollo. 

- **Pruebas de integración:** Probar microservicios puede ser engorroso y complicado debido a su naturaleza distribuida.

- **Complejidad operativa:** Cada servicio es simple, pero como un todo el sistema es más complejo. La gestión de múltiples bases de datos y transacciones puede ser realmente engorrosa. El problema de la complejidad operativa puede resolverse parcialmente mediante la implementación de nuevas herramientas de gestión de la configuración (por ejemplo, Docker, Ansible).

- **Problemas de red y latencia:** Debido a que los microservicios utilizan un tipo de comunicación inter-service (a través de la red) las peticiones pueden fallar y provocar un retraso, debemos mitigar la tolerancia a fallas, la latencia de la red y lidiar con una variedad de formatos de mensajes, así como con el equilibrio de carga. Si llamamos a la cadena de servicios para una solicitud particular, esto aumentará los problemas de latencia y necesitará un diseño correcto de las API para una comunicación adecuada.

- **Integridad de los datos:** Mantener una consistencia sólida es extremadamente difícil para un sistema distribuido. Cada microservicio dentro del sistema es responsable de su propia base de datos o algún otro almacenamiento. Esto crea el potencial de tener datos duplicados a los largo de los multiples servicios. La solución es establecer los limites de los servicios en los lugares correctos y siempre asegurar que cualquier dato en particular tenga una sola fuente de verdad.

---

## Principles of Microservices (Sam Newman)

Sam Newman, durante el trabajo que ha realizado con muchas empresas que implementan microservicios, ha establecido una lista de principios que han ayudado a dichas empresas, a construir microservicios exitosos.

Los principios de arquitectura existen por una razón, que es conseguir los objetivos estrategicos de la organizacion. Por otro lado los practicas y patrones de arquitectura es el mecanismo mediante implementamos estos principios.

La razon de estos principios es lograr construir pequeños servicios que sean autonomos.

- **Modeled Around Business Domain:** Proporcionan APIs más estable. Los servicios deben representar un contexto delimitado dentro del dominio. DDD es una herramienta para la division correcta (Decomposition by subdomain)
La historia ha demostrado que las interfaces estructuradas en torno a contextos delimitados por negocios son más estables que aquellas estructuradas en torno a conceptos técnicos.

- **Culture of Automatization:** Permite la escalabilidad a gran velocidad. Los microservicios agregan mucha complejidad, adoptar una cultura de automatización es una forma clave de abordar esto. Normalmente se adopta un enfoque Devops con CI/CD.
Las prácticas de desarrollo tales como: la automatización de pruebas, despliegue automatizado y la administración de la configuración, permiten que el sistema empresarial se escale de manera más eficiente y también mejore la coordinación de servicios.

- **Hide Implementation Details:** Permite que un servicio evolucione independientemente de otro. (Database per service)
Para maximizar la capacidad de un servicio para evolucionar independientemente de cualquier otro, es vital que ocultemos los detalles de implemebntacion, esto es esencial para mantener un bajo acoplamiento entre los servicios que interactúan en una aplicación empresarial.

- **Decentralise All the Things:** Permite agilidad. Este principio se basa en el requisito de que los servicios individuales deben desarrollarse, gestionarse y mantenerse de forma autónoma. Delegar la toma de decisiones y control a los equipos dueños de los microservicios.

- **Deploy Independently:** Permite agilidad y disponibilidad. Es uno de los principios mas importantes, debería poder cambiar un servicio y desplegarlo sin tener que realizar cambios en ningún otro servicio.

- **Consumer First:** Proporciona servicios útiles. Los servicios existen para ser llamados, por lo que deben construirse de afuera hacia adentro en lugar de adentro hacia afuera.

- **Isolate Failure:** Permite disponibilidad. La falla en un servicio no debería tener un efecto en cascada. (circuit breakers)

- **Highly Observable:** Proporciona mantenibilidad. 
Una parte importante de la gestión del ciclo de vida de las aplicaciones es el monitoreo. En el caso de los microservicios, debido a su naturaleza distribuida, es necesario proporcionar una solución de monitoreo para registrar el funcionamiento y el rendimiento del sistema.
Uso de herramientas de monitoreo y analisis de: logs, recursos, trafico, metricas, etc.


---

## Design Patterns for Microservices

La aplicación de los principios conlleva varios desafíos y problemas, problemas que son comunes para muchas soluciones. Por lo que podemos superar estos desafios con el uso de patrones de diseño adecuados.

Podemos categorizar los patrones de microservicios en 5 tipos, cada uno con varios patrones.

---

### Decomposition Patterns

Para desarrollar una aplicación grande y compleja usando la arquitectura de microservicios, necesitamos descomponer la aplicación en un conjunto de microservicios débilmente acoplados de una manera detallada y razonable. El objetivo de la arquitectura de microservicio es acelerar el desarrollo de software logrando una entrega/implementación continua.

Los microservicios son piezas de software que deben hacer cumplir con una función específica, preferiblemente cumpliendo con el principio de responsabilidad única (SRP); definir los límites no es tan sencillo y requiere de un detallado análisis. No existe un proceso exacto que siguiendo una lista de pasos nos ayude a diseñar microservicios de forma coherente.

Una de las claves de los microservicios es mantener servicios desacoplados, independientes de forma tal que se facilite su puesta en operación y reducir su tiempo de entrada al mercado (time-to-market)

---

#### By Business Capability

En este patrón se definen y modelan los microservicios acorde a las capacidades empresariales del negocio, enfocado en los elementos que aportan valor, por ejemplo, en una tienda online, existe comúnmente un área de productos, venta, entrega, pedidos, entre otras.

Llevando esto a capacidades del negocio puede traducirse en:
	- Gestión de productos.
	- Gestión de inventario.
	- Gestión de pedidos.
	- Gestión de entregas.	

Existe una relación entre el negocio y los posibles microservicios que podemos crear para soportar la automatización.

**Business Requirements**

Aquí estamos hablando de la colección de requerimientos en torno a una capacidad empresarial específica. Necesitamos identificar varias capacidades de negocio del sistema y comprender cuáles son los requerimientos.

---

#### By Subdomain

El enfoque de descomposición por subdominios se basa en los principios de Domain Driven Design (DDD), descrito por Eric Evans.

DDD propone un enfoque para alinear a los expertos del dominio y desarrolladores en base a objetivos claros, con un lenguaje común y centrado en el negocio.

Se proponen tres ejes principales para guiar el desarrollo:

- Centrarse en el dominio principal.
- Estructurar el diseño en un modelo de dominio.
- Realizar desarrollo iterativo para la mejora continua en estrecha colaboración entre los expertos del negocio y el equipo de desarrollo, usando un lenguaje común.

El diseño basado en dominio tienes dos partes principales:

Diseño estratégico: En esta etapa se define la estructura del sistema a gran escala, sin tener en cuenta ningún elemento técnico o tecnología, definimos el modelo a gran escala del sistema, definiendo las reglas de negocio. En esta etapa se definen los contextos delimitados para los modelos de dominio.

Diseño táctico: Se definen un conjunto de modelos de diseño que pueden usarse para crear el modelo de dominio. Estos modelos incluyen entidades, agregados y servicios de dominio.

A partir de las cuestiones conceptuales anteriores, vamos a seguir 4 pasos para llevar adelante la descomposición.

- Paso 1: Se inicia por analizar el dominio de la empresa para conocer los requisitos funcionales de la aplicación. El resultado de este paso es una descripción informal del dominio, que puede perfilarse en un conjunto más formal de modelos de dominio.

- Paso 2: Definir los contextos delimitados del dominio. Cada contexto delimitado contiene un modelo de dominio
que representa un subdominio concreto de la aplicación. 

- Paso 3: Dentro de cada contexto delimitado, se aplican los modelos tácticos de diseño basado en dominios para
definir las entidades, los agregados y los servicios de dominio.

- Paso 4: Se usan los resultados de etapas anteriores para identificar los microservicios de la aplicación.

----

#### Strangler Fig Pattern

A partir de la evolución de las arquitecturas, y especialmente con la llegada de los microservicios muchas aplicaciones inician un proceso de migración; el tamaño de los monolitos hace que ese proceso sea lento y gradual, surgiendo la necesidad de lograr una convivencia entre el viejo sistema y los nuevos servicios que se
van creando paulatinamente.

El patrón de estrangulación permite sustituir una aplicación heredada reemplazando de forma gradual y con menos riesgos, reemplazando piezas específicas de funcionalidad por nuevas aplicaciones y servicios. 

Este patrón ayuda a minimizar el riesgo de la migración y distribuye el esfuerzo de desarrollo a lo largo del tiempo.

Para lograr que el sistema legado funcione y cada uno de los microservicios que se van creando realice su tarea particular es necesario definir un mecanismo que sirva de fachada para las aplicaciones clientes y dirija el tráfico de las operaciones al ente correspondiente.

La fachada que se crea implementa una capa transparente para los clientes.

---

### Microservices Communications

#### Sync/Async Communication

El cliente y los servicios pueden comunicarse a través de muchos tipos diferentes de comunicación, cada uno destinado a un escenario y unos objetivos distintos. Inicialmente, esos tipos de comunicaciones se pueden clasificar en dos ejes.

**Synchronous communication**

La comunicación síncrona es la solución más sencilla cuando se intenta que los servicios se comuniquen. Como una llamada telefónica, el cliente envía una solicitud y espera una respuesta.

En el procesamiento sincrónico, un cliente envía una solicitud al servidor y espera a que el servidor complete su trabajo y envíe la respuesta antes de que el cliente pueda reanudar su trabajo.

A una solicitud sincrona se le denomina solicitud de bloqueante, ya que el cliente no puede realizar ningún otro trabajo hasta que se recibe una respuesta.

Protocolos: Se usa principalmente con los protolcos HTPP(S), API Restful, GraphQL, gRCP (Http 2 los servidios son definidos usando un protocolo de buffer).

**Asynchronous communication**

Es lo opuesto al procesamiento asincrono, aquí el cliente del mensaje no espera ninguna respuesta después de enviar una solicitud al servidor y continúa haciendo cualquier otro trabajo.

A este proceso se le conoce como no bloqueante, ya que el hilo de ejecución del cliente no está bloqueado. Esto permite que los sistemas escalen ya que se puede realizar más trabajo en un período de tiempo determinado.

La comunicación mediante mensajería asíncrona se usa, fundamentalmente, para la comunicación entre los distintos microservicios a través de un intermediario de mensajes o bróker, de tal manera que los productores de mensajes van colocándolos en una cola distribuida de la que los consumidores van recuperando. De este modo, productor y consumidor quedan totalmente desacoplados.

El protocolo más popular para estas comunicaciones asíncronas es AMQP (Protocolo avanzado de cola de mensajes). Así, con el uso de protocolos AMQP, el cliente envía el mensaje usando sistemas de mensajería tales como Kafka  RabbitMQ.

Un sistema de comunicación asincrona puede dividirse en 2, de acuerdo a su implementación, dependiendo si tiene un único receptos o varios.

- One-to-one(queue) mode:  Cada solicitud debe ser procesada por un receptor o servicio exactamente. (Command Pattern)
- One-to-many (topic) mode: Cada solicitud puede ser procesada por cero y varios receptores. (publish/subscribe)

---


#### Api Gateway Pattern


A diferencia de una arquitectura monolitica, hemos distribuido las funcionalidades en microservicios independientes y, con ello, la lógica y el acceso a los datos y, por tanto, dispersado el punto de entrada a la aplicación.

Las arquitecturas de microservicios se caracterizan por lo que se llama _dumb pipes_ (tuberías tontas), es decir, que es en los puntos finales donde reside toda la inteligencia y no debe invertirse esfuerzo en complicados mecanismos de comunicación que no aportan ningún valor al sistema y sí que supone un incremento considerable de la complejidad. Por ello, es preferible optar por mecanismos de comunicación ligeros y simples (dumb pipes).

---

**Comunicacion Directa**

En teoría, un cliente puede lanzar peticiones directas a cualquiera de los microservicios, ya que cada uno de ellos expone un endpoint (punto de acceso) público. Sin embargo esto trae problemas como la variedad de clientes con distintas capacidades, protocolos no orientados a la web (AMQP mensajeria), los clientes tienen que administrar multiples llamadas, incremento de latencia, complejidad adicional en el lado UI.

Una arquitectura de comunicación directa de cliente a microservicio podría ser suficiente para una pequeña aplicación basada en microservicio. Sin embargo, cuando creamos aplicaciones basadas en microservicios grandes y complejas y, sobre todo, cuando las aplicaciones cliente son aplicaciones móviles remotas o aplicaciones web SPA, este enfoque se enfrenta a algunos problemas.

- ¿Cómo pueden las aplicaciones cliente minimizar el número de solicitudes al back-end y reducir el exceso de comunicación con varios microservicios?

- ¿Cómo se pueden controlar cuestiones transversales como la autorización, las transformaciones de datos y la distribución de solicitudes dinámicas?

- ¿Cómo pueden las aplicaciones cliente comunicarse con servicios que usan protocolos no compatible con Internet?

- ¿Cómo se puede dar forma a una fachada creada especialmente para las aplicaciones móviles?

Para resolver éste y otros problemas relacionados se prefiere un esquema en el que un intermediario central se encargue de adaptar las llamadas a los microservicios (y sus respuestas) a distintos tipos de clientes, proporcionando API de la granularidad adecuada. Este intermediario es lo que se conoce como API Gateway.

---

**API Gateway**

Un API Gateway es un punto de acceso unico para todos los clientes, encapsulando la arquitectura detrás del sistema.

El API Gateway, por otra parte, desacopla los clientes de los microservicios, de manera que éstos pueden evolucionar con un impacto mínimo en aquellos, ya que su uso es transparente.

La mayor ventaja de un esquema de comunicación basado en API Gateway es que encapsula la estructura interna de la aplicación. En lugar de invocar a servicios específicos, los clientes simplemente se comunican con la pasarela, que proporciona a cada tipo de cliente un API específica, reduciendo así la latencia entre la aplicación y el cliente y, además, simplificando el código del cliente.

Sin embargo, el API Gateway, por su criticidad, es un componente de alta disponibilidad más qué debería ser desarrollado, desplegado y gestionado.

**Backend for Frontend**

Es una variante del patrón API Gateway. 

En lugar de un único punto de entrada para los clientes, proporciona múltiples puertas de enlace basadas en el cliente. 

El propósito es proporcionar API personalizadas de acuerdo con las necesidades del cliente, eliminando muchos problemas causados por la creación de API genéricas para todos los clientes.

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