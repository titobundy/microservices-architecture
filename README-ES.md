# Microservices Architecture

## Definition

### Service

Según OASIS (Organization for the Advancement of Structured Information Standards), se entiende por servicio “un mecanismo que permite el acceso a una o más capacidades, donde el acceso es través de una interfaz”

Por lo tanto, un servicio es una funcionalidad o un conjunto de funcionalidades de software, con el objetivo de que pueda ser reutilizado por distintos clientes con propósitos distintos, junto con las políticas que deben controlar su uso.

https://en.wikipedia.org/wiki/Service_(systems_architecture)

Entonces si un servicio es un mecanismo que permite el acceso a una o más operaciones ejecutables públicamente, entonces un microservicio es un servicio con una interfaz pública "micro". Donde proporciona la menor cantidad posible de operaciones públicas.

---

### Microservices

Martin Fowlers

*"The microservice architectural style is an approach to developing a single application as a suite of small services, each running in its own process and communicating with lightweight mechanisms, often an HTTP or gRPC API."*

*"La arquitectura de microservicios son un enfoque para desarrollar una sola aplicación como un conjunto de pequeños servicios, cada uno ejecutándose en su propio proceso y comunicándose con mecanismos ligeros, a menudo una API a través de HTTP.*

Sam Newman

*"Microservices are small, autonomous services that work together modelled around a business domain."*

*"Microservicios son pequeños servicios, autonomos que trabajan juntos (en forma colaborativa) y son modelados alrededor del dominio de negocio."*

---

### Representation

Se estructura una aplicación como una colección de pequeños servicios autónomos, organizados en función de las capacidades del negocio, que es aquello que contribuye o aporta valor al negocio para lograr sus objetivos.

Como vemos, cada servicio es auto-contenido e implementa una única capacidad de negogio.

---

## Why Microservices ?

El concepto de Microservicios surgió de una necesidad de entregar soluciones a los problemas que tenian las arquitecturas monolíticas.

Nos referimos a una arquitectura como monolítica si toda la aplicación está integrada en un solo ejecutable/paquete, implementada todo o nada, usando uno o muy pocos almacenes de datos.

---

### Monolithic Architecture

Una aplicación monolítica tiene la mayor parte de su funcionalidad dentro de un solo proceso que comúnmente se compone de librerías.

- Single codebase (Codigo de programacion para crear aplicaciones)
- Single process
- Single host
- Single database
- Consistent technology

Estas aplicaciones suelen utilizar arquitecturas escalonadas (por ejemplo, una arquitectura N-capas, donde tenemos la capa presentación, lógica empresarial, capa de acceso a datos).

(*) Codebase es el código fuente completo requerido para mantener la funcionalidad de la aplicación, o la implementación de ese código fuente.

---

**Benefits**

- Fácil comenzar a desarrollar.
- Fácil encontrar cosas debido a que tenemos una unica base de codigo.
- Fácil de depurar y realizar pruebas.
- Despliegue de solo una aplicación.
- Menos responsabilidades transversales, tales como logging, manejo de caché, monitoreo de desempeño.

---

**Limitations**

- **Inflexible**: Es extremadamente problemático introducir una nueva tecnología en una aplicación monolítica porque entonces toda la aplicación tiene que ser reescrita.

- **(Pobre) No confiable**: Un bug/error en algún punto del sistema puede potencialmente afectar a todo el sistema, debido a que todos los componentes estan interconectados (Resiliency).

- **No escalable**:  No se pueden escalar componentes de forma independiente, solo toda la aplicación. En este sentido el escalamiento horizontal se realiza clonando la aplicación en varios servidores/máquinas virtuales/contenedores, donde ejecutamos varias instancias de la aplicación detrás de un equilibrador de carga. El escalamiento vertical tiene limitaciones y es más costoso.

- **Bloquea el desarrollo continuo**: Limita la agilidad en el sentido de que muchas características de las aplicaciones no se pueden construir e implementar al mismo tiempo (varios equipos). En dicho sentido, se reduce la agilidad del equipo y la frecuencia de nuevas entregas. Por otro lado cualquier cambio por pequeño que sea requiere el re-despliegue de toda la aplicación. 

- **Desarrollo lento**: El desarrollo en aplicaciones monolíticas requiere mucho tiempo para construirse, ya que todas y cada una de las funciones deben construirse una tras otra, las reparaciones son lentas y costosas. Por otro lado tenemos un solo gran código fuente, lo que sobrecarga los IDES y ralentiza los tiempos de inicio de la aplicación.

