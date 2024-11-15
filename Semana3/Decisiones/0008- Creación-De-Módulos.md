# Creación-De-Módulos

* Status: accepted
* Deciders: Jesús, Icíar
* Date: 2024-11-11

## Context and Problem Statement

Vamos a dividir la lógica de negocio en los siguientes módulos: Clientes, Pedidos, Repartos y Rutas, Estadísticas y Pago. Esto es necesario para poder dividir las responsabilidades en diferentes unidades funcionales.

## Decision Drivers

* RF-01.1 División en módulos

## Considered Options

* 0008-1- Crear los respectivos módulos

## Decision Outcome

Chosen option: "Crear los respectivos módulos", because queremos tener unidades autónomas para conseguir una arquitectura basada en microservicios.

### Positive Consequences

* Flexibilidad en la arquitectura, ya que cada módulo se especializa en una función independiente que permite abstraerse de la complejidad del resto de modulos. 
* Mayor escalabilidad, ya que podemos escalar los módulos independientemente del resto.
* Reusabilidad: Los módulos bien diseñados pueden reutilizarse en otros proyectos.

### Negative Consequences

* Mayor complejidad inicial: La creación de una arquitectura modular requiere una planificación cuidadosa y puede aumentar la complejidad inicial del proyecto.
* Mayor esfuerzo en la comunicación entre módulos: Es necesario definir interfaces claras y precisas entre los módulos para garantizar una comunicación efectiva.

## Pros and Cons of the Options

### 0008-1- Crear los respectivos módulos

Crear los módulos Clientes, Pedidos, Repartos y Rutas, Estadísticas y Pago.

* Good, because Reducción del acoplamiento: Al separar la lógica en módulos independientes, se minimizan las dependencias entre diferentes partes del sistema.
* Good, because Alta cohesión: Cada módulo se centra en una única responsabilidad.
* Good, because Modularidad: La arquitectura modular permite añadir o reemplazar módulos fácilmente.
* Good, because Mejor gestión de dependencias: Cada módulo puede manejar sus propias dependencias externas.
* Bad, because Complejidad en la integración.
* Bad, because Mayor esfuerzo en la gestión de dependencias.