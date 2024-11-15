# Selección-Del-Patrón-Para-La-Selección-Del-Algoritmo-De-Optimización

* Status: Accepted
* Deciders: Icíar, Jesús 
* Date: 2024-11-14

## Context and Problem Statement

El sistema debe elegir entre dos algoritmos de optimización del reparto que se seleccionan en función de la demora.
Esta dinámica de selección debe ser flexible y fácil de mantener, asegurando una integración sencilla con el resto del sistema.

## Decision Drivers

* RF-06.2 Selección del algoritmo de optimización

## Considered Options

* 0014-1-Patrón-Strategy
* 0014-2-Patrón-Real-Time-Algorithm-Selection
* 0014-3-Patrón-Balancing

## Decision Outcome

Chosen option: "0014-1-Patrón-Strategy", because facilita la selección de algoritmos de optimización sin alterar la lógica principal del sistema.

### Positive Consequences

* Permite intercambiar los algoritmos de optimización de manera dinámica y eficiente.
* Es fácil agregar o modificar algoritmos en el futuro sin afectar el resto del sistema.

### Negative Consequences

* Si el número de algoritmos crece significativamente podría haber una sobrecarga de objetos.
* Cuando el número de algoritmos es bajo y estos rara vez cambian, Strategy podría añadir complejidad sin grandes beneficios.

## Pros and Cons of the Options

### 0014-1-Patrón-Strategy

Es un patrón de diseño de comportamiento que permite definir una familia de algoritmos, encapsular cada uno en su propia clase y hacer que sus instancias sean intercambiables.

* Good, because permite la selección de los algoritmos sin necesidad de cambiar la lógica del resto del sistema.
* Good, because mejora la extensibilidad y el mantenimiento del sistema al encapsular los algoritmos en clases separadas.
* Bad, because puede requerir una sobrecarga adicional para los objetos de estrategia.
* Bad, because si hay pocos algoritmos que rara vez cambian, el patrón Strategy puede añadir complejidad innecesaria.

### 0014-2-Patrón-Real-Time-Algorithm-Selection

Se utiliza en sistemas de tiempo real que necesitan elegir dinámicamente entre varios algoritmos o enfoques para resolver un problema en función de las condiciones actuales del sistema.

* Good, because puede integrarse fácilmente con la arquitectura de microservicios existente.
* Good, because permite tener un control directo sobre cómo y cuándo se realiza la selección del algoritmo.
* Bad, because puede no ofrecer el mejor rendimiento si no se configura correctamente.
* Bad, because no es tan flexible ni tan extensible como otros patrones ya que integra la lógica de selección directamente en el sistema.

### 0014-3-Patrón-Balancing

Es una técnica utilizada para distribuir la carga de trabajo entre varios servidores con el fin de mejorar la capacidad de respuesta, la fiabilidad y la escalabilidad. En este contexto, se puede utilizar para seleccionar el algoritmo según el retraso del camión.

* Good, because puede manejar la selección de algoritmos en tiempo real, mejorando la capacidad de respuesta.
* Good, because puede mejorar la escalabilidad.
* Bad, because puede introducir complejidad adicional.
* Bad, because puede requerir una configuración cuidadosa.

## Links

* https://refactoring.guru/es/design-patterns/strategyc