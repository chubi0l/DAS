# Selección-De-Clases-Del-Módulo-De-Reparto-Y-Rutas

* Status: Accepted
* Deciders: Icíar, Jesús 
* Date: 2024-11-14

## Context and Problem Statement

Se necesita desarrollar esta funcionalidad en una o dos clases para cumplir con los requisitos del sistema.
La decisión que se tome debe cumplir con los requisitos de simplicidad, escalabilidad y capacidad de integración con otros módulos de la arquitectura.

## Decision Drivers

* RF-06 Módulo de Reparto y Rutas 
* RF-06.1 Gestión de flotas de transporte

## Considered Options

* 0013-1-Usar-Una-Clase-Para-El-Módulo-De-Reparto-Y-Rutas
* 0013-2-Usar-Dos-Clases-Para-El-Módulo-De-Reparto-Y-Rutas

## Decision Outcome

Chosen option: "0013-2-Usar-Dos-Clases-Para-El-Módulo-De-Reparto-Y-Rutas", because permite un mejor desacoplamiento de responsabilidades y facilita el mantenimiento y la escalabilidad.

### Positive Consequences

* La separación en dos clases (Reparto y Rutas) mejora la organización del código, permitiendo asignar responsabilidades claras a cada clase.
* Al permitir que cada clase tenga sus respectivas funcionalidades se facilitan futuras ampliaciones y se mejora la escalabilidad.

### Negative Consequences

* El sistema se vuelve más complejo ya que se necesita establecer comunicación entre la clase Reparto y la clase Rutas.
* Se puede ver afectado el rendimiento de forma negativa, especialmente en escenarios de comunicación intensa entre módulos.

## Pros and Cons of the Options

### 0013-1-Usar-Una-Clase-Para-El-Módulo-De-Reparto-Y-Rutas

Debido a que las funciones están relacionadas el Módulo de Repartos y Rutas podría englobar todas las funcionalidades.
Además, para implementar la gestión de flotas de transporte, sería necesario organizar esta funcionalidad en forma de un método específico en esta clase.

* Good, because facilita la integración inicial con otros módulos.
* Good, because reduce la complejidad de comunicación entre clases.
* Good, because permite que la implementación sea más simple y un menor número de clases.
* Bad, because limita la escalabilidad.
* Bad, because su mantenimiento podría volvers complicado.

### 0013-2-Usar-Dos-Clases-Para-El-Módulo-De-Reparto-Y-Rutas

Debido a la cantidad de funciones que desempeña sería óptimo desacoplar su funcionalidad en dos clases.
Además, para implementar la gestión de flotas de transporte, se podría estructurar esta funcionalidad como un método específico.

* Good, because permite asignar responsabilidades específicas a cada clase.
* Good, because permite que cada clase maneje aspectos específicos del Módulo de Reparto y Rutas, posibilitando modificar o añadir nuevas funciones a cualquiera de esas clases sin afectar el funcionamiento de la otra.
* Good, because aumenta la escalabilidad.
* Bad, because la implementación de ambas clases por separado crea la necesidad de establecer una comunicación entre ellas y esto complica el sistema.
* Bad, because hay que asegurarse de que ambas clases tengan acceso a datos comunes sin duplicación o desincronización, esto añade complejidad al sistema.

## Links

* https://www.developers.dev/tech-talk/es/technology/decoupling-s-importance-in-software-development.html