- **No apto para aplicaciones complejas**: Son un reto de crecimiento y el cambio. Si la aplicación crece en complejidad, lo hará también en líneas de código y en el número de características, es más riesgoso y costoso efectuar cambios, debido a esto se comienzan a crear dependencias estrechamente acopladas.

---

**Why Microservices?**

La creación de microservicios nos brinda la oportunidad de abordar la complejidad del software y entregar más rápido; si (y es un gran si) construimos nuestros servicios correctamente: eligiendo la tecnología, las interfaces y los patrones de integración más adecuados.

Los microservicios son una forma de dividir las aplicaciones, para que podamos entregar los componentes por separado, experimentar con distintos stacks tecnologicos y crear límites claros.

Pero crear microservicios no es una tarea sencilla. Se deben considerar muchas cosas, por ejemplo:

- ¿cómo (y dónde)  dividir los servicios?
- ¿cómo se comunican entre sí (integración) y qué datos compartirán?.

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

- **Desarrollo independiente:** Todos los microservicios se pueden desarrollar fácilmente basados en su funcionalidad individual.

- **Despliegue independiente:** Permite a un equipo desplegar sus servicio sin tener que coordinarse con otros equipos.

- **Tolerancia a fallas/Resiliencia:** Un error solo afectará al servicio en el que ocurre, pero no afectará toda la aplicación.

- **Stack de tecnología mixta:** Permiten adaptarse fácilmente y aprovechar las últimas tecnologías emergentes. Se pueden usar diferentes lenguajes y bases de datos para construir diferentes servicios de la misma aplicación.

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

- **Complejidad operativa:** Cada servicio es simple, pero como un todo el sistema es más complejo. La gestión de múltiples bases de datos y transacciones puede ser realmente engorrosa.
 
- **Problemas de red y latencia:** Debido a que los microservicios utilizan un tipo de comunicación inter-service (a través de la red) las peticiones pueden fallar y provocar un retraso, debemos fortalecer la tolerancia a fallas, mitigar la latencia de la red y lidiar con una variedad de formatos de mensajes, así como con el balance de carga.

- **Integridad de los datos:** Mantener una consistencia sólida es extremadamente difícil para un sistema distribuido. Cada microservicio dentro del sistema es responsable de su propia base de datos o algún otro almacenamiento. Esto crea el potencial de tener datos duplicados a los largo de los multiples servicios. La solución es establecer los limites de los servicios en los lugares correctos y siempre asegurar que cualquier dato en particular tenga una sola fuente de verdad.

---

## Principles of Microservices (Sam Newman)

Sam Newman, durante el trabajo que ha realizado con muchas empresas que implementan microservicios, ha establecido una lista de principios que han ayudado a dichas empresas, a construir microservicios exitosos.

Los principios de arquitectura _existen por una razón_, que es _conseguir los objetivos estrategicos de la organizacion_. Por otro lado los practicas y patrones de arquitectura son el mecanismo mediante el cual implementamos estos principios.

La razon de estos principios es lograr construir pequeños servicios que sean autonomos.

- **Modeled Around Business Domain:** Proporcionan APIs más estable. Los servicios deben representar un contexto delimitado dentro del dominio. 
La historia ha demostrado que las interfaces estructuradas en torno a contextos delimitados por negocios son más estables que aquellas estructuradas en torno a conceptos técnicos. En ese sentido, DDD es una herramienta para la division correcta.

- **Culture of Automatization:** Permite la escalabilidad. Los microservicios agregan mucha complejidad, adoptar una cultura de automatización es una forma clave de abordar este problema. Las prácticas de desarrollo tales como: la automatización de pruebas, despliegue automatizado y la administración de la configuración, permiten que el sistema escale de manera más eficiente y también mejore la coordinación de servicios. Normalmente se adopta un enfoque Devops con CI/CD.

- **Hide Implementation Details:** Permite que un servicio evolucione independientemente de otro. Para maximizar la capacidad de un servicio de evolucionar independientemente de cualquier otro, _es vital que ocultemos los detalles de implementación, esto es esencial para mantener un bajo acoplamiento entre los servicios que interactúan en una aplicación_. (Database per service)

- **Decentralise All the Things:** Permite agilidad. Este principio se basa en el requisito de que los servicios individuales deben desarrollarse, gestionarse y mantenerse de forma autónoma. Es recomendado delegar la toma de decisiones y control a los equipos dueños de los microservicios.

