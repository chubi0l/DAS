# Impelementando-El-Procesado-De-Pedidos

* Status: accepted
* Deciders: Icíar, Jesús
* Date: 2024-11-13

## Context and Problem Statement

Necesitamos crear una forma flexible y escalable de procesar pedidos. El módulo de procesamiento de pedidos requiere un proceso en tres fases: preprocesamiento, autorización y aceptación.

## Decision Drivers

* RF 04.2	Procesamiento del pedido

## Considered Options

* 0012-1- Event Sourcing
* 0012-2- Chain of Responsability

## Decision Outcome

Chosen option: "0012-2- Chain of Responsability", because este patrón nos garantiza un flujo de trabajo estricto y un control riguroso sobre cada fase del pedido.

### Positive Consequences

* Escalabilidad y flexibilidad: Como las clases pueden escalarse de manera independiente, la arquitectura puede adaptarse a cambios en el tráfico sin sobrecargar el sistema.
* Resiliencia: Cada fase del proceso está desacoplada, lo que significa que si una fase falla, no afectará directamente a las otras fases.

### Negative Consequences

* Mayor complejidad de la gestión de fallos en cada fase.
* Sobrecarga de red.

## Pros and Cons of the Options

### 0012-1- Event Sourcing

Implementaremos el patrón de Event Sourcing para el procesamiento de pedidos, creando un almacén de eventos que contenga un registro de todos los eventos relacionados con el pedido, incluyendo eventos de preprocesamiento, autorización y aceptación. El sistema utilizará estos eventos para determinar el estado actual del pedido y para rastrear el progreso del pedido a través de las tres fases.

* Good, because El patrón de Event Sourcing proporciona una forma flexible y escalable de procesar pedidos.
* Good, because El patrón proporciona un historial claro de todos los cambios realizados en el estado del pedido.
* Good, because El sistema puede manejar un gran volumen de pedidos y eventos.
* Bad, because Puede agregar complejidad al sistema.
* Bad, because Puede afectar el rendimiento, especialmente si el almacén de eventos no está correctamente indexado y es consultable.
* Bad, because El sistema puede requerir recursos adicionales (por ejemplo, hardware o personal) para implementarlo y mantenerlo.

### 0012-2- Chain of Responsability

El procesamiento de cada pedido debe pasar por tres fases consecutivas: preprocesamiento, autorización y aceptación. Estas fases deben completarse en orden, y el proceso no puede avanzar a la siguiente fase a menos que la fase anterior haya sido procesada correctamente. Esto sugiere que el sistema debe garantizar una secuencia estricta y controlada de operaciones, donde cada fase depende de la correcta ejecución de la anterior. Por lo que utilizaríamos las siguioentes clases:
- Preprocesamiento: Esta clase se encargaría de la validación preliminar del pedido (verificación de la existencia de productos, disponibilidad en inventario, validación de datos del cliente, etc.). Podría requerir consultas a las bases de datos de "Clientes" y "Pedidos".
- Autorización: Esta clase gestionaría la lógica de autorización del pedido, que podría implicar la validación de pagos, la verificación de la solvencia del cliente o el proceso de verificación contra servicios externos como el sistema de pago (STRIPE). Este componente podría integrarse con sistemas externos o servicios de terceros.
- Aceptación: Este microservicio se encargaría de finalizar el proceso de pedido, asignando el pedido a un lote de entrega, confirmando la disponibilidad del producto o la programación de la entrega, y cerrando el ciclo de pedido.

* Good, because Las fases del procesamiento de pedidos son independientes y podrían actualizarse, desplegarse o modificarse sin afectar a otras fases.
* Good, because Si una fase falla (por ejemplo, la autorización del pago), el sistema puede manejar el error de forma aislada y no afectar las fases anteriores o posteriores.
* Good, because Cada fase del procesamiento de pedidos podría escalarse independientemente según la carga.
* Bad, because Mayor complejidad: Como el proceso de pedido involucra múltiples clases, gestionar la consistencia de los datos y las transacciones distribuidas puede ser complejo.
* Bad, because Al tener múltiples clases, cada una de ellas puede generar sobrecarga en la comunicación entre los mismos.