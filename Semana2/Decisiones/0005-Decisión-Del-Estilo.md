# Decisión-Del-Estilo

* Status: accepted
* Deciders: Jesus, Iciar
* Date: 2024-11-06

## Context and Problem Statement

En nuestro proyecto de desarrollo de software, hemos decidido usar una arquitectura cliente-servidor, que se basa en la comunicación HTTP. Esto permite que los usuarios se conecten independientemente del dispositivo y nos abre la puerta a implementar REST en el futuro y dividir la arquitectura en microservicios.

## Decision Drivers

* RF-01 Arquitectura basada en microservicios
* RF-02 Arquitectura HTTP/REST

## Considered Options

* Estilo Cliente-Servidor

## Decision Outcome

Chosen option: "Estilo Cliente-Servidor", because es el estilo por defecto de las arquitecturas que ofrecen servicios a través de internet.

### Positive Consequences

* a arquitectura cliente-servidor simplifica el mantenimiento al centralizar la lógica y los datos en el servidor.
* La arquitectura cliente-servidor facilita la modularidad al permitir dividir la aplicación en módulos o microservicios.
* La arquitectura cliente-servidor facilita la implementación de APIs y la exposición de servicios a través de protocolos como REST.

### Negative Consequences

* La arquitectura cliente-servidor presenta un punto único de fallo al depender de un servidor centralizado que puede afectar la disponibilidad.
* La arquitectura cliente-servidor requiere una gestión de seguridad más compleja al centralizar datos y lógica en el servidor.

## Pros and Cons of the Options

### Estilo Cliente-Servidor

El modelo cliente-servidor es una arquitectura donde los clientes solicitan servicios o recursos a servidores que los procesan y responden.

* Good, because Separación de responsabilidades entre cliente y servidor.
* Good, because Datos y recursos centralizados
* Good, because Los clientes pueden conectarse desde diferentes plataformas
* Good, because Facilita la implementación de protocolos como REST, que son ampliamente usados en sistemas distribuidos y API.
* Bad, because Puede haber retrasos en las interacciones debido a la latencia entre el cliente y el servidor.
* Bad, because El sistema depende de la disponibilidad y el rendimiento del servidor; si falla, los clientes quedan inoperativos.
* Bad, because Los servidores deben ser más seguros debido a la concentración de datos y lógica, lo que requiere medidas de protección avanzadas.
