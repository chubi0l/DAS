# Decisión-De-Los-Componentes-Del-Módulo-De-Pago

* Status: Accepted
* Deciders: Icíar, Jesús 
* Date: 2024-11-14

## Context and Problem Statement

Se necesita que el sistema incluya un componente de pago para poder procesar transacciones.

## Decision Drivers

* RF-09 Módulo de Pago
* RD-02 Pasarela de pago STRIPE 

## Considered Options

* 0015-1-Añadir-Un-Componente

## Decision Outcome

Chosen option: "0014-1-Añadir-Un-Componente", because hay que integrar los pagos en el sistema mediante el componente STRIPE.

### Positive Consequences

* Añadir el componente STRIPE va a permitir aprovechar soluciones especializadas, mejorando la eficiencia general del sistema.
* Al integrar el componente STRIPE, se mantiene el sistema modular, lo que facilita la actualización o sustitución del componente sin afectar al resto del sistema.

### Negative Consequences

* Si el componente no se integra correctamente con el resto del sistema, podría haber problemas de compatibilidad o rendimiento.
* Integrar el componente STRIPE puede aumentar la complejidad del sistema, especialmente porque depende de servicios externos.

## Pros and Cons of the Options

### 0015-1-Añadir-Un-Componente

* Good, because la integración con el sistema es rápida y sencilla.
* Good, because facilita el desacoplamiento del sistema.
* Bad, because introduce complejidad adicional y puede hacer que el sistema sea más difícil de entender o gestionar.
* Bad, because incrementa la dependencia de servicios externos.

## Links

* https://stripe.com/es