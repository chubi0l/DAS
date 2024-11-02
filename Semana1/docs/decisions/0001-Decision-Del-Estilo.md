# Decisión-del-estilo

* Status: proposed
* Deciders: Jesus, Iciar
* Date: 2024-11-02

## Context and Problem Statement

En el contexto de nuestro proyecto de desarrollo software, hemos decidido adoptar un estilo REST para permitir la comunicación de los clientes con los servicios de la aplicación, y para emjorar la escalabilidad de nuestro sistema.

## Decision Drivers

* RF-01 Arquitectura basada en microservicios
* RF-02 Arquitectura HTTP/REST
* RF-03 Escalabilidad
* RD-05 Acceso desde dispositivos Móviles y PC

## Considered Options

* 0001 Estilo Cliente - Servidor
* 0001-2 Estilo REST

## Decision Outcome

Chosen option: "0001-2 Estilo REST", because la naturaleza stateless del estilo REST nos va a facilitar cumplir con los requisitos propuestos.

### Positive Consequences

* Facilidad en el escalado
* Facilidad en la conexión desde distintos tipos de dispositivos

### Negative Consequences

* Mayor carga en el servidor al realizar un mayor número de peticiones
* Mayor dificultad en el manejo de sesiones

## Pros and Cons of the Options

### 0001 Estilo Cliente

El modelo cliente-servidor es una arquitectura donde los clientes solicitan servicios o recursos a servidores que los procesan y responden. El modelo cliente-servidor permite que el servidor mantenga el estado de la sesión, facilitando interacciones
contextuales entre peticiones.

* Good, because Mantenimiento del estado de la sesión
* Good, because Menor restricción en las operaciones que se pueden realizar
* Good, because Datos y recursos centralizados
* Good, because Separación de responsabilidades entre cliente y servidor.
* Good, because Posibilidad de agregar más servidores para soportar más clientes.
* Bad, because Escalabilidad más complicada debido a la obligación de mantener los estados de las sesiones.
* Bad, because Menor cacheabilidad porque no está diseñado para aprovechar el almacenamiento en caché de las respuestas.
* Bad, because Heterogeneidad en la interfaz al no limitar los tipos de operaciones
* Bad, because La caída del servidor afecta a todos los clientes.
* Bad, because Puede haber retrasos en las interacciones debido a la latencia entre el cliente y el servidor.

### 0001-2 Estilo REST

El estilo REST es un modelo de arquitectura para aplicaciones web que se basa en el intercambio de recursos a través de peticiones HTTP simples y sin estado. En REST, los clientes solicitan recursos específicos mediante verbos como GET, POST, PUT y DELETE, y los servidores responden con datos en un formato estándar, como JSON o XML.

* Good, because Independencia entre el cliente y el servidor
* Good, because Independencia de la plataforma, permitiendo que diferentes sistemas se comuniquen fácilmente.
* Good, because Facilidad para la esacalabilidad
* Good, because Uniformidad de la interfaz al limitar las operaciones
* Good, because Almacenamiento en caché de la respuesta, reduciendo la carga y optimizando el rendimiento.
* Good, because Al ser stateless, permite escalar fácilmente, ya que cada solicitud es independiente y no depende del estado anterior.
* Good, because Reducción del acoplamiento
* Good, because Reutilización de los recursos
* Good, because Testeabilidad de los recursos
* Bad, because La naturaleza stateless puede complicar el manejo de sesiones o transacciones que requieren estado.
* Bad, because Sobrecarga de red al necesitar toda la información en cada llamada debido a su naturaleza stateless
* Bad, because Más posibles puntos de error
* Bad, because Mayor dificultad en el gobierno de los servicios

## Links

* https://aws.amazon.com/es/what-is/restful-api/
* https://reactiveprogramming.io/blog/es/estilos-arquitectonicos/rest
* https://www.redhat.com/es/topics/api/what-is-a-rest-api
* https://es.wikipedia.org/wiki/Cliente-servidor