- **Deploy Independently:** Permite agilidad y disponibilidad. Es uno de los principios mas importantes, debería poder cambiar un servicio y desplegarlo sin tener que realizar cambios en ningún otro servicio.

- **Consumer First:** Proporciona servicios útiles. Los servicios existen para ser llamados, por lo que deben construirse de afuera hacia adentro en lugar de adentro hacia afuera.

- **Isolate Failure:** Permite disponibilidad. La falla en un servicio no debería tener un efecto en cascada. (circuit breakers)

- **Highly Observable:** Proporciona mantenibilidad. Una parte importante de la gestión del ciclo de vida de las aplicaciones es el monitoreo. En el caso de los microservicios, debido a su naturaleza distribuida, es necesario proporcionar una solución de monitoreo que permita registrar el funcionamiento y el rendimiento del sistema (logs, recursos, trafico, metricas, etc).

---

## Design Patterns for Microservices

La aplicación de los principios conlleva varios desafíos y problemas, problemas que son comunes para muchas soluciones. Por lo que podemos superar estos desafios con el uso de patrones de diseño adecuados.

Podemos categorizar los patrones de microservicios en 5 tipos, cada uno con varios patrones.

---

### Decomposition Patterns

Para desarrollar una aplicación grande y compleja usando la arquitectura de microservicios, necesitamos descomponer la aplicación en un conjunto de microservicios débilmente acoplados de una manera detallada y razonable. **_El objetivo de la arquitectura de microservicios es acelerar el desarrollo de software logrando una entrega/despliegue continuo._**

Una de las claves para ello es mantener servicios desacoplados, independientes de forma tal que se facilite su puesta en operación y reducir su tiempo de entrada al mercado (time-to-market)

---

#### By Business Capability

En este patrón se definen y modelan los microservicios acorde a las capacidades empresariales del negocio, enfocado en los elementos que aportan valor, por ejemplo, en una tienda online, existe comúnmente un área de productos, inventario, entrega, pedidos, entre otras.

Llevando esto a capacidades del negocio puede traducirse en:
	- Gestión de productos.
	- Gestión de inventario.
	- Gestión de pedidos.
	- Gestión de entregas.	

Existe una relación entre el negocio y los posibles microservicios que podemos crear para soportar la automatización.

---

#### By Subdomain

El enfoque de descomposición por subdominios se basa en los principios de Domain Driven Design (DDD), descrito por Eric Evans.

DDD propone un enfoque para alinear a los expertos del dominio y desarrolladores en base a objetivos claros, con un lenguaje común y centrado en el negocio.

Se proponen tres ejes principales para guiar el desarrollo:

1. Centrarse en el dominio principal.
2. Estructurar el diseño en un modelo de dominio.
3. Realizar un desarrollo iterativo para la mejora continua en estrecha colaboración entre los expertos del negocio y el equipo de desarrollo, usando un lenguaje común.

Conceptos:
- El dominio consta de varios subdominios. 
- Cada subdominio corresponde a una parte diferente del negocio.
- Cada subdominio tiene un modelo y el alcance de ese modelo se denomina contexto delimitado (bounded context).
- Los microservicios se desarrollan en torno a este contexto acotado.

----

#### Strangler Fig Pattern

A partir de la evolución de las arquitecturas, y especialmente con la llegada de los microservicios muchas aplicaciones inician un proceso de migración; el tamaño de los monolitos hace que ese proceso sea lento y gradual, surgiendo la necesidad de lograr una convivencia entre el viejo sistema y los nuevos servicios que se
van creando paulatinamente.

El patrón de estrangulación permite sustituir una aplicación heredada de forma gradual y con menos riesgos, reemplazando piezas específicas de funcionalidad por nuevas aplicaciones y servicios. 

Para lograr que el sistema legado funcione y cada uno de los microservicios que se van creando realice su tarea particular es necesario definir un mecanismo que sirva de fachada para las aplicaciones clientes y dirija el tráfico de las operaciones al ente correspondiente.

La fachada que se crea implementa una capa transparente para los clientes.

---

### Microservices Communications

El cliente y los servicios pueden comunicarse a través de muchos tipos diferentes de comunicación, cada uno destinado a un escenario y unos objetivos distintos. Inicialmente, esos tipos de comunicaciones se pueden clasificar en dos ejes.

