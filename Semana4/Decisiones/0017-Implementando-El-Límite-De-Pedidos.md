# Impelementando-El-Límite-De-Pedidos

* Status: accepted
* Deciders: Iciar, Jesús
* Date: 2024-11-19

## Context and Problem Statement

En una arquitectura de microservicios, se está diseñando un sistema de gestión de pedidos para una empresa de productos alimenticios que requiere alta disponibilidad y resiliencia. El sistema maneja módulos críticos y semi-críticos, como el de órdenes, donde es necesario gestionar los intentos fallidos al realizar pedidos, garantizando una experiencia de usuario fluida pese a errores transitorios en la red o en los servicios.

## Decision Drivers

* RF 04.1	Límite de intentos de pedido

## Considered Options

* 0017-1-Patrón Retry
* 0017-2-Patrón Circuit Breaker

## Decision Outcome

Chosen option: "0017-2-Patrón Circuit Breaker", because este patrón proporciona un mecanismo más sofisticado para manejar fallos en cascada y prevenir la sobrecarga del sistema, mejorando la resiliencia general de la aplicación.

### Positive Consequences

* El Circuit Breaker aísla las fallos y evita que se propaguen por todo el sistema, protegiendo los servicios críticos
* Al detener las solicitudes a un servicio que falla, el Circuit Breaker permite que el resto de la aplicación siga funcionando, mejorando la disponibilidad general.
* El Circuit Breaker proporciona información sobre el estado de los servicios, lo que facilita la identificación y resolución de problemas.

### Negative Consequences

*  Requiere una lógica adicional para monitorear el estado del circuito y gestionar las transiciones entre estados.
* La verificación del estado del circuito puede agregar una pequeña latencia a las solicitudes.

## Pros and Cons of the Options

### 0017-1-Patrón Retry

El patrón Retry es una estrategia en arquitectura de microservicios que permite a un sistema reintentar la ejecución de una operación que falló temporalmente debido a errores transitorios o intermitentes, como fallos en la red o congestión del sistema. 

Para implementar el patrón Retry en la arquitectura de microservicios para el sistema de órdenes, podemos configurar un mecanismo que reintente el procesamiento de una orden en caso de fallo, hasta un máximo de tres intentos. En este caso, el proceso de ordenamiento podría utilizar un intermediario, como una cola de mensajes o un componente de orquestación, que gestiona los intentos y aplica una lógica de reintentos con un temporizador de espera (back-off) entre intentos. Una vez alcanzado el límite de tres intentos, se activará una política de bloqueo temporal, prohibiendo la creación de nuevas órdenes para el cliente afectado.

El flujo sería el siguiente:

1. El cliente inicia un pedido.
2. Si el pedido falla, el sistema lo reintenta automáticamente (hasta tres veces).
3. Si el pedido sigue fallando, el sistema aplica un bloqueo temporal, prohibiendo nuevos intentos hasta que pase el tiempo especificado.
El bloqueo temporal puede integrarse con un mecanismo de caché o una base de datos para gestionar el estado de bloqueo de los clientes.

* Good, because Resiliencia ante Fallos Temporales: Permite que el sistema gestione errores transitorios sin intervención manual, aumentando la disponibilidad del servicio de órdenes.
* Good, because Manejo Controlado de Errores: Reduce la cantidad de errores presentados al usuario final, ya que reintenta automáticamente en caso de fallos.
* Good, because Alineación con una Arquitectura Distribuida: Al implementar Retry, el sistema puede seguir funcionando de manera independiente y modular, alineándose con el principio de autonomía de microservicios.
* Bad, because Incremento en el Uso de Recursos: Los reintentos pueden sobrecargar el sistema o las bases de datos si el volumen de órdenes es alto
* Bad, because Complejidad en la Implementación y Mantenimiento: La implementación del patrón Retry agrega complejidad al código

### 0017-2-Patrón Circuit Breaker

El patrón Circuit Breaker actúa como un interruptor automático que monitorea la salud de un servicio. Si el servicio falla repetidamente, el Circuit Breaker se "abre" e impide que se envíen más solicitudes al servicio fallido, evitando así una sobrecarga del sistema y permitiendo que se recupere. Después de un tiempo, el Circuit Breaker pasa a un estado "semiabierto" para probar si el servicio se ha recuperado.

Para implementar el Circuit Breaker en el sistema de órdenes, se puede utilizar una librería como Hystrix o Resilience4j. El Circuit Breaker monitorearía las llamadas al servicio de órdenes y, en caso de fallos consecutivos, se abriría el circuito, impidiendo nuevas solicitudes. Durante este tiempo, se podría mostrar un mensaje al usuario indicando que el servicio no está disponible temporalmente.

* Good, because Aísla los fallos y evita que afecten a otros servicios.
* Good, because Permite que el sistema se recupere automáticamente de los fallos.
* Good, because roporciona información sobre la salud del servicio.
* Bad, because Requiere configurar los umbrales y tiempos de espera adecuados.