---

#### Synchronous communication

La comunicación síncrona es la solución más sencilla cuando se intenta la comunicación entre cliente y servicios o entre servicios. Funciona como una llamada telefónica, el cliente envía una solicitud y espera una respuesta.

En el procesamiento sincrónico, un cliente envía una solicitud al servidor y espera a que el servidor complete su trabajo y envíe la respuesta antes de que el cliente pueda reanudar su trabajo.

Es por ello que se le denomina solicitud de bloqueante, ya que el cliente no puede realizar ningún otro trabajo hasta que se recibe una respuesta.

Protocolos: Se usa principalmente con los protocolos HTPP(S), API Restful, GraphQL, gRCP (Http 2 los servicios son definidos usando un protocolo de buffer).

---

#### Asynchronous communication

Es lo opuesto al procesamiento sincrono, aquí el cliente del mensaje no espera ninguna respuesta después de enviar una solicitud al servidor y continúa haciendo cualquier otro trabajo.

A este proceso se le conoce como no bloqueante, ya que el hilo de ejecución del cliente no está bloqueado. Esto permite que los sistemas escalen ya que se puede realizar más trabajo en un período de tiempo determinado.

La comunicación mediante mensajería asíncrona se usa, fundamentalmente, para la comunicación entre los distintos microservicios a través de un intermediario de mensajes o bróker, de tal manera que los productores de mensajes van colocándolos en una cola distribuida de la cual los consumidores van recuperando. De este modo, productor y consumidor quedan totalmente desacoplados.

El protocolo más popular para estas comunicaciones asíncronas es AMQP (Protocolo avanzado de cola de mensajes). Algunos ejemplos: Kafka y RabbitMQ.

---

#### Api Gateway Pattern


A diferencia de una arquitectura monolitica, hemos distribuido las funcionalidades en microservicios independientes y, con ello, la lógica y el acceso a los datos y, por tanto, dispersado el punto de entrada a la aplicación.

Las arquitecturas de microservicios se caracterizan por optar por mecanismos de comunicación ligeros y simples llamados _dumb pipes_ (tuberías tontas), es decir, que es en los puntos finales donde reside toda la inteligencia y no debe invertirse esfuerzo en complicados mecanismos de comunicación que no aportan ningún valor al sistema y sí que supone un incremento considerable de la complejidad.

---

**Direct Communication**

En teoría, un cliente puede lanzar peticiones directas a cualquiera de los microservicios, ya que cada uno de ellos expone un endpoint (punto de acceso) público. Sin embargo esto trae problemas como la variedad de clientes con distintas necesidades y capacidades, protocolos no orientados a la web (AMQP mensajeria), se transfiere a los clientes el administrar multiples llamadas, provocando un incremento de latencia, además de complejidad adicional en el lado UI.

La comunicación directa entre el cliente y los microservicios podría ser suficiente para una pequeña aplicación basada en esta arquitectura. Sin embargo, cuando creamos aplicaciones basadas en microservicios grandes y complejas y, sobre todo, cuando las aplicaciones cliente son aplicaciones móviles remotas o aplicaciones web SPA, este enfoque se enfrenta a algunos problemas.

- ¿Cómo pueden las aplicaciones cliente minimizar el número de solicitudes al back-end y reducir el exceso de comunicación con varios microservicios?

- ¿Cómo se pueden controlar cuestiones transversales como la autorización, las transformaciones de datos?

- ¿Cómo pueden las aplicaciones cliente comunicarse con servicios que usan protocolos no compatible con Internet?

- ¿Cómo se puede dar forma a una fachada creada especialmente para las aplicaciones móviles?

Para resolver éste y otros problemas relacionados se prefiere un esquema en el que un intermediario central se encargue de adaptar las llamadas a los microservicios y sus respuestas a distintos tipos de clientes, proporcionando esta API de la granularidad adecuada. Este intermediario es lo que se conoce como API Gateway.

---

**API Gateway**

Un API Gateway es un punto de acceso unico para todos los clientes. La mayor ventaja de este esquema es que encapsula la estructura interna de la aplicación.  

En lugar de invocar a servicios específicos, los clientes simplemente se comunican a través de la pasarela, reduciendo así la latencia entre la aplicación y el cliente, y además desacopla los clientes de los microservicios, de manera que éstos pueden evolucionar con un impacto mínimo en aquellos, ya que su uso es transparente.

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
